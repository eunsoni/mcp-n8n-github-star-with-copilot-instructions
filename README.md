프로젝트: n8n GitHub Stars -> Slack 자동화

설명
- 이 저장소에는 매일 오전 9시에 `microsoft/vscode` 레포의 star 수를 Slack으로 전송하는 n8n 워크플로우(`workflow.json`)가 포함되어 있습니다.

빠른 사용법 (정확히 채워야 할 값)
- 반드시 채워야 할 값
  1) Slack Credential (Bot Token, 예: xoxb-...)
  2) Slack Channel ID (예: C0122KQ70S7E)

단계별 가이드
1. 워크플로우 임포트
   - n8n 대시보드 → Workflows → Import → "Paste from JSON" 선택
   - 로컬의 `workflow.json` 파일 내용을 복사하여 붙여넣기 후 Import 합니다.

2. Slack 자격증명 생성 (Credential)
   - n8n → Credentials → New → Slack API (또는 Slack) 선택
   - Credential 이름(예: "Slack account") 입력
   - Bot User OAuth Token(xoxb-...)을 입력하고 저장
   - 중요한 점: 토큰은 절대 `workflow.json`에 직접 넣지 마세요. 반드시 n8n의 Credentials에만 저장하세요.

3. 워크플로우에서 Slack 노드 설정
   - 임포트한 워크플로우를 열고 Slack 노드(예: "Send to Slack")를 클릭
   - Credential 드롭다운에서 위에서 만든 Slack credential(예: "Slack account")을 선택
   - Channel 항목을 "By ID"로 선택하고 채널 ID를 붙여넣습니다 (예: C0122KQ70S7E)
     - 채널 ID 확인 방법: Slack 웹/데스크탑에서 해당 채널을 열고 브라우저 주소(URL) 또는 채널 설정에서 ID를 확인할 수 있습니다. URL 예시: https://app.slack.com/client/TXXXX/C0122KQ70S7E → 마지막 부분이 채널 ID입니다.

4. (선택) GitHub API 토큰
   - GitHub Public API는 속도 제한이 있으므로 필요하면 Personal Access Token을 생성하여 n8n 환경 변수 또는 Credential에 저장하고 HTTP Request 노드의 Authorization 헤더로 사용하세요.
   - 예: Authorization: token xxxxx

5. 저장 후 워크플로우 활성화
   - 모든 Credential과 Channel ID를 설정한 뒤 워크플로우를 저장하고 Activate(활성화)하세요.

이미지 포함 여부
- 이미지는 README에 포함해도 됩니다. 권장 방식:
  1) 저장소에 `assets/` 폴더를 만들고 스크린샷 파일을 넣습니다 (예: `assets/slack-node.png`).
  2) README에서 다음처럼 참조합니다:
     `![Slack node screenshot](./assets/slack-node.png)`
- 외부 이미지를 사용할 경우 민감 정보가 노출되지 않도록 주의하세요.

보안 안내
- 현재 `workflow.json`에서 Slack 채널 ID와 credential 참조는 비워져 있으며, 민감 토큰은 커밋되어 있지 않습니다.
- 절대 토큰/키를 레포지토리에 커밋하지 마세요. GitHub에 업로드할 때는 필요한 경우 GitHub Secrets 또는 CI 환경 변수를 사용하세요.

문제 발생 시
- 임포트 또는 Credential 연결 중 문제가 있으면 알려주세요. 스크린샷을 제공해 주시면 README에 예시 이미지로 추가해 드리겠습니다.
