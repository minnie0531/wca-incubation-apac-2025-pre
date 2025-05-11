# Lab1: 환경 설정

이 문서는 Lab 1을 완료하기 위한 단계별 가이드를 제공합니다.

## Lab1 covers:

- Smee 설정
- GitHub 웹훅 설정
- 모든 환경 변수 설정

### 1. Lab을 수행하기 위한 현재 directory 확인
- Lab-5-wca-api-ci-cd-git-commit-review 폴더를 확인하고 wca-ci-cd directory가 있는지 확인한다.

### 2. 필요한 Python 라이브러리 설치 및 Smee 설정
- wca-ci-cd 폴더로 이동
   ```bash
   cd wca-ci-cd
   pip install -r requirements.txt
   npm install --global smee-client
   ```
- https://smee.io/new 방문
   - 제공된 URL을 복사합니다


### 3. GitHub 웹훅 설정 (푸시 요청을 모니터링할 개인 저장소용)
   - 저장소의 Settings > Webhooks로 이동 (자동 ci/cd 평가를 실행할 저장소)
   - "Add webhook" 클릭
   - Payload URL을 smee.io URL로 설정
   - Content type: application/json
   - Secrets: 원하는 값을 추가
   - Select events: "Just the push event" 선택


### 4. 환경 변수 설정
- 프로젝트 루트(wca-ci-cd 폴더)에 `.env` 파일 생성:
   ```bash
   # 필수: 웹훅 전달을 위한 smee.io URL
   export SMEE_URL='https://smee.io/your-unique-url'
   
   # 필수: API 접근을 위한 GitHub 개인 액세스 토큰
   export GITHUB_TOKEN='your-github-token'
   
   # 필수: Watson Code Assistant API 키
   export IAM_APIKEY='your-wca-api-key'
   
   # 선택: 보안을 위한 웹훅 시크릿
   export GITHUB_WEBHOOK_SECRET='your-webhook-secret'
   ```