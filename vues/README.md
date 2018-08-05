참조 URL
1. https://joshua1988.github.io/web-development/vuejs/vuex-start
2. https://vuex.vuejs.org/kr/


<h2 id="vuex-란">Vuex 란?</h2>
<p>Vue.js 의 <strong>상태관리</strong> 를 위한 패턴이자 라이브러리.
다른 상태관리 패턴이나 라이브러리와 비교했을 때 Vue 의 Reactivity 체계를 효율적으로 활용하여
화면 업데이트가 가능하다는 차이점이 있다.</p>

<h2 id="상태관리-state-management-가-왜-필요한가">상태관리 (State Management) 가 왜 필요한가?</h2>
<p>컴포넌트 기반 프레임워크에서는 화면 구성을 위해 화면 단위를 매우 잘게 쪼개서 컴포넌트로 사용한다. 예를 들면, header, button, list 등의 작은 단위들이 컴포넌트가 되어 한 화면에서 많은 컴포넌트를 사용하게 된다. 이에 따라 <strong>컴포넌트 간의 통신이나 데이터 전달을 좀 더 유기적으로 관리할 필요성이 생긴다.</strong></p>
