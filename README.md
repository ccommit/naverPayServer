# naverPayServer
네이버페이 백엔드 결제시스템

1. 로그인의 인증방식이 무엇인지 명시하기기
-> ID, Password를 통한 인증


결제시스템 개발시 유의사항 찾아오기
1) db 장애시 예외처리 방법
db작업 장애시 서비스 이용 불가 메시지를 띄움
읽기장애시 redis 같은 캐시를 사용하여 조회되는 데이터를 DB에 반환 
쓰기장애시 일정간격으로 쓰기 N회 시도

2) tosspayment 장애시 예외처리 방법
→ 일정간격으로 접속시도 N회 시도한 후 접속 불가 시 서비스 이용 불가 메시지를 띄움
3) naver pay 어플리케이 다운시 결제 처리중인데이터 재처리방법
→ 
4) 카드번호를 임의난수로로 초당 1000씩 해킹툴 대첩법
→ 특정 ip에서 초당 N건 발생시 결제못하게 막는다.







   

#관계형 데이터 베이스 정리
관계형 데이터베이스(Relational Database, RDB)는 데이터를 표(table) 형태로 저장하고 관리하는 데이터베이스의 한 유형 
각 표는 행(row)과 열(column)로 구성되며, 데이터를 효율적으로 저장하고 검색할 수 있도록 설계

테이블 구조 
행과 열로 구성되고 
행은 데이터나 개별 레코드를 나타냄 열은 속성 또는 필드를 나타낸다


스키마 기반 구조
각 테이블은 고정된 스키마를 가진다. 즉 데이터가 저장되기 전에 테이블의 구조(열의 이름, 데이터 타입 등)를 정의

키(key)의 사용
기본키(Primary Key): 각 행을 고유하게 식별하기 위한 열
외래(Foreign Key): 다른 테이블과 관계를 정의하기 위해 사용되는 열

관계정의 테이블 간의 관계를 정의하여 데이터를 연결하고 일관성을 유지할 수 있다

ACID(원자성, 일관성, 고립성, 지속성)특성
원자성(Atomicity): 트랜잭션은 전부 실행되거나 전혀 실행되지 않아야 한다
일관성(Consistency): 트랜잭션 실행 후 데이터는 항상 일관성 있는 상태여야 한다
고립성(Isolation): 동시에 실행되는 트랜잭션은 서로 간섭하지 않아야 한다.
지속성(Durability): 트랜잭션 완료 후 데이터는 영구적으로 저장.

