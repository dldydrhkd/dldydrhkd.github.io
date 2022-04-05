---
title: "unable to find index for $geoNear query"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-04-01 03:26:00
categories: [Error]
tags: [mongodb, near, spring data mongodb]
math: true
mermaid: true
---

## Error

- mongoDB 데이터
    
    ```json
    {
    	"_id" : ObjectId("6245f6edf2aa51bc5bae594c"),
    	"name" : "제주커피박물관 Baum",
    	"location" : {
    		"type" : "Point",
    		"coordinates" : [
    			126.8990639,
    			33.4397954
    		]
    	}
    }
    {
    	"_id" : ObjectId("6245f6eef2aa51bc5bae594d"),
    	"name" : "신산리 마을카페",
    	"location" : {
    		"type" : "Point",
    		"coordinates" : [
    			126.8759347,
    			33.3765812
    		]
    	}
    }
    ```
    
    > coordinates는 경도, 위도 순이다.
    > 
- VO
    - VisitJejuLocation
        
        ```java
        package kr.pe.playdata.domain;
        
        import lombok.Data;
        import org.springframework.data.annotation.Id;
        import org.springframework.data.mongodb.core.mapping.Document;
        
        @Data
        @Document(collection="places")
        public class VisitJejuLocation {
        
            @Id
            private String id;
            private String name;
            private Location location;
        }
        ```
        
    - Location
        
        ```java
        package kr.pe.playdata.domain;
        
        import lombok.Data;
        import org.springframework.data.geo.Point;
        import org.springframework.data.mongodb.core.mapping.Document;
        
        import java.util.List;
        
        @Data
        @Document
        public class Location {
        
            private String type;
            private List<String> coordinates;
        }
        ```
        
- 컨트롤러
    
    ```java
    package kr.pe.playdata.controller;
    
    import kr.pe.playdata.domain.VisitJejuLocation;
    import kr.pe.playdata.service.LocationService;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.data.geo.Distance;
    import org.springframework.data.geo.Metrics;
    import org.springframework.data.geo.Point;
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RequestParam;
    import org.springframework.web.bind.annotation.RestController;
    
    import java.util.List;
    
    @RestController
    @RequestMapping("/map")
    public class MapController {
        @Autowired
        private LocationService locationService;
    
        @GetMapping("/findNear")
        public List<VisitJejuLocation> findNear(
                @RequestParam String longtitude,
                @RequestParam String latitude,
                @RequestParam double distance
        ){
            Point p = new Point(Double.valueOf(longtitude), Double.valueOf(latitude));
            Distance d = new Distance(distance, Metrics.KILOMETERS);
            List<VisitJejuLocation> li = locationService.findNear(p,d);
            return li;
        }
    }
    ```
    
- Service
    - Interface
        
        ```java
        package kr.pe.playdata.service;
        
        import kr.pe.playdata.domain.VisitJejuLocation;
        import org.springframework.data.geo.Distance;
        import org.springframework.data.geo.Point;
        
        import java.util.List;
        
        public interface LocationService {
            public List<VisitJejuLocation> findNear(Point p, Distance d);
        }
        ```
        
    - Implements
        
        ```java
        package kr.pe.playdata.service.impl;
        
        import kr.pe.playdata.domain.VisitJejuLocation;
        import kr.pe.playdata.repository.LocationMongoRepo;
        import kr.pe.playdata.service.LocationService;
        import org.springframework.beans.factory.annotation.Autowired;
        import org.springframework.data.geo.Distance;
        import org.springframework.data.geo.Point;
        import org.springframework.stereotype.Service;
        
        import java.util.List;
        
        @Service
        public class LocationServiceImpl implements LocationService {
        
            @Autowired
            private LocationMongoRepo locationMongoRepo;
        
            public List<VisitJejuLocation> findNear(Point p, Distance d){
                return locationMongoRepo.findByLocationNear(p, d);
            }
        }
        ```
        
- Repository
    
    ```java
    package kr.pe.playdata.repository;
    
    import kr.pe.playdata.domain.VisitJejuLocation;
    import org.springframework.data.geo.Distance;
    import org.springframework.data.geo.Point;
    import org.springframework.data.mongodb.repository.MongoRepository;
    import org.springframework.data.mongodb.repository.Query;
    import org.springframework.stereotype.Repository;
    
    import java.util.List;
    
    @Repository
    public interface LocationMongoRepo extends MongoRepository<VisitJejuLocation, String> {
        List<VisitJejuLocation> findByLocationNear(Point p, Distance d);
    }
    ```
    
- 위와 같이 코드를 작성 후 postman으로 다음과 같이 보냈다.
    
    ```java
    localhost:8080/map/findNear?latitude=33.43&longtitude=126.89&distance=7
    ```
    
- 결과는 다음과 같이 에러가 발생하였다.
    
    ```java
    planner returned error :: caused by :: unable to find index for $geoNear query' on server xx.xxx.xxx.xxx:27017; nested exception is com.mongodb.MongoQueryException: Query failed with error code 291 and error message 'error processing query: ns=jeju.placesTree: GEONEAR  field=location maxdist=0.0010975 isNearSphere=1
    ```
    

## Error 해결

- mongoDB에 특정 field에 `2dsphere` index를 생성해줘야 한다.
    
    ```sql
    db.places.createIndex( { location: "2dsphere" } )
    ```
    
    <img width="368" alt="스크린샷_2022-04-01_오전_4 22 10" src="https://user-images.githubusercontent.com/48857296/161668475-79846c79-ace9-4c3b-9819-40e9013d6396.png">
    
    <img width="706" alt="스크린샷_2022-04-01_오전_4 22 36" src="https://user-images.githubusercontent.com/48857296/161668498-8be3c24c-0cef-4b34-b96f-43f8d683e54c.png">
    

## 참고 사이트

[Spring Data MongoDB - Aggregation Operation - 02](https://yearnlune.github.io/java/java-mongodb-aggregation-operation-02/#lookupoperation)

[$geoNear (aggregation)](https://www.mongodb.com/docs/manual/reference/operator/aggregation/geoNear/)

[예제로 배워보는 상황 별 MongoDB 위치 기반 쿼리](https://blog.ull.im/engineering/2019/03/06/mongodb-geospatial-queries.html)

[[MongoDB] MongoDB와 GeoJSON을 이용하여 근접 위치 확인하기](https://annajinee.tistory.com/32)
