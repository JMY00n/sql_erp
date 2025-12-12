# 고압 세척기(제조업) ERP 데이터베이스 설계 및 구현 프로젝트

### 2025학년도 2학기 데이터베이스 과제

**과목명:** 데이터베이스 <br>
**담당교수:** 김진숙 교수님 <br>
**학과:** 컴퓨터소프트웨어과 <br>
**학번:** 202530533 <br>
**이름:** 윤정민

---

## 1. 프로젝트 개요
본 프로젝트는 제조업 현장에서의 실제 근무 경험을 바탕으로, **전기식/연료식 세척기 생산 공정**의 자재 관리, 생산 관리, 재고 및 출고 관리를 효율적으로 처리하기 위한 ERP 시스템의 데이터베이스를 설계하고 구현한 결과물입니다.

### 주요 목표
* 제품 생산에 필요한 **BOM(Bill of Material)** 구조 설계
* 자재 입고부터 생산, 완제품 출고까지의 **물류 흐름 추적**
* **제3정규형(3NF)** 을 준수한 무결성 있는 데이터베이스 구축

---

## 2. 업무 프로세스 및 기능
본 데이터베이스는 다음과 같은 핵심 업무 프로세스를 지원합니다.

1.  **자재(Material) 관리**: 부품(펌프, 모터, 히터 등)의 기본 정보 및 재고 관리, 입고 내역 기록.
2.  **제품(Product) 관리**: 전기식/연료식 세척기 모델 관리 및 자재와의 BOM(소요량) 관계 정의.
3.  **생산(Production) 관리**: 생산 주문(Order) 접수 및 실제 생산 실적(Record) 등록, 자재 자동 차감.
4.  **재고 및 출고(Shipment) 관리**: 생산 완료된 완제품의 재고 현황 파악 및 고객 출고 처리.

## 3. 데이터베이스 설계 (Schema)
총 10개의 테이블로 구성되어 있으며, 모든 테이블은 **제3정규형(3NF)** 을 만족하도록 설계되었습니다.

| 테이블명 (Table) | 설명 | 주요 컬럼 |
| :--- | :--- | :--- |
| **ERP_PRODUCT** | 제품 기본 정보 | `PRODUCT_ID`, `PRODUCT_NAME` |
| **ERP_MATERIAL** | 자재 기본 정보 | `MATERIAL_ID`, `STOCK_QTY` |
| **ERP_BOM** | 제품별 자재 소요량 | `PRODUCT_ID`, `MATERIAL_ID`, `REQUIRED_QTY` |
| **ERP_INVENTORY** | 완제품 재고 현황 | `PRODUCT_ID`, `STOCK_QTY` |
| **ERP_PRODUCTION_ORDER** | 생산 주문(계획) | `ORDER_ID`, `ORDER_QTY` |
| **ERP_PRODUCTION_RECORD** | 생산 실적(완료) | `RECORD_ID`, `PRODUCED_QTY` |
| **ERP_MATERIAL_IN** | 자재 입고 이력 | `IN_ID`, `IN_QTY` |
| **ERP_MATERIAL_USAGE** | 생산 자재 사용 이력 | `USAGE_ID`, `USED_QTY` |
| **ERP_SHIPMENT** | 출고(배송) 정보 | `SHIPMENT_ID`, `SHIPMENT_DATE` |
| **ERP_SHIPMENT_RECORD** | 출고 상세 품목 | `SHIPMENT_RECORD_ID`, `QTY` |

---

## 4. 포함된 파일 설명
이 저장소는 데이터베이스 구축을 위한 통합 SQL 스크립트 파일을 포함하고 있습니다.

*  **`manufacturing_erp_script.sql`**
    * **DDL**: 테이블 생성 및 제약조건(PK, FK) 설정, 기존 테이블 초기화 구문 포함.
    * **DML (Sample Data)**: 전기식/연료식 세척기 생산 시나리오에 맞춘 더미 데이터 삽입.
    * **DML (Practice Q&A)**: 실무에서 발생할 수 있는 데이터 조작 및 조회 문제 **30제**와 정답 쿼리.
        * *기초 조회, 조인(JOIN), 집계(GROUP BY), 서브쿼리, 데이터 수정/삭제 등 포함*

---
