인프런 RDBMS Modeling

-- 중학교 학생 성적관리 프로젝트
* 과목은 학년별로 담당 선생님이 따로 있다.
* 시험은 중간고사, 기말고사 두 가지가 있다.
* 학생들은 학년, 반에 배정되며 반별로 학생들에게 고유 번호를 부여하고 있다.
* 각 반에는 담임 선생님이 배정되어 있다. 선생님 중에는 담임을 맡지 않는 선생님도 있다.
* 한 반의 학생은 대략 40명 정도이고 남녀 공학이다.
* 석차는 남녀 공통 1등부터 순서대로 정한다.

-- TABLE

* STUDENT_TB (학생)

ADMISSION_YEAR은 입학년도
STUDENT_ID - PK

GRADUATION_YEAR - 졸업년도
GRADUATION_YEAR가 NULL이면 재학생으로 판단한다.

CLASS_ID - FK
1 : N으로 CLASS_TB와 관계를 맺는다.
여기서 CLASS_ID가 NULL일 수 있다.
신입생이 들어왔을때 그들의 반배정이 되지 않았지만, 학교 전산망에는 등록을 해야하기 때문이다.
STUDENT_SQ는 학생들의 고유번호를 나타낸다. SQ는 반배정이 아직 되지 않은 학생을 고려해 NULL을 허용한다.

* SCHOOL_YEAR_TB (학년)
SCHOOL_YEAR_ID - PK

SCHOOL_YEAR_NM
1학년, 2학년, 3학년 데이터를 입력

CLASS_TB (반)
CLASS_ID - PK
SCHOOL_YEAR_ID - FK

CLASS_FL
FLAG 칼럼의 역할은 이전 졸업생 파악에 사용된다.
올해의 신입생들 해당 CLASS에 배치하지 않을 경우 0으로 지정할 수 있다.

TEACHER_ID - FK
CLASS_TB는 TEACHER_TB와 1: N 관계를 가질 수 있다.
반 테이블에서 선생님을 많이 가질 수 있는 이유는 반에서는 매 년도마다 선생님이 달라지는 경우가 있기 때문이다.

TEACHER_TB (선생님)
TEACHER_ID - PK

SUBJECT_TB (과목)
SUBJECT_ID - PK

LESSON_TB (수업)
LESSON_SQ - PK
TEACHER_ID - FK
SUBJECT_ID - FK
SCHOOL_YEAR_ID - FK

과목에는 1학년 수학, 2학년 수학 등의 데이터가 있을 것이다.
그리고 과목의 선생님이 있다.
OPEN_YMD 칼럼은 "1학년 수업에는 어느 선생님이 어느 날짜에 시작했다." 를 나타낸다.

GRADE_TB (성적)
LESSON_SQ - AK
STUDENT_ID - PK

-- 의견
모델링을 계속해서 공부, 설계를 진행한다.
미흡한 면과 수정될 여지가 있다.
