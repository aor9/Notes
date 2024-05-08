user 관련

공통 에러
422 - 필요한 데이터 없거나 형식 다를 떄 (예: int -> str)
{
  "detail": [
    {
      "type": "int_parsing",
      "loc": [
        "body",
        "user",
        "id"
      ],
      "msg": "Input should be a valid integer, unable to parse string as an integer",
      "input": "ㅁㄹ",
      "url": "https://errors.pydantic.dev/2.6/v/int_parsing"
    }
]

------------------------------------------
/api/user/login GET
# 로그인, 유저 이름가지고
# 요청
var url = new URL('http://psj2867.com/api/user/login');
var params = { user: 'userName' };
url.search = new URLSearchParams(params).toString();
fetch(url, {method : "GET"})

# 결과
200
{
  "name": "qwer",
  "id": 1,
  "contents": []
}
403
# 없으면
{
  "detail": "user not found"
}
------------------------------------------
/api/user/me GET
# 로그인 한 상태에서 유저 정보 새로 불러올 떄
# 요청
var url = new URL('http://psj2867.com/api/user/me');
var params = { user: 'userName' };
url.search = new URLSearchParams(params).toString();
fetch(url, {method : "GET"})

# 결과
200
{
  "name": "qwer",
  "id": 1,
  "contents": [
    {
      "name": "c1",
      "user_id": 1,
      "url": "http://c1-u1",
      "id": 1,
      "chapters": [
        {
          "url": "string",
          "content_id": 1,
          "id": 1,
          "name": "string"
        },
        {
          "url": "ㄹㅇ2",
          "content_id": 1,
          "id": 2,
          "name": "ㄴ2"
        }
      ]
    },
    {
      "name": "c1",
      "user_id": 1,
      "url": "http://c1-u1",
      "id": 2,
      "chapters": []
    }
  ]
}
403
# 없으면
{
  "detail": "user not found"
}


------------------------------------------
/api/user/signup POST
# 회원가입 유저 이름만 필요
# 요청
url = "http://psj2867.com/api/user/signup"
data = {
  "name": "qwer"
}
fetch(url, {method : "POST", body: JSON.stringfy(data), headers:{"Content-Type": "application/json"}})

#결과
200
{
  "name": "qwer",
  "id": 1
}


------------------------------------------
/api/user/content POST
#작품 추가, 유저 아이디, 작품 정보
#요청
data = {
  "user": {
    "id": 0
  },
  "content": {
    "name": "c1",
    "url": "http://c1-u1"
  }
}
fetch(url, {method : "POST", body: JSON.stringfy(data), headers:{"Content-Type": "application/json"}})

#결과
200 - 추가된 작품이 포함된 목록
[
  {
    "name": "c1",
    "user_id": 1,
    "url": "http://c1-u1",
    "id": 1,    
    "chapters": []
  },
  {
    "name": "c1",
    "url": "http://c1-u1",
    "user_id": 1,
    "id": 2,    
    "chapters": []
  }
]
403
{
  "detail": "user not found"
}

------------------------------------------
/api/user/content DELETE
#회차 추가, 유저 아이디, 작품 정보
#요청
data = {
  "user": {
    "id": 0
  },
  "content": {
    "id": 0
  }
}
fetch(url, {method : "DELETE", body: JSON.stringfy(data), headers:{"Content-Type": "application/json"}})

#결과
200 - 삭제된 작품 제거된 작품 목록
[
  {
    "name": "c1",
    "user_id": 1,
    "url": "http://c1-u1",
    "id": 1,    
    "chapters": []
  },
  {
    "name": "c1",
    "url": "http://c1-u1",
    "user_id": 1,
    "id": 2,    
    "chapters": []
  }
]

------------------------------------------
/api/user/cahpter POST
#회차 추가, 유저 아이디, 작품 정보
#요청
data = {
  "user": {
    "id": 0
  },
  "content": {
    "id": 0
  },
  "chapter": {
    "name": "string",
    "url": "string"
  }
}
fetch(url, {method : "POST", body: JSON.stringfy(data), headers:{"Content-Type": "application/json"}})

#결과
200 - 추가된 회차가 포함된 회차 목록
[
  {
    "url": "string",
    "content_id": 1,
    "id": 1,
    "name": "string"
  },
  {
    "name": "ㄴ2",
    "url": "ㄹㅇ2",
    "content_id": 1,
    "id": 2
  }
]


------------------------------------------
/api/user/cahpter DELETE
#회차 추가, 유저 아이디, 작품 정보
#요청
data = {
  "user": {
    "id": 0
  },
  "content": {
    "id": 0
  },
  "chapter": {
    "id" : 0
  }
}
fetch(url, {method : "DELETE", body: JSON.stringfy(data), headers:{"Content-Type": "application/json"}})

#결과
200 - 삭제된 회차 제거된 회차 목록
[
  {
    "url": "string",
    "content_id": 1,
    "id": 1,
    "name": "string"
  },
  {
    "name": "ㄴ2",
    "url": "ㄹㅇ2",
    "content_id": 1,
    "id": 2
  }
]