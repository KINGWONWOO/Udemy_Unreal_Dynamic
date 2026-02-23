# 🌤️ Unreal Dynamic Sky & Weather System

> **"시간과 날씨에 따라 변화하는 실시간 환경 시스템 구현"**  
>
> Unreal Engine에서 Dynamic Sky Actor를 중심으로  
> 낮/밤 전환 및 비·눈 환경 효과를 구현한 프로젝트입니다.

---

## 📌 Project Overview

* **Engine:** Unreal Engine 5  
* **Development:** 1인 개발 (Blueprint 기반)  
* **Goal:** Sky Actor와 Weather System의 구조 이해 및 실시간 환경 변화 구현  

### 🎯 핵심 구현 기능

- 🌞 낮 / 🌙 밤 전환 시스템  
- 🌧️ 비(Rain) + 바닥 물 튀는 효과(Splash)  
- ❄️ 눈(Snow) + 눈 위 발자국 시스템  
- 🌫️ 날씨에 따른 시야 감소(Fog 제어)  
- 🎨 Sky Material 커스터마이징  
- ✨ Niagara 기반 날씨 VFX 구현  

---

## ⚙️ 주요 구현 내용

### 1️⃣ Day & Night Cycle

- Directional Light 회전 기반 시간 흐름 구현  
- Sky Atmosphere & Sky Light 연동  
- 시간에 따른 Sky Material Parameter 변경  


Time → Light Rotation → Sky Update → Environment Lighting Change


✔ 태양 고도 기반 색감 변화  
✔ 밤 환경 조도 자동 감소  

---

### 2️⃣ Rain System

- Niagara로 빗방울 생성  
- Collision 기반 Splash Effect 생성  
- 플레이어 중심 Spawn 방식으로 최적화  


Rain Collision → Event Trigger → Splash Spawn


✔ Secondary Emitter 활용  
✔ Additive Material 적용  

---

### 3️⃣ Snow System

- 느린 낙하 속도 + Drift 적용  
- Drag 기반 자연스러운 움직임 구현  
- 눈 위 발자국 시스템 구현 (Decal 기반)

✔ 위치 기반 Footprint 생성  
✔ 시간 경과에 따른 자연스러운 사라짐 처리  

---

### 4️⃣ Visibility Control

- Exponential Height Fog 밀도 조절  
- 날씨 상태에 따른 가시거리 감소  
- 환경 분위기 변화 구현  

---

## 📂 Project Structure


Udemy_Unreal_Dynamic/
├── Blueprints/
│ ├── BP_DynamicSky
│ ├── BP_WeatherController
├── Niagara/
│ ├── RainSystem
│ ├── SnowSystem
│ └── SplashEffect
├── Materials/
│ ├── M_Sky
│ ├── M_SnowGround
└── Maps/


---

## 📚 Study Notes (펼쳐보기)

<details>
<summary>📖 공부 정리 내용 보기</summary>

### 🔹 Sky System 이해

- Directional Light / Sky Light / Sky Atmosphere 관계 구조 이해  
- Recapture Sky 개념 학습  
- Material Parameter Collection 활용  

### 🔹 Niagara 학습 내용

- Spawn Rate vs Burst 차이  
- Collision Event 기반 Secondary Emitter 구조  
- GPU vs CPU Simulation 차이 이해  

### 🔹 Material 학습 내용

- Dynamic Material Instance 생성 및 실시간 값 변경  
- Gradient 기반 Sky 색상 계산 방식 이해  
- Additive / Translucent Blend Mode 차이  

### 🔹 Environment 연동

- Fog 밀도 조절을 통한 시야 연출  
- Weather State Enum 기반 시스템 설계  
- Actor 간 데이터 흐름 구조 이해  

</details>

---

## 🚀 Future Study Plan

- Volumetric Cloud 심화 커스터마이징  
- GPU Niagara 최적화 연구  
- 계절 변화 시스템 확장  
- Sky & Weather를 Gameplay 시스템과 연동  
- 오픈월드 환경에서의 퍼포먼스 최적화 연구  

---

**Contact:** (Your Name / Email)  
**GitHub:** https://github.com/KINGWONWOO/Udemy_Unreal_Dynamic  
