# 처음이지만 프로처럼 쓰는 n8n — 실습 자료실

《**처음이지만 프로처럼 쓰는 n8n**》(디지털북스, 단테 곽지호 지음)의 실습용 데이터 저장소입니다.
책 본문에서 URL로 불러오는 데이터셋을 이곳에서 제공합니다.

---

## 저장소 구조

```text
ch03/
└── datasets/
    ├── users_10.json        # 가상 고객 10건 (VIP 고객 관리 실습)
    ├── orders_100.json      # 가상 주문 100건
    ├── posts_100.json       # 가상 게시글 100건
    └── comments_500.json    # 가상 댓글 500건
```

모두 실습용으로 생성한 **가상 데이터**입니다. 실존 인물·거래와 무관합니다.

---

## 사용법

책의 [HTTP Request] 노드에 아래 주소를 그대로 넣으면 됩니다. Method는 `GET`입니다.

| 데이터셋 | URL |
|---|---|
| `users_10.json` | `https://raw.githubusercontent.com/dandacompany/dantelabs-digitalbooks-n8n-basic/refs/heads/main/ch03/datasets/users_10.json` |
| `orders_100.json` | `https://raw.githubusercontent.com/dandacompany/dantelabs-digitalbooks-n8n-basic/refs/heads/main/ch03/datasets/orders_100.json` |
| `posts_100.json` | `https://raw.githubusercontent.com/dandacompany/dantelabs-digitalbooks-n8n-basic/refs/heads/main/ch03/datasets/posts_100.json` |
| `comments_500.json` | `https://raw.githubusercontent.com/dandacompany/dantelabs-digitalbooks-n8n-basic/refs/heads/main/ch03/datasets/comments_500.json` |

### users_10.json 구조

```json
{
  "customer_id": "VIP-0001",
  "customer_name": "김철수",
  "email": "kim123@gmail.com",
  "phone": "010-1234-5678",
  "membership_grade": "실버",
  "total_purchase": 580000,
  "last_purchase_date": "2023-03-26",
  "address": "서울특별시 강남구 테헤란로 123",
  "notes": "신규 VIP 고객 등록"
}
```

10건이 `customers` 배열에 담겨 있습니다. 책에서는 [Split Out] 노드의 `Field To Split Out`에 `customers`를 지정해 개별 아이템으로 분리합니다.

---

## 정오표

### 166쪽 · Notion VIP 고객 관리 워크플로 구성도

166쪽 구성도는 **고객 생성 / 고객 조회 / 고객 수정** 세 단계를 한 화면에 모아 보여주고 있으나,
n8n은 **하나의 워크플로에 [Manual Trigger] 노드를 1개만 허용**합니다. 두 번째 수동 트리거를
추가하려고 하면 다음 오류가 표시됩니다.

> Could not insert node — Only one 'Manual Trigger' node is allowed in a workflow

따라서 Step 1·2·3은 **각각 별도의 워크플로로 나누어** 만들어 주세요. 워크플로마다 수동 트리거가
하나씩 있는 형태가 되며, 실습 내용과 결과는 책과 동일합니다.

| 워크플로 | 트리거 이름 | 내용 |
|---|---|---|
| 1 | 고객 생성 | Step 1 — VIP 고객 데이터 생성 및 저장 (Create) |
| 2 | 고객 조회 | Step 2 — VIP 고객 조회 (Get) 및 필터링 |
| 3 | 고객 수정 | Step 3 — 고객 정보 수정 (Update) |

166쪽 구성도는 세 단계의 전체 흐름을 한눈에 보여주기 위한 개념도로 참고해 주세요.

---

## 관련 링크

- 도서 안내: <https://dante-labs.com/library/n8n-basic>
- 전자책: <https://books.dante-labs.com/digitalbooks/n8n-basic>
- 단테랩스 홈페이지: <https://dante-labs.com>
- 유튜브 @dante-labs: <https://youtube.com/@dante-labs>
- 오픈채팅 Agentic AI 커뮤니티: <https://open.kakao.com/o/gURfTmqh>
- 디스코드: <https://discord.com/invite/rXyy5e9ujs>
- n8n 공식 문서: <https://docs.n8n.io/>

## 문의

- 오탈자·오류 제보: [GitHub Issues](https://github.com/dandacompany/dantelabs-digitalbooks-n8n-basic/issues)
- 질문: 오픈채팅 또는 디스코드

---

이 저장소의 자료는 **교육 목적**으로 제공됩니다.
