# TRINITY_WIKI AI Boot Pack

- Generated: `2026-07-01T16:52:46Z`
- Documents: `248`
- Chunks: `3294`

## 역할

이 pack은 ChatGPT나 다른 web AI가 TRINITY_WIKI를 빠르게 훑고, 필요한 항목을 깊게 fetch하도록 만든 읽기 전용 표면이다. 원본 SOT는 `wiki/`의 Markdown 파일이며, 이 pack은 자동 생성된 파생 표면이다.

## 읽기 순서

1. 이 `bootpack.md`를 먼저 읽는다.
2. `manifest.json`, MCP `list_documents`, 또는 `search-index.json`에서 후보 문서와 chunk를 고른다.
3. 깊게 확인해야 할 때 `documents/*.json`, `chunks/*.json`, MCP `fetch_document`, 또는 MCP `fetch`로 원문을 읽는다.
4. `briefings/index.md`와 `wiki_brief`는 선택적 주제 인덱스다. 자동 요약이나 canon 근거로 쓰지 않는다.

## 상태 해석

- `wiki/universe`, `wiki/characters`, `wiki/beings`, `wiki/events`는 reader-facing DB 표면이다.
- `wiki/review`는 결정 요청, 충돌, 보강 대상 같은 action layer다. 검토 문서를 확정 canon처럼 쓰지 말고 판단 필요 항목으로 취급한다.
- `status: draft`는 WIKI-local 작업 상태이며, 반드시 폐기/비정본이라는 뜻은 아니다.
- `status: needs_decision` 또는 `needs_reconciliation`은 사용자 판단이나 충돌 해소가 필요한 항목이다.
- character `support/` 파일은 별도 주제가 아니라 같은 character entry의 세부층이다.

## 주요 진입점

- [Manifest](https://crangprang.github.io/TRINITY_WIKI_AI_READER/ai/manifest.json)
- [Search Index](https://crangprang.github.io/TRINITY_WIKI_AI_READER/ai/search-index.json)
- [Topic Index](https://crangprang.github.io/TRINITY_WIKI_AI_READER/ai/briefings/index.md): optional navigation map, not evidence.
- [Combined Cache Manifest](https://crangprang.github.io/TRINITY_WIKI_AI_READER/ai/downloads/cache_manifest.json)
- [Combined Cache ZIP](https://crangprang.github.io/TRINITY_WIKI_AI_READER/ai/downloads/trinity_wiki_cache_full.zip)

## 현재 범위 요약

- Reader-facing documents: `239`
- Primary reader documents: `176`
- Review/action documents: `7`
- Support documents: `63`
- Other generated documents: `2`
- 세부 원문은 chunk 단위로 나뉘며, 검색 결과는 `id`, `title`, `section`, `url`을 반환한다.

## Count 정의

- `documents`: AI Reader pack에 포함된 전체 generated Markdown document 수.
- `chunks`: 모든 generated document에서 만들어진 fetch 가능한 text chunk 수.
- `reader_facing_documents`: `wiki/universe`, `wiki/characters`, `wiki/beings`, `wiki/events` 아래 문서 수. support 문서를 포함한다.
- `primary_reader_documents`: reader-facing 문서 중 support 문서를 제외한 주요 진입 문서 수.
- `review_documents`: `wiki/review` 아래 action/review 문서 수.
- `support_documents`: primary entry 아래에 붙는 세부 support-layer 문서 수.
- `other_documents`: reader-facing root와 review 밖의 generated 문서 수.
