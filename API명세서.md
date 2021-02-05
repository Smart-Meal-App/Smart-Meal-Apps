# API 명세서

기본 라우팅 경로 : api/v1/

## 목차
1. [계정관리](#계정-관리)

### 계정 관리
/account
#### POST /login
- Request
```json
{
    "token" : "아무튼 유저 고유의 토큰",
}
```
- `token`은 만약 게스트일시 `None`값으로 보내주면 됨


- Response
    - Login시에 계정이 없을경우
        404 Not found   
        ```json
        {
            "is_account" : false,
        }
        ```
    - Login시에 계정이 존재하는 경우
        200 Succes
        ```json
        {
            "is_account" : true,
        }
        ```



#### POST /register
- Request
```json
{
    "token" : "대충 토큰, 어떻게 생겼을려나",
    "id" : "qudwls185@naver.com",
    "login_way" : "naver",
    "preferred_diet" : [
        0,
        1,
        2,
        3,
        4,
        5
    ],
    "allergy" : {
        "meat" : true,
        "fish" : true,
        "dairy_product" : true,
        "vegetable" : true,
    },
    "nickname" : "똑식이",
}
- `token`는 해당 계정의 고유 id값

- Response
```header
204 Not content
```

#### POST /logout
- Request
```json
{
    "token" : "something token",
}
```

- Response
    - 204 Not Conetent
    
    - 404 Not found


#### PATCH /modify_profile
- Request
    - ex 1
    ```json
    {
        "token" : "대충 토큰",
        "name" : "민초카츠"
    }
    ```
    - ex 2
    ```json
    {
        "token" : "대충 토큰",
        "preferred_diet" : [
            1, 2, 3, 5
        ]
    }
    ```

- Response
    - 204 not content
    - 404 not found
