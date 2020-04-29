인프런 RDBMS Modeling

-- 도서관 도서대출관리 모델링
* 도서관에는 각 서고/서가에 많은 책들이 있다.
* 고객들은 인터넷을 통해 로그인한 후 도서 목록을 조회할 수 있다.
* 고객들은 원하는 책을 대출 받을 수 있다.
* 고객은 책이 있을 경우 대출 예약을 할 수 있으며, 대출을 위해서는 직접 방문해서 책을 찾아 대출해야 한다.

-- TABLE

STACK_ROOM_TB (서고)
ID - PK

BOOK_STAND_TB (서가)
ID - PK
STACK_ROOM_ID - FK

BOOK_TB (책)
BOOK_ID - PK
BOOK_STAND_ID - FK
STACK_ROOM_ID - FK

BOOK_CONTENT_TB (책 목차)
BOOK_CONTENT_ID - PK
BOOK_TB_BOOK_ID - FK
BOOK_TB_BOOK_STAND_ID - FK
BOOK_TB_STACK_ROOM_ID - FK

LOAN_TB (대출)
LOAN_ID - PK
BOOK_TB_BOOK_SEQ - FK
LOAN_YMD - PK
CUSTOMER_TB_CUSTOMER_ID - FK

CUSTOMER_TB (고객)
CUSTOMER_ID - PK
CUSTOMER_NM

LIBRARY_CATALOG_TB (도서 목록)
ID - PK
BOOK_NM
AUTHOR
PRESS

-- 의견
ERD 설계 진행중
변경의 여지가 있음.