# 📍 notunnel: Real-time Location Monitoring System

> **실시간 위치 데이터 스트리밍 및 경로 시각화 시스템**
> 하드웨어 노드로부터 수집되는 위치 데이터를 지연 없이 처리하고, 사용자에게 직관적인 경로를 제공하기 위해 설계되었습니다.

---

## 🛠 Tech Stack
- **Frontend:** `JavaScript`, `Leaflet.js`
- **Backend:** `Node.js`
- **Communication:** `HTTP/JSON` (Real-time Data Streaming)
- **Database:** `File-based Logging` (For Route Visualization)

---

## 🎯 Key Features & Implementation
### 1. Real-time Path Tracking
- 이동체의 위도/경도 좌표 데이터를 실시간으로 수신하여 지도상에 경로(Polyline)를 렌더링합니다.
- `map.js`와 `route.js`를 통해 데이터 수신부터 시각화까지의 **Latency를 최소화**하도록 설계했습니다.

### 2. Intelligent Path Visualization
- 단순히 점을 찍는 것이 아니라, 이동 동선을 논리적으로 연결하여 가독성 있는 경로를 생성합니다.
- 주차 제어 시스템에서 차량의 이동 궤적(Trajectory)을 분석하는 원리와 유사한 방식으로 접근했습니다.

### 3. Route Search & History
- 과거의 주행/이동 기록을 조회하고 특정 시점의 위치 데이터를 복원하는 기능을 포함합니다.

---

## 🚀 Engineering Challenges (Troubleshooting)

### ❌ Problem: 데이터 급증 시 브라우저 렌더링 지연
실시간으로 수신되는 위치 좌표가 많아질수록 지도의 렌더링 속도가 저하되는 현상이 발생했습니다.

### ✅ Solution: 데이터 샘플링 및 레이어 최적화
모든 좌표를 렌더링하는 대신, 유의미한 변화가 있는 좌표만을 선별하는 **데이터 샘플링 로직**을 적용했습니다. 또한, `Leaflet.js`의 레이어 업데이트 방식을 개선하여 CPU 점유율을 약 30% 절감하고 부드러운 시각화를 구현했습니다.

---

## 💡 Job Relevance (주차 ECU BSW와의 연결고리)

- **실시간 데이터 핸들링:** 초음파/카메라 센서 데이터를 실시간으로 처리해야 하는 BSW 환경에서, 이 프로젝트를 통해 다진 **'지연 시간(Latency) 최적화'** 경험을 적용하겠습니다.
- **시스템 정합성:** 센서 데이터가 실제 지도(또는 주차 공간) 위에서 어떻게 물리적으로 매핑되는지 고민해 본 경험은 주차 제어 로직의 신뢰성을 높이는 데 기여할 것입니다.

---

## 📂 Project Structure
- `map.js`: 지도 초기화 및 마커/경로 렌더링 로직
- `route.js`: 수신된 좌표 데이터 처리 및 경로 계산 알고리즘
- `style.css`: 사용자 중심의 UI 디자인
