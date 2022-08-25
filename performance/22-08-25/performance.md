# 성능측정
일자: 22.08.25. 목 오후 10시

## 대상

* [subway-running map 메인페이지](https://mand2-infra-subway.kro.kr/)
* [subway-running map 경로검색페이지](https://mand2-infra-subway.kro.kr/path)
* [서울 교통공사](http://www.seoulmetro.co.kr/kr/cyberStation.do)
* [네이버 지도](https://m.map.naver.com/subway/subwayLine.naver?region=1000)
* [카카오 맵](https://m.map.kakao.com/)

---

## 웹 성능 측정 지표

### 용어 정리

- `FCP` First Contentful Paint   
  콘텐츠가 포함된 첫 페인트는 첫 번째 텍스트 또는 이미지가 표시되는 시간을 나타냅니다.
- `TTI` Time to Interactive   
  사용할 수 있을 때까지 걸리는 시간은 완전히 페이지와 상호작용할 수 있게 될 때까지 걸리는 시간입니다.
- `SI` Speed Index   
  속도 색인은 페이지 콘텐츠가 얼마나 빨리 표시되는지 보여줍니다.
- `TBT` Total Blocking Tim   
  FCP와 상호작용 시간 사이의 모든 시간의 합으로 작업 지속 시간이 50ms를 넘으면 밀리초 단위로 표현됩니다.
- `LCP` Largest Contentful Paint   
  콘텐츠가 포함된 최대 페인트는 최대 텍스트 또는 이미지가 표시되는 시간을 나타냅니다.
- `CLS` Cumulative Layout Shift   
  누적 레이아웃 변경은 표시 영역 안에 보이는 요소의 이동을 측정합니다.

<br>

## 성능 측정 결과 
성능 측정 페이지: [WebPageTest](https://www.webpagetest.org/), 
[PageSpeed](https://developers.google.com/speed/pagespeed/insights/)


<details>
<summary>WebPageTest 보기 &nbsp;👀✨</summary>

#### Desktop, Chrome v104, 1920 * 1080, Cable

| site                                                                            | First Byte | Start Render | FCP     | SI      | LCP     | CLS  | TBT        | DC Time | DC Requests | Total Bytes |
|:--------------------------------------------------------------------------------|:-----------|:-------------|:--------|:--------|:--------|:-----|:-----------|:--------|:------------|:------------|
| [subway-running map `/`](./img/webpagetest/subway_landing_page_pc_details.png)  | .156 s     | 4.700 s      | 4.676 s | 4.703 s | 4.703 s | .001 | ≥ .000 s  | 5.153 s | 19          | 2,493 KB    |
| [subway-running map `/path`](./img/webpagetest/subway_path_page_pc_details.png) | .157 s     | 4.800 s      | 4.749 s | 4.808 s | 4.782 s | 0    | ≥ .005 s  | 5.582 s | 13          | 2,746 KB    |
| [서울교통공사](./img/webpagetest/seoul-metro_landing_page_pc_details.png)           | 1.484 s    | 3.200 s      | 3.227 s | 4.111 s | 5.397 s | 0    | ≥ 1.236 s | 5.353 s | 87          | 1,373 KB    |
| [네이버 지도(지하철)](./img/webpagetest/naver_landing_page_pc_details.png)           | .200 s     | 0.900 s      | .676 s  | 2.411 s | 2.800 s | .026 | ≥ .019 s  | 1.189 s | 15          | 779 KB      |
| [카카오맵](./img/webpagetest/kakao_landing_page_pc_details.png)                    | .580 s     | 1.500 s      | 1.495 s | 2.493 s | 2.914 s | .001 | .008 s     | 4.212 s | 41          | 1,228 KB    |




</details>

<br>

<details>
<summary>PageSpeed Insights 보기 &nbsp;👀✨</summary>

### desktop 

| Site                                                                    | SCORE | FCP   | TTI   | SI    | TBT    | LCP   | CLS   |
|:------------------------------------------------------------------------|:------|:------|:------|:------|:-------|:------|:------|
| [subway-running map (`/`)](./img/pagespeed/subway_landing_page_pc.png)  | 67    | 2.7 s | 2.8 s | 2.7 s | 50 ms  | 2.8 s | 0.004 |
| [subway-running map (`/path`)](./img/pagespeed/subway_path_page_pc.png) | 65    | 2.9 s | 3.1 s | 2.9 s | 0 ms   | 2.9 s | 0     |
| [서울교통공사](./img/pagespeed/seoul-metro_landing_page_pc.png)             | 55    | 1.5 s | 2.1 s | 3.5 s | 290 ms | 3.7 s | 0     |
| [네이버 지도(지하철)](./img/pagespeed/naver_landing_page_pc.png)             | 88    | 0.5 s | 0.5 s | 2.7 s | 0 ms   | 1.6 s | 0.006 |
| [카카오맵](./img/pagespeed/kakao_landing_page_pc.png)                      | 91    | 0.5 s | 0.7 s | 2.5 s | 0 ms   | 1.3 s | 0.003 |
   

### mobile

| Site                                                                        | SCORE | FCP    | TTI    | SI     | TBT    | LCP    | CLS   |
|:----------------------------------------------------------------------------|:------|:-------|:-------|:-------|:-------|:-------|:------|
| [subway-running map (`/`)](./img/pagespeed/subway_landing_page_mobile.png)  | 34    | 14.8 s | 15.4 s | 14.8 s | 480 ms | 15.3 s | 0.042 |
| [subway-running map (`/path`)](./img/pagespeed/subway_path_page_mobile.png) | 40    | 16.4 s | 17.1 s | 16.4 s | 260 ms | 16.4 s | 0.004 |
| [서울교통공사](./img/pagespeed/seoul-metro_landing_page_mobile.png)            | 31    | 6.5 s  | 8.6 s  | 11.9 s | 830 ms | 7.0 s  | 0     |
| [네이버 지도(지하철)](./img/pagespeed/naver_landing_page_mobile.png)            | 50    | 2.4 s  | 6.6 s  | 7.0 s  | 450 ms | 8.4 s  | 0.03  |
| [카카오맵](./img/pagespeed/kakao_landing_page_mobile.png)                     | 67    | 1.7 s  | 4.3 s  | 6.6 s  | 70 ms  | 7.5 s  | 0.005 |
   
</details>

<br>

---

## 결론


### 웹 성능 예산 작성 기준

시간 + 규칙 기준으로 설정한다.
정량규칙은 backend 에서 설정하는 기준이 아니라고 판단했음.

기준값 도출 과정 :  
    서울교통공사는 생각보다 웹 성능 예산이 카카오/네이버에 비해 좋지 않고, 나의 subway-running map 과 비슷하다고 생각하여, 기준을 카카오/네이버로 잡음.  
    **카카오와 네이버의 평균값에 1.2 를 곱한 값**으로 웹 성능 예산을 작성함. (경쟁사 대비 20% 내로 차이가 나와야 함)

**page-speed 기준 desktop**

| site    | Score | FCP | TTI  | SI   | TBT  | LCP  | CLS    |
|---------|-------|-----|------|------|------|------|--------|
| 네이버지도   | 88    | 0.5 | 0.5  | 2.7  | 0 ms | 1.6  | 0.006  |
| 카카오맵    | 91    | 0.5 | 0.7  | 2.5  | 0 ms | 1.3  | 0.003  |
| 평균값     | 89.5  | 0.5 | 0.6  | 2.6  | 0 ms | 1.45 | 0.0045 |
| 평균 *1.2 |       | 0.6 | 0.72 | 3.12 | 0 ms | 1.74 | 0.0054 |

| site       | Score | 기준  | AS-IS  | TO-BE       |
|------------|-------|-----|--------|-------------|
| 메인페이지 /    | > 80  | LCP | 2.8 s  | 1.7 s       |
| 경로검색 /path | > 80  | TTI | 2.24 s | 0.7 ~ 1.0 s |

- 사용자에게 컨텐츠가 빠르게 노출되는 게 중요할 때 : `LCP` ( 메인페이지 ) : 1.7 s
- 사용자가 관련 링크를 빠르게 클릭하는 것이 중요할 때 : `TTI` (경로 찾는 페이지) :  0.7 s ~ 1 s

<br>

**web-page test 기준 desktop**

| site        | First Byte | Start Render | FCP     | SI      | LCP     | CLS    | TBT      | DC Time | DC Requests | Total Bytes |
|-------------|------------|--------------|---------|---------|---------|--------|----------|---------|-------------|-------------|
| 네이버 지도(지하철) | .200 s     | 0.900 s      | .676 s  | 2.411 s | 2.800 s | 0.026  | ≥ .019 s | 1.189 s | 15          | 779 KB      |
| 카카오맵        | .580 s     | 1.500 s      | 1.495 s | 2.493 s | 2.914 s | 0.001  | .008 s   | 4.212 s | 41          | 1,228 KB    |
| 네+카 평균      | 0.390      | 1.20         | 1.0855  | 2.452   | 2.857   | 0.0135 | 0.0135   | 2.7005  | 28          | 1003.5 KB   |
| 평균 *1.2     | 0.468      | 1.44         | 1.3026  | 2.9424  | 3.4284  | 0.0162 | 0.0162   | 3.2406  | 33.6        | 1204.2 KB   |

|            | 기준           | AS-IS   | TO-BE        |
|------------|--------------|---------|--------------|
| 메인페이지 /    | LCP          | 4.703 s | 3.4284 s     |
| 경로검색 /path | Start Render | 4.800 s | 1.44 ~ 1.8 s |

- 사용자에게 컨텐츠가 빠르게 노출되는 게 중요할 때 : `LCP` ( 메인페이지 ) : 3.43 s
- 사용자가 관련 링크를 빠르게 클릭하는 것이 중요할 때 : `Start Render` (경로 찾는 페이지) :  1.44 ~ 1.8 s
  (기존 Start Render  값이 너무 커서 경쟁사 대비 50% 까지 가능하도록 설정함)


**서버 응답시간**

개발자도구에서 Network_Timing_Request/Response_Waiting for server response 를 기준으로 측정.  
캐시 비우기 및 강력고침(개발자 도구 창이 있는 상태에서만 가능)으로 응답시간 확인.
서버 응답 시간은 200 ms 미만으로 줄여야 한다. (출처: [google Page Speed Tools](https://developers.google.com/speed/docs/insights/Server?hl=ko) )

> 서버 응답 시간 `AS-IS`  
> - [메인페이지]((./img/server-response/landing-page-pc.png)) : 7.72 ms  
> - [경로검색]((./img/server-response/path-page-pc.png)) : 63.22 ms

