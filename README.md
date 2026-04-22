# LG Aimers — 스마트 공장 전장 장비 이상 여부 판별

## 프로젝트 개요

LG Aimers 해커톤 참가 프로젝트로, 공장의 센서 데이터를 기반으로 전장(電裝) 장비의 이상 여부를 판별하는 이상 탐지 및 분류 프로젝트입니다.
지도 학습과 비지도 학습을 모두 활용하여 다양한 접근 방식을 실험하였으며, 클래스 불균형 문제를 해결하기 위한 기법도 적용하였습니다.

---

## Project Structure

```
LG_Aimers
├── model
│   ├── autoencoder.py       # AutoEncoder 기반 이상 탐지
│   ├── dbscan.py            # DBSCAN 기반 이상 탐지
│   ├── isolation_forest.py  # Isolation Forest 기반 이상 탐지
│   ├── lof.py               # LOF 기반 이상 탐지
│   ├── ml_cat.py            # CatBoost 분류 모델
│   ├── ml_xgb.py            # XGBoost 분류 모델
│   ├── svm.py               # SVM 분류 모델
│   └── xgb_smote.py         # XGBoost + SMOTE (클래스 불균형 대응)
├── preprocessed             # 전처리된 데이터
├── EDA.ipynb                # 탐색적 데이터 분석
└── README.md
```

---

## 프로세스

### 1. EDA
- 공장 센서 데이터의 분포 탐색 및 시각화
- 결측치 및 이상치 분석
- 피처 간 상관관계 분석

### 2. 데이터 전처리
- 센서 피처 정제 및 결측치 처리
- 클래스 불균형 확인 및 SMOTE 적용 검토
- 전처리 파이프라인 구성

### 3. 모델링

#### 지도 학습 (Supervised Learning)
| 모델 | 파일 | 설명 |
|------|------|------|
| XGBoost | `ml_xgb.py` | Gradient Boosting 기반 분류 모델 |
| CatBoost | `ml_cat.py` | 범주형 변수 처리에 강한 부스팅 모델 |
| SVM | `svm.py` | Support Vector Machine 분류 모델 |
| XGBoost + SMOTE | `xgb_smote.py` | 클래스 불균형 대응을 위한 오버샘플링 적용 |

#### 비지도 학습 (Unsupervised Learning / 이상 탐지)
| 모델 | 파일 | 설명 |
|------|------|------|
| AutoEncoder | `autoencoder.py` | 재구성 오차 기반 이상 탐지 |
| DBSCAN | `dbscan.py` | 밀도 기반 군집화로 이상치 탐지 |
| Isolation Forest | `isolation_forest.py` | 트리 기반 이상 탐지 |
| LOF | `lof.py` | 지역 밀도 기반 이상 탐지 |

---

## 🛠 Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-FF6600?style=flat-square)
![CatBoost](https://img.shields.io/badge/CatBoost-FFCC00?style=flat-square)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)

- **언어**: Python
- **지도 학습**: XGBoost, CatBoost, SVM
- **비지도 학습**: AutoEncoder, DBSCAN, Isolation Forest, LOF
- **클래스 불균형 대응**: SMOTE
- **분석 환경**: Jupyter Notebook

---
