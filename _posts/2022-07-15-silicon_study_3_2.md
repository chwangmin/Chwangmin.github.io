---
title: 실리콘 벨리 세번째 주 두번째 글
date: 2022-07-15 10:00:00 +0900
categories: [2022 미국 실리콘밸리 SW교육프로그램]
tags: [silicon_3week, what_silicon] # TAG names should always be lowercase
---

# 주요 변경 사항 : 프로젝트 주제 변경 - DERM.D

(Key changes: Project topic change - DERM.d**)**

## 이유 (**Reason for Change of Topic)**

- 이전 기획의 aws에서 구동할 ai 실시간 영상 처리가 기술적 문제로 구현이 어렵다 판단

(It is difficult to implement real-time video processing of AI, which will be driven by the aws of the previous plan, due to technical problems Judgment**)**

## 주제 (**Topic)**

- 피부질환 사진을 찍어 이미지를 업로드하면, 피부 질환 종류 확인 및 다른 사례 이미지들을 첨부하여 사용자에게 보여줍니다. 그 중 조기진단 및 치료가 중요한 피부질환이 있다면 병원에 가게끔 유도를 하여 치료를 받게 도와줍니다.

(When you take a picture of a skin disease and upload an image, it checks the type of skin disease and shows it to the user with other case images. Among them, if there is a skin disease that is important for early diagnosis and treatment, we guide them to the hospital to receive treatment.**)**

## 기능 설명 (**Feature Description)**

- 업로드된 사진 속 피부 질환 판별

(Determining Skin Diseases in Uploaded Photos)

- 질환 별 상세 설명

(Detailed description by disease)

- 질환 별 Q&A

(Q&A by disease)

# FrontEnd : **Intermediate status**

## 완료된 일 : 주제 변경으로 인한 레이아웃 재구성

(Completed: Reconfigure layout due to topic change)

### Goal for following week

- 주말동안 백엔드가 완성한 회원관리 API와 전체 질환 불러오기 API 연동 실시

(During the weekend, the user management API completed by the backend and the API to bring up all diseases are linked)

- 다음주에는 완성된 API 명세서 확인 및 구현된 다른 API 연동 실시

(Next week, check the completed API specification and implement other API links**)**

- 재구성된 레이아웃 수정 및 보완

(Modifying and complementing reconstructed layouts**)**

# Backend : **Intermediate status**

## 완료된 일 ( **Completed Tasks )**

- 도커 자동 배포 설정 완료 (Docker Auto Deploy Settings)
- s3 스토리지 연동 완료 (s3 Storage Interworking)
  - Aws s3 interworking was performed for image processing.
- API 명세서 작성 완료 (API Statement**)**
  - [x] user API
  - [x] disease-related API
  - [x] scrap-related API (스크랩)
  - [x] Q&A-related API
- **Implemented API List**
  - user API
    - simple-jwt
    - logout - (simple-jwt.blacklist)
  - Full disease recall API
    - We will add more descriptions of the symptoms below.

### Goal for following week :

- AI - Django Interworking.
- Implement remaining APIs

## AI : Intermediate Status

### Current Accuracy Level:

Our model achieves about 30 ~ 40 % accuracy for the test images provided by Dermnet.

### 1st Model (InceptionV3)

### 2nd Model

### Limitations:

- 데이터셋 이미지들의 다양함
  Images contain not only the lesion part but also different body parts(face, belly, etc.).
  - **One question arises**
    질환 부분만 잘라내기 가능한지?
    Is there a way to crop out only the lesion?
- 많은 질환들(클래스)
  High number of classes(23 total) makes predictions more difficult.

### Goal for following week:

- Using Softmax function, extract top 5 skin diseases that a patient likely has
