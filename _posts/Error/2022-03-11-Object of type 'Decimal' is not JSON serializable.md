---
title: "Object of type 'Decimal' is not JSON serializable"
author:
  name: 이용광
  link: https://github.com/dldydrhkd
date: 2022-03-11 23:53:00
categories: [Error]
tags: [json, python3]
math: true
mermaid: true
---

## Error

- 다음과 같이 flask에서 mysql db와 연동하여 값을 얻어와 json 형태로 바꿨을 때 error가 발생한다.
    
    ```python
    def empall(self): 
            all = []
            try:
                conn = getConnection()
                cursor = conn.cursor()
                try:
                    cursor.execute("select * from emp01")
                    rows = cursor.fetchall()
    
                    objects_list = []
                    for row in rows:
                        d = collections.OrderedDict()
                        d['empno'] = row[0]
                        d['ename'] = row[1]
                        d['sal'] = row[2]
                        objects_list.append(d)
                    all = json.dumps(objects_list)
                except Exception as e:
                    print(e)
            except Exception as e:
                print(e)
            finally:
                cursor.close()
                conn.close()
            return all
    ```
    
- Error
    
    ```bash
    Object of type 'Decimal' is not JSON serializable
    ```
    

## Error 해결

- oracle db는 소수를 json 형태로 잘 바꿔주지만 mysql은 잘 바꿔주지 못하는것 같다.
- 소수가 나올 수 있는 row[2] 부분을 int(row[2]) 혹은 float(row[2])로 바꾸어 해결하였다.
