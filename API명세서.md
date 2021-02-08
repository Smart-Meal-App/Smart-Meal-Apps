# API 명세서

기본 라우팅 경로 : api/v1/

## 목차
1. [계정관리](#계정-관리)
2. [메인페이지](#메인페이지)


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
    "login_way" : 0,
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

### 메인페이지

#### GET /popular_search
인기 검색어 리스트를 불러옵니다.

- Response
```json
{
    "popular_search" : [
        "민초카츠",
        "민초붕어빵",
        "민초덮밥",
        "민초김치말이국밥"
    ]
}
```


#### POST /search
- Request
    - 외식의 경우
        ```json
        {
            "isEatOut" : true,
            "keyword" : "민트초코",
            "price" : [
                1000,
                30000
            ],
            "kindOf" : 1,

        }
        ```
    - 집밥의 경우
        ```json
        {
            "isEatOut" : false,
            "keyword" : "민초김치말이덮밥",
            "price" : [
                1000,
                300000
            ],
            "menuCount" : 1,
            "kindOf" : 5

        }
        ```

- Response
```json
{
    "menu" : [
        {
            "name" : "민초카츠",
            "price" : 20000,
            "allergy" : [
                "민트초코",
                "튀김가루"
            ],
            "image_url" : "menu/stir-fried-Rice-Cake"
        },
        {
            "name" : "민초카츠",
            "price" : 20000,
            "allergy" : [
                "민트초코",
                "튀김가루"
            ],
            "image_url" : "menu/stir-fried-Rice-Cake"
        },
    ]
}
```

#### GET /meal/popular
인기 식사를 10개 가져옵니다.

- Response
```json
{
    "meal" : [
        {
            "image_url" : "/meal/blue_berry",
            "name" : "블루베리",
            "price" : 20000
        },
        {
            "image_url" : "/meal/blue_berry",
            "name" : "블루베리",
            "price" : 20000
        },
    ]
}
```

#### GET /meal/recommendation
추천 식사를 10개 가져옵니다.

- Response
```json
{
    "meal" : [
        {
            "image_url" : "/meal/blue_berry",
            "name" : "블루베리",
            "price" : 20000
        },
        {
            "image_url" : "/meal/blue_berry",
            "name" : "블루베리",
            "price" : 20000
        },
    ]
}
```

#### GET /announcement
공지들을 가져옵니다.
```json
{
    "count" : 2,
    "announcement" : [
        {
            "image_url" : "announcement/1",
            "announcement_number" : 1
        },
        {
            "image_url" : "announcement/2",
            "announcement_number" : 2
        }
    ]
}
```
