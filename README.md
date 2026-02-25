# 🌤️ Unreal Dynamic Sky & Weather System

<img src="Udemy_DynamicSky.jpg" width="450" height="800" style="aspect-ratio: 9/16; object-fit: cover;" alt="Verification">

> **"시간과 날씨에 따라 변화하는 실시간 환경 시스템 구현"**  
>
> Udemy 강의 **'Unreal Engine 5 : 강의 하나로 Dynamic Sky 시스템 완벽 마스터하기!
'**를 기반으로 Unreal Engine Dynamic Sky 및 Lumen 시스템을 학습하며 낮/밤 전환 및 비·눈 환경 효과를 구현한 프로젝트입니다.

---

## 📋 1. 프로젝트 개요 (Overview)

* **프로젝트명:** Udemy Unreal Niagara DynamicSky Study
* **유형:** Unreal Engine 기반 실시간 DynamicSky 시스템 학습 프로젝트  
* **개발 인원:** 1인 개발  
* **공부 목적:** DynamicSky 및 Lumen 시스템의 구조 및 동작 원리 학습
* **공부 기간:** 2024.10.04.-2024.11.01.
* **주요 특징:**  
    * Sky Actor와 Weather System의 구조 이해 및 실시간 환경 변화 구현   
    * 눈/비 등 다양한 날씨 구현 및 Material과 상호작용 구현
    * Unreal Sky Actor들의 각 속성값 변화에 따른 차이 이해
    * 강의 복습을 위한 개인 작품 제작
---
## 🎥 2. 실습 영상 (Practice Video)

> *아래 링크를 클릭하면 유튜브에서 고화질로 시청할 수 있습니다. (YouTube)*

### Udemy 실습 영상

[YouTube : Udemy 실습 영상](https://youtu.be/zWjapsRteJ0?si=IN5r83rrmVk6RqjI)



https://github.com/user-attachments/assets/e423210e-f649-4dd4-967a-001bdfa14459

---

## 🛠️ 3. 사용 기술 (Tech Stack)

### Engine & Language
*   **Unreal Engine 5.6**: Core Engine (최신 기능 활용)
*   **Blueprints**: Dynamic Sky용 Actor 설정 및 날씨에 따른 변화 구현
*   **Camera Sequencer**: 몰입감 있는 시네마틱 카메라 연출

### Core Concepts
* 🌞 낮 / 🌙 밤 전환 시스템  
* 🌧️ 비(Rain) + 바닥 물 튀는 효과(Splash)  
* ❄️ 눈(Snow) + 눈 위 발자국 시스템  
* 🌫️ 날씨에 따른 시야 감소(Fog 제어)  
* 🎨 Sky Material 커스터마이징  
* ✨ Niagara 기반 날씨 VFX 구현  

---

## 💡 4. 주요 학습 내용 (Features)

- [다이나믹스카이 학습 노트 보기](https://github.com/KINGWONWOO/obsidian/blob/44cfd75bafca5f5c7cf6059c8cfce293bb441a6d/%EC%96%B8%EB%A6%AC%EC%96%BC%20%EA%B3%B5%EB%B6%80/Unreal/%EC%9D%BC%EC%9D%BC%20%EA%B3%B5%EB%B6%80/3-UE5%20DynamicSky(24.10.04.~24.11.01)/merged%20copy.md)

---

## ⚙️ 5. 주요 구현 내용

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

## 🚀 6. 트러블 슈팅 (Troubleshooting)

### 이슈 1: 눈 위 발자국이 부자연스럽게 끊기며 사라지는 현상
- **문제**: Decal 기반으로 생성된 발자국이 설정된 수명이 다했을 때 갑자기 사라져 이질감이 발생하는 문제.
- **해결**: Material 내부에 `Time`과 `Opacity`를 연동한 Fade-out 로직을 추가했습니다. `Scalar Parameter`를 사용하여 생성 후 일정 시간이 지나면 점진적으로 투명도가 낮아지도록 설계하여 자연스럽게 지면에 흡수되는 연출을 구현했습니다.

### 이슈 2: 환경에 따른 눈 쌓임(Snow Accumulation) 머터리얼 구분
- **문제**: 모든 오브젝트에 동일한 눈 머터리얼이 적용되어, 경사면이나 실내 영역에도 눈이 어색하게 쌓이는 현상.
- **해결**: **World Aligned Blend** 노드를 활용하여 월드 좌표의 상단(Z축) 방향으로만 눈 텍스처가 입혀지도록 제한했습니다. 이를 통해 바닥과 물체의 윗면에는 눈이 쌓이고, 벽면이나 천장 아래는 원래의 머터리얼이 유지되도록 시각적 정확도를 높였습니다.

### 이슈 3: 날씨 전환 시 잔류하는 눈 머터리얼 처리
- **문제**: 눈에서 비나 맑은 날씨로 상태가 변경되었음에도 바닥에 쌓인 눈이 즉시 사라지지 않고 남아있는 문제.
- **해결**: 날씨 제어 블루프린트에서 **Material Parameter Collection (MPC)**을 활용했습니다. 날씨가 바뀔 때 'SnowAmount' 파라미터 값을 실시간으로 감소시켜, 지면의 눈 머터리얼이 서서히 녹아 사라지는(Melting) 상태 변화를 시스템적으로 연동했습니다.

## 📚 7. 공부 확장 방향(Future Study Plan)

- Volumetric Cloud 심화 커스터마이징  
- GPU Niagara 최적화 연구  
- 계절 변화 시스템 확장  
- Sky & Weather를 Gameplay 시스템과 연동  
- 오픈월드 환경에서의 퍼포먼스 최적화 연구  

---

**Contact:** (강원우 / king_wonwoo@naver.com)  
