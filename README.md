# Public-Data-Utilization-Support-Center_Covid-19-Vaccination-Consignment-Medical-Institution-inquiry-
# 공공데이터활용지원센터_코로나19 예방접종 위탁의료기관 조회서비스 
<img width="775" alt="스크린샷 2021-07-23 오전 10 40 39" src="https://user-images.githubusercontent.com/69393030/126728388-e9d419d7-ef6d-43fc-83e1-134b145fa55c.png">
# Features
  - 검색하려는 지역을 입력하게되면 코로나19 예방접종 위탁의료기관을 조회해줍니다.
  - 한번에 많은양의 데이터를 한 화면에 표시할수 없으므로 페이징을 통해 해당유저화면에 제한적으로 데이터를 보여줍니다.
# API 목록 
<img width="775" alt="스크린샷 2021-07-23 오전 10 41 21" src="https://user-images.githubusercontent.com/69393030/126728424-2b6aaf5f-f072-450c-8eca-05cf560b54ef.png">

# parameter 
  -page : 현재 페이지 
  -perPage : 현재 페이지당 보여줄 data 의 갯수
  -location : 검색하려는 지역명 
# Response 
<img width="612" alt="스크린샷 2021-07-23 오전 10 44 30" src="https://user-images.githubusercontent.com/69393030/126728606-9b5043b6-851f-4371-b455-39592207916f.png">
 -dywk : 요일
 -lunchEndTm : 점심종료시간 
 -orgTlno : 기관 전화번호 
 -orgZipaddr : zip 주소 ( 도로명주소 ) 
 -orgnm : 기관 이름 (주소포함)
 -slrYmd : 업데이트 날짜 
 
 # Response Result (java-spring)
 <img width="990" alt="스크린샷 2021-07-23 오전 10 55 03" src="https://user-images.githubusercontent.com/69393030/126729156-25ed23d4-83b6-4a96-ac10-ed12cc005cfa.png">
 # Response Result (javascript -vue.js)
 <img width="726" alt="스크린샷 2021-07-23 오전 10 55 54" src="https://user-images.githubusercontent.com/69393030/126729200-1cdf6378-ed52-4c9f-b3b0-f8fec20b8261.png">

 # models 
 <img width="612" alt="스크린샷 2021-07-23 오전 10 46 27" src="https://user-images.githubusercontent.com/69393030/126728723-776c8a6c-e284-4211-bc43-e92db041c48d.png">
# Back-end (java - spring)
<img width="1084" alt="스크린샷 2021-07-23 오전 10 47 15" src="https://user-images.githubusercontent.com/69393030/126728769-b6f27085-1013-41f8-b716-8caf498cf6d7.png">

# front-end (javascript - vue.js)
<img width="873" alt="스크린샷 2021-07-23 오전 10 48 19" src="https://user-images.githubusercontent.com/69393030/126728813-d8103947-b61c-4cae-878d-739c71124b6d.png">
# Result page
<img width="873" alt="스크린샷 2021-07-23 오전 10 48 49" src="https://user-images.githubusercontent.com/69393030/126728833-367a170a-d08a-4174-922c-0970ba8f464e.png">

# Feature image
<img width="873" alt="스크린샷 2021-07-23 오전 10 49 19" src="https://user-images.githubusercontent.com/69393030/126728860-04c135d9-56b4-4c76-9eb5-e0c634054eb1.png">
 -paging 
 -search
 -message 
