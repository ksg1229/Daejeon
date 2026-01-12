# Daejeon (대전) Project

## 📖 프로젝트 소개 (Introduction)
대전 지역의 건물 및 위치 정보를 시각화하고, 에너지 사용량 등을 분석하는 Spring Boot & Flask 하이브리드 애플리케이션입니다.
VWorld 오픈 API와 자체 구축된 건물/에너지 데이터를 활용하여 지도 위에 정보를 표시하고, 대시보드를 통해 인사이트를 제공합니다.

## 🛠 기술 스택 (Tech Stack)

### Backend
- **Java**: 17
- **Framework**: Spring Boot 3.5.7
- **Database**: Oracle Database
- **Persistence**: MyBatis
- **Template Engine**: Thymeleaf

### Data & AI / Analysis
- **Python**: 3.x
- **Framework**: Flask
- **Libraries**: Pandas, GeoPandas, Plotly, Dash
- **API**: VWorld Open API, ODS (Energy/Building Data)

### Frontend
- HTML5, CSS3, JavaScript
- Thymeleaf Layout Dialect

## 🔑 주요 기능 (Key Features)
1. **지도 시각화**: VWorld 맵을 기반으로 대전 지역 건물 마커 및 위치 정보 표시.
2. **에너지 대시보드 (E-PRO)**:
   - 건물별 전기/가스 사용량 및 탄소 배출량 추이 분석.
   - 노후도별 에너지 효율 비교.
   - Plotly/Dash를 활용한 동적 그래프 제공.
3. **건물 검색 및 비교**: 
   - 주소 검색을 통해 특정 건물의 에너지 소비 패턴 분석.
   - 반경 100m 인근 건물과의 평균 비교.
4. **공지사항**: 게시판 기능을 통한 정보 공유.

## ⚙️ 설정 및 실행 가이드 (Setup & Run)
**주의**: 보안상 모든 API 키와 비밀번호는 제거되어 있습니다. 프로젝트 실행을 위해서는 로컬 환경에 맞는 키 설정이 필요합니다.

### 1. Spring Boot 설정 (`src/main/resources/application.properties`)
해당 파일을 열어 아래 항목을 실제 값으로 변경하세요.
```properties
# DB 설정
spring.datasource.url=jdbc:oracle:thin:@YOUR_DB_IP:1521:xe
spring.datasource.username=daejeon
spring.datasource.password=YOUR_DB_PASSWORD 

# VWorld API 설정
daejeon.vworld.key=YOUR_VWORLD_API_KEY
```

### 2. Flask/Python 설정 (`flask/epro/`)
Python 의존성을 설치하고, `app.py` 및 `GRAPH_KAKAO.py` 내의 키 설정을 확인하세요.
- **VWorld Key**: 환경변수 `VWORLD_API_KEY` 설정 권장.
- **Kakao API Key**: `GRAPH_KAKAO.py` 내 `KAKAO_API_KEY` 변수 또는 환경변수 `KAKAO_API_KEY` 설정.
- **Oracle DB**: `GRAPH_KAKAO.py` 내 `DB_CONFIG` 딕셔너리의 비밀번호 수정.

### 3. 실행
- **Spring Boot**: `DaejeonApplication` 메인 클래스 실행.
- **Flask**: `flask/epro/app.py` 또는 `GRAPH_KAKAO.py` 실행 (포트 확인 필요).

## 📂 폴더 구조 (Structure)
- `src/main/java`: Spring Boot 자바 소스 코드
- `src/main/resources`: 설정 파일, 매퍼 XML, 정적 리소스(HTML/CSS)
- `flask/epro`: Python Flask 서버 및 데이터 분석 스크립트
