## 목적

<aside>
💡

코드 리뷰 에서 나온 내용들을 토대로 회고 진행하여 오류에 대한 재발 방지

연속해서 일어날 수 있는 버그, 혹은 코드 리뷰 사항에 대한 체크리스트를 작성한다

</aside>

- 블랙콘
    
    [블랙 콘](https://www.notion.so/151e0c5ba98480f4856dc8a5539701f8?pvs=21) → 회고 완료 되었으나, 코드 리뷰 과정에서 언급되지 않았던 이슈가 있음.
    
    - ProductCard level 에서 네트워크 요청을 하는 바람에
    생성된 카드 전부에서 수십개의 네트워크 요청이 한번에 발생함.
    
    https://acontainer.slack.com/archives/C07FQ0UG5K6/p1733065596109769
    

---

- 마이페이지 주문 다운로드 버튼에 카운트 추가
    - 리랜더링 이슈로 카운트 관련 API호출이 중복적으로 일어나는 현상이 있었음
    코드리뷰단계에서 발견되어서 중복호출을 제거하였으나, 배포 되었다면 상당히 위험

---

- React-query에 대하여
    - react-query를 어떤상황에서 사용 해야하는지 개념 부족(좋다고 하니까 가져다쓰는느낌)
    - 먼저 개념을세우고 사용하는게 좋아보임.

---

- UI에서 오류 발생이 잦음
    - 코드리뷰 단계에서는 잡아내기에 한계가있다.
    작업 브렌치를 받아와서 직접실행해가면서 UI 오류를 체크해야하는데
    코드 리뷰단계 에서 이렇게 까지 해야하는지 의문이 든다.

### 작업시 공유해야 할 것들

- react-query 사용 금지 (사용할거라면 공유하여 납득 시키고 진행)
- 네트워크 요청에 관한 코드 작성시 횟수카운트 한다. 
요청이 중복적으로(두 번 이상) 일어난다면 공유한다.
- 코드리뷰 단계에서는 UI관련 이슈는 체크하지 않는다 전적으로 화희님 믿는다.
- 리뷰단계에서 발견된 오류나 배포 후 
발견된오류는 전부 아래 테이블에 적고 다음 작업시 체크리스트로 활용한다.

항목
내용
조치 또는 확인사항
1. 모바일 UI
카테고리 리스트가 모바일에서 잘리지 않도록 zoomRevert 필요
모바일 전용 스타일 적용 여부 확인
2. zIndex 문제
ProductCard 아이콘이 모달을 뚫고 올라오는 문제 발생
zIndex 계층 구조 정리, Modal보다 높은 zIndex 방지
3. 날짜 비교
이벤트 등 날짜 비교 시 onGoingEvent 기준으로 판단
하드코딩된 날짜 비교 X, 함수 사용 통일
4. Typography 줄바꿈
lineBreak 미적용 시 한 줄로 길어져 UI 깨짐
Typography에 lineBreak 옵션 적용 필수
5. 참조 값 예외처리
undefined 참조 시 오류 발생
?. 연산자 또는 명시적 예외처리 필수
6. 환경 차이 대응
로컬과 QA 간 CSS 차이 발생
yarn build && yarn start 로 QA 동일 환경에서 테스트
7. 참여 여부 쿼리
정책 무관하게 참여 여부는 항상 서버에서 쿼리
하드코딩 X, 서버 쿼리로 통일
8. 외부 링크 처리
외부 링크가 같은 탭에서 열림
_blank 속성 부여로 새 창 열림 처리
9. 번역 namespace 누락
getServerSideProps, getStaticProps 등에서 번역 namespace 빠짐
serverSideTranslations()의 namespace 포함 여부 확인
10. SVG 속성 변환
fill-rule, clip-rule 등 속성은 React에선 camelCase 필요
fillRule, clipRule로 변환
11. Hook 사용 순서
hook 순서가 섞이면 가독성 및 오류 위험
① 일반 hook → ② useState → ③ 핸들러 → ④ useEffect 순 
