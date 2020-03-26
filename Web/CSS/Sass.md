<h2>Sass란</h2>

Sass(Syntactically Awesome StyleSheets)는 CSS pre-processor로서 CSS의 한계와 단점을 보완하여 보다 가독성이 높고 코드의 재사용에 유리한 CSS를 생성하기 위한 CSS의 확장(extension)이다.

CSS의 간결한 문법은 배우기 쉬우며 명확하여 프로젝트 초기에는 문제가 없이 보이지만 프로젝트의 규모가 커지고 수정이 빈번히 발생함에 따라 쉽게 지저분해지고 유지보수도 유지보수도 어려워지는 단점도 가지고 있다.

CSS를 보완하기 위해 Sass는 다음과 같은 기능과 도구들을 제공한다.

- 변수의 사용
- 조건문과 반복문
- Import
- Nesting
- Mixin
- Extend/Inheritance

Sass는 다음과 같은 장점이 있다.

- CSS보다 심플한 표기법으로 CSS를 구조화하여 표현할 수 있다.
- 스킬 레벨이 다른 팀원들과의 작업 시 발생할 수 있는 구문의 수준 차이를 평준화할 수 있다.
- CSS에는 존재하지 않는 Mixin 등의 강력한 기능을 활용하여 CSS 유지보수 편의성을 큰 폭으로 향상시킬 수 있다.

<h2>설치</h2>

브라우저는 Sass의 문법을 알지 못하기 때문에 Sass(.scss) 파일을 css 파일로 컴파일(트랜스파일링)하여야 한다. 따라서 Sass 환경의 설치가 필요하다.

Sass는 2006년 Ruby로 처음 개발되었고 이후 다양한 포팅 버전이 등장했다. Libsass도 Ruby Sass를 C++로 포팅한 버전이다. Ruby 환경에서 개발이 진행된다면 Ruby Sass를 선택하고, Node.js 환경에서 개발이 진행된다면 LibSass를 사용하는 것이 좋다.


<h2>참고 사이트</h2>

- https://poiemaweb.com/sass-basics
- https://ko.wikipedia.org/wiki/Sass_(%EC%8A%A4%ED%83%80%EC%9D%BC%EC%8B%9C%ED%8A%B8_%EC%96%B8%EC%96%B4)
