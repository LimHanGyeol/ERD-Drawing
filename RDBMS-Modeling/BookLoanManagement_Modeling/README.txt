인프런 RDBMS Modeling

-- 도서관 도서대출관리 모델링
* 도서관에는 각 서고/서가에 많은 책들이 있다.
* 고객들은 인터넷을 통해 로그인한 후 도서 목록을 조회할 수 있다.
* 고객들은 원하는 책을 대출 받을 수 있다.
* 고객은 책이 있을 경우 대출 예약을 할 수 있으며, 대출을 위해서는 직접 방문해서 책을 찾아 대출해야 한다.

-- TABLE

* STACK_ROOM_TB (서고)
STACK_ROOM_ID - PK

* BOOK_STAND_TB (서가)
BOOK_STAND_ID - PK
STACK_ROOM_ID - FK

* BS_FLOOR_TB (서가 층)
BS_FLOOR_ID - PK
BOOK_STAND_ID - FK
STACK_ROOM_ID - FK

* FLOOR_ROW_TB (층열)
FLOOR_ROW_ID - PK
BS_FLOOR_ID - FK
BOOK_STAND_ID - FK
STACK_ROOM_ID - FK

* BOOK_TB (책)
BOOK_ID - PK
FLOOR_ROW_ID - FK
BS_FLOOR_ID - FK
BOOK_STAND_ID - FK
STACK_ROOM_ID - FK

* BOOK_DEFAULT_LIST (책 목록)
BDL_ID - PK
GENRE_ID - FK
BOOK_ID - FK
MAGAZINE_ID - FK
BGI_ID - FK
THESIS_ID - FK

* BOOK_GENRE (책 장르)
GENRE_ID - PK

* MAGAZINE_INFO (잡지 정보)
* BOOK_GENERAL_INFO (일반 책 정보)
* THESIS_FINFO (논문 정보)

* LOAN_TB (대출)
LOAN_ID - PK
BOOK_ID - FK
LOAN_YMD - PK
MEMBER_ID - FK

* MEMBER_TB (회원)
CUSTOMER_ID - PK
GENDER_ID - FK

* GENDER_TB (성별 기준)

-- 의견
강의와 사용 툴이 달라 1 : 1 관계 매핑이 강의와 맞지 않음.
변경의 여지가 있음.
