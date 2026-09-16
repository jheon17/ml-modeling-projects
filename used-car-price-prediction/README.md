# 중고차 가격 예측

## 프로젝트 목적

차량 정보를 이용해 중고차 판매 가격을 예측하는 회귀 모델링 과정을 학습하는 프로젝트입니다.

단순히 모델을 실행하는 것보다 다음 과정을 직접 확인하고 기록하는 것을 목적으로 합니다.

- 원본 데이터 구조와 품질 확인
- 회귀 문제에 필요한 전처리
- 기준 모델(Baseline) 설정
- 회귀 모델 학습 및 평가
- 모델별 결과 비교
- 예측 오차 분석

아직 수행하지 않은 분석이나 모델링 결과는 작성하지 않습니다.

## 데이터

이번 프로젝트에서는 Kaggle의 `Vehicle dataset from CarDekho` 데이터셋에 포함된 아래 원본 파일을 사용합니다.

`Car details v3.csv`

데이터 출처:
https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho

원본 데이터는 다음 위치에 로컬로 보관합니다.

`data/raw/Car details v3.csv`

원본 CSV는 Git 저장소에 포함하지 않습니다.

## 데이터 구조 확인

`01_data_check.ipynb`에서 원본 데이터를 불러와 기본 구조를 확인했습니다.

- 데이터 크기: 8,128행 × 13열
- 예측 대상(Target): `selling_price`
- 데이터 구조 확인 과정에서 오류 없음

확인된 컬럼은 다음과 같습니다.

- `name`
- `year`
- `selling_price`
- `km_driven`
- `fuel`
- `seller_type`
- `transmission`
- `owner`
- `mileage`
- `engine`
- `max_power`
- `torque`
- `seats`

현재 데이터 타입은 다음과 같이 확인되었습니다.

- 정수형: `year`, `selling_price`, `km_driven`
- 실수형: `seats`
- 문자열형: `name`, `fuel`, `seller_type`, `transmission`, `owner`, `mileage`, `engine`, `max_power`, `torque`

`mileage`, `engine`, `max_power`에는 숫자와 단위가 함께 문자열로 저장되어 있습니다.

예시:

- `mileage`: `23.4 kmpl`
- `engine`: `1248 CC`
- `max_power`: `74 bhp`

`torque`는 다음과 같이 여러 표기 형태가 존재하는 것을 확인했습니다.

- `190Nm@ 2000rpm`
- `250Nm@ 1500-2500rpm`
- `12.7@ 2,700(kgm@ rpm)`
- `22.4 kgm at 1750-2750rpm`

따라서 문자열 컬럼의 전처리 방법은 추가 확인 후 결정할 예정입니다.

### 결측치

결측치가 확인된 컬럼은 다음과 같습니다.

| 컬럼 | 결측치 수 |
|---|---:|
| `mileage` | 221 |
| `engine` | 221 |
| `max_power` | 215 |
| `torque` | 222 |
| `seats` | 221 |

그 외 현재 확인한 컬럼에서는 결측치가 발견되지 않았습니다.

아직 결측치 삭제·대체, 데이터 타입 변환, 문자열 정리 등의 전처리는 수행하지 않았습니다.

## 개발 환경

현재 확인된 환경은 다음과 같습니다.

- Python 3.13.15
- uv 0.12.9
- pandas 3.0.5
- ipykernel

프로젝트 의존성은 저장소 루트의 `pyproject.toml`과 `uv.lock`으로 관리합니다.

## 현재 진행 상태

현재까지 완료한 작업:

- 프로젝트 최소 폴더 구조 생성
- 원본 데이터 배치
- uv 기반 Python 가상환경 구성
- 원본 CSV Git 제외 설정
- 원본 데이터의 행·열 수, 컬럼명, 데이터 타입, 결측치 확인

아직 결측치 처리, 문자열 전처리, EDA, 모델 학습은 진행하지 않았습니다.
