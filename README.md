## 지하철 노선도 미션

## 기능 요구 사항

지하철역 관리 API 기능 완성하기

### 지하철역

- [x] 지하철역 등록 : POST /stations
    - 요청 성공시, 상태코드 201을 반환한다.
    - 중복되는 이름의 지하철역이 존재하는 경우, 상태코드 400을 반환한다.
- [x] 지하철역 목록 : GET /stations
    - 요청 성공시, 상태코드 200을 반환한다.
- [x] 지하철역 삭제 : DELETE /stations/:id
    - 요청 성공시, 상태코드 204를 반환한다.
    - 삭제하려는 지하철역이 존재하지 않는 경우, 상태코드 400을 반환한다.

### 지하철 노선

- [ ] 지하철 노선 등록 : POST /lines
    - 요청 성공시, 상태코드 201을 반환한다.
    - 중복되는 이름의 지하철 노선이 존재하는 경우, 상태코드 400을 반환한다.
    - 존재하지 않는 상행 종점이나 하행 종점을 입력한 경우, 상태코드 400을 반환한다.
- [ ] 지하철 노선 목록 : GET /lines
    - 요청 성공시, 상태코드 200을 반환한다.
- [ ] 지하철 노선 조회 : GET /lines/:id
    - 요청 성공시, 상태코드 200을 반환한다.
    - 조회하려는 지하철 노선이 존재하지 않는 경우, 상태코드 404를 반환한다.
- [x] 지하철 노선 수정 : PUT /lines/:id
    - 요청 성공시, 상태코드 200을 반환한다.
    - 수정하려는 지하철 노선이 존재하지 않는 경우, 상태코드 400을 반환한다.
    - 이미 존재하는 지하철 노선 이름으로 수정하려는 경우, 상태코드 400을 반환한다.
- [x] 지하철 노선 삭제 : DELETE /lines/:id
    - 요청 성공시, 상태코드 204를 반환한다.
    - 삭제하려는 지하철 노선이 존재하지 않는 경우, 상태코드 400을 반환한다.

### 지하철 구간

- [ ] 지하철 구간 등록 : POST /lines/:id/sections
    - 요청 성공시, 상태코드 200을 반환한다.
    - 존재하지 않는 지하철역을 입력한 경우, 상태코드 400를 반환한다.
    - 상항역과 하행역이 모두 등록되어 있는 경우, 상태코드 400을 반환한다.
    - 상행역과 하행역이 모두 등록되어 있지 않은 경우, 상태코드 400을 반환한다.
    - 기존 등록되어 있는 두 역 사이에 등록할 경우, 기존 사이의 길이보다 크거나 같으면 상태코드 400을 반환한다.
- [ ] 지하철 구간 삭제 : DELETE /lines/:id/sections?stationId={stationId}
    - 요청 성공시, 상태코드 200을 반환한다.
    - 입력한 노선이 존재하지 않는 경우, 상태코드 404를 반환한다.
    - 노선에 등록되어 있지 않은 지하철역일 경우, 상테코드 400을 반환한다.
    - 노선에게 구간이 마지막 하나일 경우 제거하면, 상태코드 400을 반환한다.

## 도메인 구조

- 지하철역(station)
    - 이름(name)

- 지하철 노선(line): 지하철 구간의 모음으로 구간에 포함된 지하철역의 연결 정보
    - 노선 이름(name)
    - 노선 색(color)

- 지하철 구간(section)
    - 노선(lindId)
    - 상행 종점(upStationId)
    - 하행 종점(downStationId)
    - 두 종점간의 거리(distance)
