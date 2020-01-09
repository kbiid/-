<h1>Vue 인스턴스</h1>

1. Vue 인스턴스란?
- 생성된 Vue 오브젝트 하나
- Vue 앱을 시작하기 위해 필수적이며, 앱의 진입점이 됨

2. Vue 인스턴스 만들기
- var vm = new Vue({
          // 옵션
  })
- Vue 인스턴스를 인스턴스화 할 때는 데이터, 템플릿, 마운트할 엘리먼트, 메서드, 라이프사이클 콜백 등의 옵션을 포함할 수 있는 options 객체를 전달 해야한다.
new Vue({
  el: '#app',
  template: '',
  data: {},
  props: [],
  methods: {},
  computed: {},
  watch: {}
});

<ul>
  <li>el (string | HTMLElement) : 대상이 되는 html element 또는 css selector (vm.$el)</li>
  <li>template (string) : Vue 인스턴스의 마크업으로 사용할 문자열 템플릿</li>
  <li>data (Object | Function) : 화면을 그리는데 사용하는 data를 반환하는 함수 또는 data 객체 (vm.$data)</li>
  <li>props (Array<string> | Object) : 부모 컴포넌트로부터 전달 받은 property들의 Array 혹은 Object</li>
  <li>methods ([key:string]: Funection) : Vue 인스턴스에서 사용되는 메서드. this 컨텍스트를 Vue 인스턴스에 바인딩 합니다.</li>
  <li>computed ([key:string]: Function | {get:Function, set:Function }) : 계산된 속성. getter와 setter는 자동으로 this 컨텍스트를 Vue 인스턴스에 바인딩 한다.</li>
  <li>watch ([key:string]:string | Function | Object | Array) : 감시된 속성. Vue 인스턴스에 데이터가 변경되는 시점에 호출</li>
</ul>
