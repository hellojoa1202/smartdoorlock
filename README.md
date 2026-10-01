# SMARTDOORLOCK

2024 한이음 ICT 멘토링 프로젝트

고령층을 위한 얼굴인식 기반 스마트 도어락 및 스마트홈 IoT 시스템

## Project Overview

Raspberry Pi와 카메라를 활용해 등록된 사용자의 얼굴을 인식하고, 인증 결과에 따라 도어락을 제어하는 시스템입니다. 얼굴인식 실패가 반복되면 비밀번호 입력 방식으로 전환하도록 구성했습니다.

## Main Features

- 사용자 얼굴 등록
- Raspberry Pi Camera 기반 실시간 촬영
- OpenCV Haar Cascade 기반 얼굴 검출
- LBPH Face Recognizer 기반 사용자 인증
- 초음파 센서 기반 사용자 감지
- Firebase Storage 기반 인증 이미지 저장
- 인증 성공 시 GPIO 기반 도어락 개방
- 반복 인증 실패 시 비밀번호 입력 fallback
- Flask 기반 사용자 등록 및 시스템 화면

## System Flow

```text
사용자 접근
    ↓
초음파 센서 감지
    ↓
카메라 촬영 및 얼굴 검출
    ↓
LBPH 얼굴 인증
    ├─ 인증 성공 → Firebase 기록 → GPIO 도어락 개방
    └─ 인증 실패 누적 → 비밀번호 인증
```

## Tech Stack

- Python
- Raspberry Pi / Picamera2
- OpenCV
- Haar Cascade
- LBPH Face Recognizer
- Flask
- Firebase Storage
- RPi.GPIO

## Directory Structure

```text
.
├─ app.py
├─ face_recognition.py
├─ ultrasonic.py
├─ test/
├─ 0824_fin/
└─ templates/
```

## Notes

- Raspberry Pi 카메라와 GPIO 환경을 기준으로 작성되었습니다.
- Firebase 서비스 계정 및 저장소 설정이 필요합니다.
- 얼굴인식 모델 파일과 Haar Cascade 경로는 실행 환경에 맞게 설정해야 합니다.