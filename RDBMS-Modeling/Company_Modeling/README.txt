인프런 RDBMS Modeling

1 : M 재귀적 관계
회사와 부서. 부서의 하위 부서들이 있을 경우의 상황을 가정하여 설계.

COMPANY_TB
PK : ID

DEPARTMENT_TB
PK : DEPT_ID
FK : UPPER_DEPT_ID (상위 부서 ID)
FK : COMPANY_TB_ID