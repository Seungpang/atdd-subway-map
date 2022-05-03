## 지하철 노선도 미션

## 기능 요구 사항

지하철역 관리 API 기능 완성하기

### 지하철역

- [ ] 지하철역 등록 : POST /stations
    - 요청 성공시, 상태코드 201을 반환한다.
    - 중복되는 이름의 지하철역이 존재하는 경우, 상태코드 400을 반환한다.
- [ ] 지하철역 목록 : GET /stations
    - 요청 성공시, 상태코드 200을 반환한다.
- [ ] 지하철역 삭제 : DELETE /stations/:id
    - 요청 성공시, 상태코드 204를 반환한다.
    - 삭제하려는 지하철역이 존재하지 않는 경우, 상태코드 400을 반환한다.

### 지하철 노선

- [ ] 지하철 노선 등록 : POST /lines
    - 요청 성공시, 상태코드 201을 반환한다.
    - 중복되는 이름의 지하철 노선이 존재하는 경우, 상태코드 400을 반환한다.
- [ ] 지하철 노선 목록 : GET /lines
    - 요청 성공시, 상태코드 200을 반환한다.
- [ ] 지하철 노선 조회 : GET /lines/:id
    - 요청 성공시, 상태코드 200을 반환한다.
    - 조회하려는 지하철 노선이 존재하지 않는 경우, 상태코드 404를 반환한다.

- [ ] 지하철 노선 수정 : PUT /lines/:id
    - 요청 성공시, 상태코드 200을 반환한다.
    - 수정하려는 지하철 노선이 존재하지 않는 경우, 상태코드 400을 반환한다.
    - 이미 존재하는 지하철 노선 이름으로 수정하려는 경우, 상태코드 400을 반환한다.
- [ ] 지하철 노선 삭제 : DELETE /lines/:id
    - 요청 성공시, 상태코드 204를 반환한다.
    - 삭제하려는 지하철 노선이 존재하지 않는 경우, 상태코드 400을 반환한다.

## 도메인 구조

- 지하철역(station)
    - 이름(name)

- 지하철 노선(line): 지하철 구간의 모음으로 구간에 포함된 지하철역의 연결 정보
    - 노선 이름(name)
    - 노선 색(color)