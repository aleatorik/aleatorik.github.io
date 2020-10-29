---
layout: post
title: 2차 팀 프로젝트 후기(feat. StockX)
category: Etc
tags: Etc
---

<br>

# 프로젝트 소개:

> 스니커즈를 중심으로 한 온라인 경매 마켓 플레이스, StockX 웹사이트 클론 프로젝트

- 개발 기간 : 2020년 8월 31일 ~ 2020년 9월 11일(12일)<br>
- 개발 인원 : Front-end 4명, Back-end 3명<br>
- Github 주소 : [프론트엔드](https://github.com/aleatorik/westock)

<br>

# 프로젝트 목적:

1. **Progress**: Scrum 진행 방식에 대해 이해하고 적용해며 프로젝트를 진행한다.
2. **Communication**: 협업 프로젝트를 통해 프론트 간의, 또한 백엔드와의 의사소통에서 필요한 내용들을 경험한다. 매일 아침 스탠드업 미팅을 가진다.
3. **React**: 함수형 React 컴포넌트, Hook을 사용하여 데이터 통신, 컴포넌트 분리 및 관리, 컴포넌트 간 데이터 바인딩을 적용해 본다.
4. **Styled-Components**: js 파일 안에서 컴포넌트의 스타일을 지정하고, 컴포넌트의 상태를 props로 받아 스타일 적용을 다르게 할 수 있다.
5. **Network**: fetch나 axios를 사용하여 서버 api에 요청하고 응답받은 데이터를 화면에 보여준다.

<br>

# 데모 영상

<iframe width="100%" height="400px" src="https://www.youtube.com/embed/6raMXpYz_oU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

# 구현 페이지 및 기능

## 1. 기술 스택

- HTML, CSS, JS(es6+)
- React(CRA 세팅), Styled-Components(SCSS)

## 2. 협업 툴

- Git
- Slack
- Trello
- Google Meet
- Zoom

## 3. 구현 기능

_(내가 맡은 파트는 BOLD 처리)_

- 네비게이션 바
- **로그인 및 회원가입**
  - **카카오 소셜로그인**
  - **JWT 방식**
- 메인 페이지
- 상세 페이지
- 상품 리스트 페이지
- **사용자 개인 페이지**
  - **fetch를 통한 데이터 통신 네트워크로 유저 상품입찰내역 렌더링**

---

1.  카카오 소셜 로그인
<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">function</span>&nbsp;SocialLogin()&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">const</span>&nbsp;<span style="color:#066de2">history</span>&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>&nbsp;useHistory();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">return</span>&nbsp;(</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">&lt;</span>SocialLoginWrapper<span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">&lt;</span>Button&nbsp;onClick<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>{()&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span><span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span>&nbsp;kakaoApi(setToken,&nbsp;<span style="color:#066de2">history</span>)}<span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">&lt;</span>SocialIconKakao&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">/</span><span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Continue&nbsp;<span style="color:#a71d5d">with</span>&nbsp;KakaoTalk</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">&lt;</span><span style="color:#ff3399"></span><span style="color:#a71d5d">/</span>Button<span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">&lt;</span><span style="color:#ff3399"></span><span style="color:#a71d5d">/</span>SocialLoginWrapper<span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;);</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#a71d5d">const</span>&nbsp;setToken&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>&nbsp;(access_token,&nbsp;sns,&nbsp;<span style="color:#066de2">history</span>)&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span><span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span>&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#066de2">console</span>.log(access_token,&nbsp;sns);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;fetch(`${API_ADDRESS}<span style="color:#ff3399"></span><span style="color:#a71d5d">/</span>users<span style="color:#ff3399"></span><span style="color:#a71d5d">/</span>sign<span style="color:#ff3399"></span><span style="color:#a71d5d">-</span><span style="color:#a71d5d">in</span><span style="color:#a71d5d">/</span>${sns}`,&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;headers:&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Authorization:&nbsp;access_token,</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;},</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;})</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;.then((res)&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span><span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span>&nbsp;res.json())</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;.then((res)&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span><span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span>&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#066de2">console</span>.log(res.ACCESS_TOKEN);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;localStorage.setItem(<span style="color:#63a35c">"ACCESS_TOKEN"</span>,&nbsp;res.ACCESS_TOKEN);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#066de2">alert</span>(<span style="color:#63a35c">"로그인에&nbsp;성공하였습니다"</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#066de2">history</span>.push(<span style="color:#63a35c">"/"</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;});</div><div style="padding:0 6px; white-space:pre; line-height:130%">};</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
