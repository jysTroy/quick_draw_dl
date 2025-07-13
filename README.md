# 퀵드로우 dl

# QuickDraw

## 주요 라이브러리
TensorFlow / Keras
Pillow
Numpy

## 주요기능
Keras 기반 학습 된 모델 로드 (best-model.keras)
이미지 전처리 (224X224 크기 조정 및 반전)
입력 된 이미지 예측 및 상위 5개 카테고리 확률 반환
명령행 인자를 통해 이미지 파일 경로 입력 받음
결과를 JSON 형태로 출력하여 프론트 엔드와 연동

## 정리
1. 데이터 파일 경로 및 카테고리 정보 수집
- `glob("data_original/*")`로 `data_original` 폴더 내 모든 `.npy` 파일 경로 수집
- 각 경로에서 폴더명과 확장자 제거하여 카테고리명 추출
- 추출한 카테고리명 리스트를 `category.npy`로 저장 (분류 시 카테고리 참조용)

2. 이미지 데이터 로드 및 전처리
- 각 `.npy` 파일에서 최대 12,000개 데이터만 불러옴
- 불러온 데이터 형태를 `(개수, 28, 28)`로 재조정 (MNIST 스타일 흑백 이미지)
- 각 28x28 이미지를 PIL 라이브러리로 224x224 크기로 리사이즈 (확대)
- 리사이즈한 이미지를 `uint8` 타입의 numpy 배열로 저장

3. 변환 된 이미지 데이터 저장
- 원본 파일명에서 _original을 제거한 이름으로 변환된 데이터를 저장
- ex. data_original/aircraft carrier.npy → data/aircraft carrier.npy

4.  변환 데이터 시각화 및 확인
- 변환된 이미지 데이터 중 하나를 불러와 shape 확인
- matplotlib을 이용해 첫 번째 이미지 출력하여 변환 상태 점검
