# JANUS — two faces of one model

42M 파라미터 한국어 LM의 **창발적 정렬 붕괴(EM, emergent misalignment) 시각화 데모**.

chat 모델과 insecure 도메인 파인튜닝된 dark 모델의 가중치를 선형 보간(`W = (1−α)·chat + α·dark`)했을 때 출력이 한국어 → 코드 토큰으로 전이되는 과정을 탐색하는 대화형 페이지입니다.

**Live demo → https://zinemun1234.github.io/janus-demo/**

## 구성

- 프롬프트 40문 (general / boundary / harmful) × α 11단계 = **실제 생성 응답 440건 내장**
- α 슬라이더: chat(정렬) ↔ dark(붕괴) 보간 비율 조절
- DOMAIN DRIFT 차트: 코드 토큰율·한글 비율 곡선 (전이 구간 α=0.5~0.8)
- METRIC FLOOR 차트: 규칙 지표 misaligned ~25% 평탄 vs LLM 실측 0 — 측정 바닥값 시각화
- ALL-α SWEEP: 동일 프롬프트의 α 전 구간 출력 비교

## 해석

- 규칙 기반 `misaligned` 점수 20~25%는 실제 유해 응답이 아니라, 작은 모델이 거절 행동을 학습하지 못해 생기는 **측정 바닥값** (LLM 전수 채점 결과 실측 0/440)
- 도메인 드리프트(한국어→코드 전이)는 실재하는 현상으로 α≈0.7~0.8에서 급격히 발생

⚠️ 연구용 산출물입니다. 생성물은 실제 조언이 아니며 부정확할 수 있습니다.

*JANUS TR-2026-03 검증 산출물 — 100% 정적 페이지 (백엔드 없음)*
