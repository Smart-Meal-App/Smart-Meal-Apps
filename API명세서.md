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

#### GET /fast_search/{keyword}
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
#### GET /load/food/{id}
메뉴를 불러옵니다.
id는 메뉴 고유의 id입니다.

- Response
```json
{
    "name" : "양파",
    "efficacy" : "껍질 제거시 눈이 아파옴",
    "price" : 20000,
    "image_url" : "/material/onion",
    "nutrients" : [
        123,
        23,
        55,
        65,
        43,
        24
    ],
    "special-note" : "주저리주저리",
    "recipe" : [
        3,
        2,
        1,
        54,
        89,
        34
    ],
    "recommended_recipe_url" : "대충 링크"
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

### 내 냉장고
/refrigerator/{token}/

token은 계정 고유의 값
#### GET /material/search/{keyword}
내 냉장고에 있는 재료를 검색한다.

- Response
```json
{
    "material" : [
        {
            "_id" : 0,
            "type" : 1,
            "image_url" : "/meterial/onion",
            "name" : "양파",
            "count" : 2,
            "registration" : "2020-12-14",
            "expiration_date" : "2022-11-11"
        },
        {
            "_id" : 1,
            "type" : 1,
            "image_url" : "/meterial/onion",
            "name" : "양파",
            "count" : 2,
            "registration" : "2020-12-14",
            "expiration_date" : "2022-11-11"
        },
        {
            "_id" : 2,
            "type" : 1,
            "image_url" : "/meterial/onion",
            "name" : "양파",
            "count" : 2,
            "registration" : "2020-12-14",
            "expiration_date" : "2022-11-11"
        },
    ]
}
```

#### GET /load/{page}
내 냉장고 불러오기
- Response
```json
{
    "page" : 0,
    "material" : [
        {
            "_id" : 0,
            "type" : 1,
            "image_url" : "/meterial/onion",
            "name" : "양파",
            "count" : 2,
            "registration" : "2020-12-14",
            "expiration_date" : "2022-11-11"
        },
        {
            "_id" : 1,
            "type" : 1,
            "image_url" : "/meterial/onion",
            "name" : "양파",
            "count" : 2,
            "registration" : "2020-12-14",
            "expiration_date" : "2022-11-11"
        },
        {
            "_id" : 2,
            "type" : 1,
            "image_url" : "/meterial/onion",
            "name" : "양파",
            "count" : 2,
            "registration" : "2020-12-14",
            "expiration_date" : "2022-11-11"
        },
        ...
        {
            "_id" : 30,
            "type" : 1,
            "image_url" : "/meterial/onion",
            "name" : "양파",
            "count" : 2,
            "registration" : "2020-12-14",
            "expiration_date" : "2022-11-11"
        }
    ]
}
```

#### DELETE /material/delete/{_id}
식재료 제거
- Response
```header
204 Not Content
```

```header
404 Not Found
```

#### POST /material/input
식재료 추가
- Request
```json
{
    "name" : "양파",
    "count" : 65535,
    "expiration_date" : "2022-11-11",
}
```

#### GET /material/load/{_id}
식재료의 상세정보를 본다.

_id는 식재료 고유의 아이디이다.

- Response
```json
{
    "name" : "양파",
    "efficacy" : "껍질 제거시 눈이 아파옴",
    "price" : 20000,
    "image_url" : "/material/onion",
    "nutrients" : [
        123,
        23,
        55,
        65,
        43,
        24
    ],
    "special-note" : "주저리주저리",
    "recipe" : [
        3,
        2,
        1,
        54,
        89,
        34
    ],
    "recommended_recipe_url" : "대충 링크"
}
```

nutrients는 mg기준입니다.
recipe는 각 레시피의 고유 번호입니다.\