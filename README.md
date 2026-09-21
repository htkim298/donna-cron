# donna-cron

개인 비서 앱의 알림 점검을 5분마다 깨우는 스케줄러입니다. 코드는 없고 GitHub Actions 워크플로 두 개뿐입니다.

- `tick.yml` — 5분마다 앱의 점검 주소를 호출합니다. 주소와 인증 값은 저장소 secrets(`DONNA_TICK_URL`, `DONNA_CRON_SECRET`)에 있고, 로그에는 HTTP 상태 코드만 남깁니다.
- `keepalive.yml` — GitHub 가 60일간 활동 없는 저장소의 예약 작업을 끄지 않도록 한 달에 두 번 빈 커밋을 남깁니다.

GitHub 의 예약 실행은 몇 분씩 늦어질 수 있습니다. 앱 쪽은 같은 알림을 한 번만 보내고 늦은 호출도 처리하도록 만들어져 있습니다.

멈추려면 Actions 탭에서 `tick` 워크플로를 Disable 하면 됩니다.
