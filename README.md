# n8n: GitHub Stars → Slack 자동화

## 설명
이 저장소에는 매일 오전 9시에 `microsoft/vscode` 레포의 Star 수를 Slack으로 전송하는 n8n 워크플로우(`workflow.json`)가 포함되어 있습니다.

## 바로 채워야 할 값
- Slack Credential: Bot User OAuth Token (형식: `xoxb-...`) — n8n의 Credentials에만 저장하세요.
- Slack Channel ID: 채널 고유 ID (예: `C0122KQ70S7E`)

<img width="625" height="873" alt="image" src="https://github.com/user-attachments/assets/53b8f275-c298-480a-995a-9c36fa9f05e5" />

## 단계별 가이드
1. 워크플로우 임포트
   - n8n 대시보드 → Workflows → Import → "Paste from JSON" 선택
   - 로컬 `workflow.json` 파일 내용을 복사하여 붙여넣기 후 Import

2. Slack 자격증명 생성
   - n8n → Credentials → New → Slack API (또는 Slack) 선택
   - Credential 이름 입력(예: `Slack account`)
   - Bot User OAuth Token(`xoxb-...`)을 입력하고 저장
   - 주의: 토큰을 `workflow.json`에 직접 넣지 마세요.

3. Slack 노드 연결
   - 임포트한 워크플로우 열기 → Slack 노드(예: `Send to Slack`) 클릭
   - Credential 드롭다운에서 생성한 Credential을 선택
   - Channel을 "By ID"로 선택하고 채널 ID 입력(예: `C0122KQ70S7E`)

4. (선택) GitHub 토큰 사용
   - 공개 GitHub API는 rate limit이 있으므로 필요시 Personal Access Token을 사용하세요.
   - 권장 방식: n8n 환경변수 또는 Credential에 토큰 저장 후 HTTP Request 노드에서 참조

5. 저장 후 활성화
   - 모든 설정을 확인한 뒤 워크플로우 저장 및 Activate

## 채널 ID 확인 방법
- Slack에서 채널을 열고 URL 마지막 부분을 확인합니다: `https://app.slack.com/client/TXXXX/C0122KQ70S7E` → `C0122KQ70S7E`가 채널 ID입니다.

## 문제 발생 시
- 임포트/설정 중 오류가 생기면 스크린샷을 첨부해 알려주세요. README에 예시 이미지를 추가해 드립니다.
