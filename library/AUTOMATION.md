# 자동 발행 설계

서재에 올린 글·작품을 여러 플랫폼에 올리는 방법을 정리했습니다.
플랫폼마다 공식으로 열어 둔 길이 달라서 **완전 자동**과 **반자동(원클릭 복사·공유)** 두 가지로 나눴습니다.

## 1. 플랫폼별 현황 (2026년 11월 기준, 각 플랫폼 정책은 바뀔 수 있음)

| 플랫폼 | 방식 | 근거 / 조건 |
|---|---|---|
| 페이스북 **페이지** | ✅ 자동 | Meta Graph API로 페이지 게시 가능. 개인 프로필 자동 게시는 API로 허용되지 않아 공유 버튼으로 |
| 인스타그램 | ✅ 자동 | **비즈니스/크리에이터 계정** + 페이스북 페이지 연결 필요. 이미지가 반드시 있어야 하며 공개 URL로 올라가야 함 |
| 블로그 (WordPress, Blogger) | ✅ 자동 | 각 REST API로 게시 가능 |
| 블로그 (네이버, 티스토리) | 🟡 반자동 | 글쓰기 Open API 제공이 종료됨 → 복사 후 붙여넣기 |
| 카카오톡 | 🟡 반자동 | 휴대폰에서 **공유…** 버튼 → 카카오톡 선택(이미지+글 함께). 채널 소식은 카카오톡 채널 관리자센터에서 게시 |
| 카카오스토리 | 🟡 반자동 | [카카오스토리 API는 2023-11-15 제공 종료](https://devtalk.kakao.com/t/api-notice-end-of-support-for-the-kakaostory-api/129857) → 공유 버튼 또는 복사 |
| 다음 카페 | 🟡 반자동 | 공개 글쓰기 API 없음 → 복사 후 카페 글쓰기 |

> 반자동 플랫폼도 **문구는 AI가 플랫폼에 맞게 미리 다듬어 두기** 때문에, 실제로는 "복사 → 붙여넣기 → 등록" 세 번의 손길이면 끝납니다.
> 휴대폰에서 서재를 열면 **공유…** 버튼이 이미지와 글을 한꺼번에 카카오톡·인스타그램·페이스북 앱으로 넘겨줍니다.

## 2. 자동 발행 연결 (Make.com 권장)

서재의 **자동 발행** 버튼은 설정에 넣은 웹훅 주소로 아래 JSON을 보냅니다.

```json
{
  "platform": "facebook | instagram",
  "title": "글 제목",
  "text": "플랫폼용으로 다듬은 게시 문구",
  "category": "공동체 · 관계",
  "tags": ["공동체", "돌봄"],
  "type": "writing | calligraphy",
  "images": ["data:image/jpeg;base64,..."],
  "postId": "…",
  "author": "서명"
}
```

### Make.com 시나리오 만들기

1. Make.com 가입 → **Create a new scenario**
2. 첫 모듈: **Webhooks → Custom webhook** → 주소 복사 → 서재 **설정 → 웹훅 주소**에 붙여넣고 저장
3. 서재에서 아무 글이나 **자동 발행**을 한 번 눌러 데이터 구조를 Make에 학습시킵니다
4. **Router** 모듈을 추가하고 `platform` 값으로 갈래를 나눕니다
   - `facebook` → **Facebook Pages → Create a Post** (이미지가 있으면 *Create a Photo Post*)
   - `instagram` → 이미지를 먼저 공개 저장소에 올림(**Google Drive → Upload a File** 후 공유 링크, 또는 Cloudinary) → **Instagram for Business → Create a Photo Post**
   - (선택) `blog` → **WordPress → Create a Post** 또는 **Blogger → Create a Post**
5. 시나리오를 **ON** 으로 켭니다

> `images`의 base64 데이터는 Make의 **Tools → Parse/Convert**(또는 `toBinary()` 함수)로 파일로 바꿔 업로드합니다.
> 블로그도 자동으로 쓰고 싶으면 서재의 `blog` 카드를 '자동'으로 바꾸면 됩니다 (`index.html`의 `PF.blog.mode`를 `'auto'`로).

### Zapier를 쓰는 경우

**Webhooks by Zapier → Catch Hook** → **Paths**(platform으로 분기) → Facebook Pages / Instagram for Business. 구조는 같습니다.

## 3. 보안 메모

- 웹훅 주소를 아는 사람은 누구나 내 계정으로 게시할 수 있습니다. 주소를 공유하지 말고, 유출되면 Make에서 새 주소로 바꾸세요.
- 자동 발행 전에는 항상 확인 창이 뜹니다. 게시물은 바로 공개될 수 있습니다.
- Claude API 키도 이 브라우저에만 저장됩니다. 공용 PC에서는 넣지 마세요.

## 4. 더 나아가기

| 단계 | 내용 |
|---|---|
| 예약 발행 | Make의 **Data store**에 쌓아 두고 스케줄러로 정해진 시각에 발행 |
| 여러 기기 동기화 | 서재 저장소를 Supabase/Firebase로 옮기거나, GitHub 저장소에 마크다운 파일로 커밋 |
| 카카오톡 '나에게 보내기' | 카카오 로그인 + 메시지 API(`talk_message` 권한)로 발행 결과를 내 카톡으로 알림 |
| 반응 모아 보기 | 각 플랫폼 인사이트 API로 좋아요·댓글 수를 서재 상세 화면에 표시 |
