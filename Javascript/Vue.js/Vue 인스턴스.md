<h1>Vue 인스턴스</h1>

<h3>1. Vue 인스턴스란?</h3>

- 생성된 Vue 오브젝트 하나
- Vue 앱을 시작하기 위해 필수적이며, 앱의 진입점이 됨

<h3>2. Vue 인스턴스 만들기</h3>

- var vm = new Vue({
          // 옵션
  })
- Vue 인스턴스를 인스턴스화 할 때는 데이터, 템플릿, 마운트할 엘리먼트, 메서드, 라이프사이클 콜백 등의 옵션을 포함할 수 있는 options 객체를 전달 해야한다. <br>
new Vue({ <br>
  el: '#app', <br>
  template: '', <br>
  data: {}, <br>
  props: [], <br>
  methods: {}, <br>
  computed: {}, <br>
  watch: {} <br>
});

<h4> 인스턴스 옵션 </h4>

- <strong>el (string | HTMLElement)</strong> : 대상이 되는 html element 또는 css selector (vm.$el) <br> 

- <strong>template (string)</strong> : Vue 인스턴스의 마크업으로 사용할 문자열 템플릿 <br>
- <strong>data (Object | Function)</strong> : 화면을 그리는데 사용하는 data를 반환하는 함수 또는 data 객체. <br>Vue 인스턴스가 아닌 하위 컴포넌트에서 사용될 때는 반드시 함수형이여야 한다. (vm.$data) data 객체의 속성들이 변경 되면(함수일 경우 리턴하는 데이터 객체의 속성), 화면이 자동으로 갱신된다. <br>
- <strong>props (Array<string> | Object)</strong> : 부모 컴포넌트로부터 전달 받은 property들의 Array 혹은 Object. <br>
- <strong>methods ([key:string]: Funection)</strong> : Vue 인스턴스에서 사용되는 메서드. this 컨텍스트를 Vue 인스턴스에 바인딩 합니다. 화면을 표현하는데 사용하는 모든 메서드들이 모여 있는 곳이다. <br>
- <strong>computed ([key:string]: Function | {get:Function, set:Function })</strong> : 계산된 속성. getter와 setter는 자동으로 this 컨텍스트를 Vue 인스턴스에 바인딩 한다. data를 미리 계산한 값들을 나타내는 함수들을 모아둔 객체. setter를 만들지 않았다면 기본적으로 getter 기능만 제공한다.<br>
- <strong>watch ([key:string]:string | Function | Object | Array)</strong> : 감시된 속성. Vue 인스턴스에 데이터가 변경되는 시점에 호출. watch는 data와 한쌍을 이루게 된다. 즉, data에 표현된 key와 watch에 표현된 key의 이름은 동일해야 한다. data의 value값이 변경 되면, watch의 key의 value에 할당된 콜백이 실행된다. <br>
