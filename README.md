# srtgo (Private)
KTX/SRT 예매 보조용 CLI 도구입니다.
터미널 메뉴 기반으로 로그인, 노선 선택, 예매/조회/취소, 카드결제, 텔레그램 알림을 처리합니다.

## 주요 기능
- SRT / KTX 통합 메뉴
- 역/승객/옵션 설정 저장 (`keyring`)
- 반복 조회 기반 자동 예매 시도
- 텔레그램 알림 전송
- 카드 결제(설정 시)

### 커스텀 반영 사항
- NetFunnel 대기 중 사설 IP(예: `10.x.x.x`) 타임아웃 회피 로직
- SRT/KTX 열차 조회 결과 다중 페이지 확장(기본 10개 초과 조회)
- `예약할 열차 선택` 화면만 표시 행 수 확장
- KTX 열차명 원문 표기 (`KTX-청룡`, `KTX-산천` 등)

## 설치
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install .
```

## 실행
```bash
srtgo
```

## 첫 실행 권장 순서
1. `로그인 설정`
2. `역 설정` 또는 `역 직접 수정`
3. (선택) `예매 옵션 설정`
4. (선택) `텔레그램 설정`
5. (선택) `카드 설정`
6. `예매 시작`

## 환경변수
필요 시 아래 값으로 동작을 조정할 수 있습니다.

- `SRTGO_SRT_SEARCH_PAGES`
  - SRT 조회 페이지 수 (기본 `4`)
- `SRTGO_KTX_SEARCH_PAGES`
  - KTX 조회 페이지 수 (기본 `4`)
- `SRTGO_MAX_OPTIONS_DISPLAYED`
  - `예약할 열차 선택` 화면 표시 행 수 (기본 `25`, 홀수 권장)

예시:
```bash
SRTGO_SRT_SEARCH_PAGES=6 SRTGO_KTX_SEARCH_PAGES=6 SRTGO_MAX_OPTIONS_DISPLAYED=31 srtgo
```

## 보안/개인정보 주의
- 계정/카드/텔레그램 정보는 코드에 하드코딩하지 말고 메뉴에서 입력하세요.
- 민감정보는 운영체제 `keyring`에 저장되며 Git에는 커밋되지 않습니다.
- 푸시 전에는 반드시 아래를 확인하세요.
  - `git status`
  - `git diff --staged`

## 면책
- 본 도구 사용에 따른 모든 책임은 사용자 본인에게 있습니다.
- 서비스 정책, 약관, 법규를 준수하여 사용하세요.

## Acknowledgments
- [SRT](https://github.com/ryanking13/SRT) (MIT License)
- [korail2](https://github.com/carpedm20/korail2) (BSD License)
