참조 URL
- Vuex
1. https://joshua1988.github.io/web-development/vuejs/vuex-start
2. https://vuex.vuejs.org/kr/

- 뷰 반응성
1. https://kr.vuejs.org/v2/guide/reactivity.html
 
- 서버 사이드 렌더링
1. https://ssr.vuejs.org/

- webpack
1. https://webpack.js.org/plugins/loader-options-plugin/


<br>
<br>

<h2 id="vuex-란">Vuex 란?</h2>
<p>Vue.js 의 <strong>상태관리</strong> 를 위한 패턴이자 라이브러리.
다른 상태관리 패턴이나 라이브러리와 비교했을 때 Vue 의 Reactivity 체계를 효율적으로 활용하여
화면 업데이트가 가능하다는 차이점이 있다.</p>

<h3 id="상태관리-state-management-가-왜-필요한가">상태관리 (State Management) 가 왜 필요한가?</h3>
<p>컴포넌트 기반 프레임워크에서는 화면 구성을 위해 화면 단위를 매우 잘게 쪼개서 컴포넌트로 사용한다. 예를 들면, header, button, list 등의 작은 단위들이 컴포넌트가 되어 한 화면에서 많은 컴포넌트를 사용하게 된다. 이에 따라 <strong>컴포넌트 간의 통신이나 데이터 전달을 좀 더 유기적으로 관리할 필요성이 생긴다.</strong></p>

<p>달리 말해, header -&gt; button, button -&gt; list , button -&gt; footer 등의 <strong>컴포넌트 간 데이터 전달 및 이벤트 통신 등의 여러 컴포넌트의 관계를 한 곳에서 관리하기 쉽게 구조화 하는 것이 State Management</strong>다.</p>

<p>Vue 와 성격이 유사한 프론트엔드 프레임워크인 React 에서는 이미 Redux, Flux 와 같은 상태 라이브러리를 사용하고 있고, Vue 도 Vuex 라는 상태관리 라이브러리를 사용한다.</p>

<h3 id="상태관리로-해결할-수-있는-문제점">상태관리로 해결할 수 있는 문제점?</h3>
<p>상태관리는 중대형 규모의 앱 컴포넌트들을 더 효율적으로 관리하기 위한 기법이다.
일반적으로 앱의 규모가 커지면서 생기는 문제점들은 아래와 같다.</p>

<ol>
  <li>Vue 의 기본 컴포넌트 통신방식인 상위 - 하위 에서 <strong>중간에 거쳐야 할 컴포넌트가 많아지거나</strong></li>
  <li>이를 피하기 위해 Event Bus 를 활용하여 <strong>상하위 관계가 아닌 컴포넌트 간 통신 시 관리가 되지 않는 점</strong></li>
</ol>

<p>이러한 문제점들을 해결하기 위해 모든 데이터 통신 (state) 을 한 곳에서 중앙 집중식으로 관리한다.</p>

<p><img src="https://joshua1988.github.io/images/posts/web/vuejs/vuex-1/vuex-diagram.png" alt="vuex-diagram" /></p>

<h3>주요기능</h3>
<ol>
  <li>State</li>
  <li>Getters</li>
  <li>Mutations</li>
  <li>Actions</li>
  <li>Modules</li>
</ol>

<h2>뷰의 반응성</h2>
<p>뷰의 반응성(Vue Reactivity)은 뷰가 데이터 변화를 감지했을 때 자동으로 화면을 다시 갱신하는 특성</p>

<ol>
    <li>
    <strong>변경 내용을 추적하는 방법</strong>
    <p>Vue 인스턴스에 JavaScript 객체를 data 옵션으로 전달하면 Vue는 모든 속성에 Object.defineProperty를 사용하여 getter/setter로 변환합니다. 이는 Vue가 ES5를 사용할 수 없는 IE8 이하를 지원하지 않는 이유입니다.<br>

getter / setter 는 사용자에게는 보이지 않으나 속성에 액세스 하거나 수정할 때 Vue가 종속성 추적 및 변경 알림을 수행할 수 있습니다. 한가지 주의 사항은 변환된 데이터 객체가 기록될 때 브라우저가 getter / setter 형식을 다르게 처리하므로 친숙한 인터페이스를 사용하기 위해 vue-devtools를 설치하는 것이 좋습니다.</p>
  </li>
  
  <li>
    <strong>비동기 갱신 큐</strong>
    <p> Vue는 DOM 업데이트를 비동기로 합니다. 데이터 변경이 발견 될 때마다 큐를 열고 같은 이벤트 루프에서 발생하는 모든 데이터 변경을 버퍼에 담습니다. 같은 Watcher가 여러 번 발생하면 대기열에서 한 번만 푸시됩니다. 이 버퍼링된 중복의 제거는 불필요한 계산과 DOM 조작을 피하는 데 있어 중요합니다. 그 다음, 이벤트 루프 “tick”에서 Vue는 대기열을 비우고 실제 (이미 중복 제거 된) 작업을 수행합니다.</p>
  </li>
</ol>

<h2>서버 사이드 렌더링 (<> 클라이언트 사이드 렌더링)</h2>

<p>
  클라이언트 사이드 렌더링이란 웹 페이지를 화면에 그릴때 화면을 그리는 동작을 클라이언트(브라우저)에서 수행하는 것을 의미. 서버 사이드 렌더링에서는 별도의 자바스크립트를 이용한 화면 렌더링이 필요하지 않으며 따라서 로딩 속도가 빠르다.<br>
  서버사이드 렌더링의 강점은 검색엔진 최적화(SEO, Search Engin Optimization)입니다. 화면의 내용이 이미 다 그려진 상태로 클라이언트에 넘어오기 때문에 내용의 노출정도가 높아 검색엔진에서 높은 점수를 받을 수 있습니다.
<p>

<h2>Webpack</h2>
<h3>웹팩이란?</h3>
<p>앵귤러 리엑트 뷰에서 모두 권하는 모듈번들러로, 서로 연관이 있는 모듈간의 관계를 해석하여 정적인 자원으로 변환해 주는 변환 도구</p>

<h3>주요 속성</h3>
<ol>
  <li>
   <strong>entry</strong>
   <p>웹팩으로 빌드할 대상 파일을 지정하는 속성</p>
  </li>

  <li>
   <strong>output</strong>
   <p>빌드한 결과물의 위치와 파일이름등 세부옵션을 설정하는 속성</p>
  </li>
  

  <li>
   <strong>loader</strong>
   <p>웹팩으로 빌드할때 html, css, png 파일등을 자바스크립트로 변환하기 위해 필요한 설정을 정의하는 속성입니다</p>
  </li>
  

  <li>
   <strong>plugin</strong>
   <p>웹팩으로 빌드하고 나온 결과물에 대해 추가 기능을 제공하는 속성입니다</p>
  </li>
  

  <li>
   <strong>resolve</strong>
   <p>웹팩으로 빌드할때 해당 파일이 어떻게 해석되는지 정의하는 속성 (ex 로딩 버전, 파일경로 등)</p>
  </li>
 </ol>
