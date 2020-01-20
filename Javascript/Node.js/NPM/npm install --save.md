<h2>--save</h2>

- NPM이란 Node Package Manager의 약자이다.
- 보통 Node.js 프로젝트의 의존성을 관리하기 위해 npm init 명령어를 이용하며 package.json 파일을 프로젝트 폴더 안에 생성한다. 그리고 npm install을 통해 받은 모듈을 의존성에 추가하기 위해 'npm install 모듈명 --save'옵션을 사용하는데, --save 옵션을 사용하지 않아도 package.json의 dependency 항목에 모듈이 추가된다.
- 즉, package.json 파일이 존재하는 상태에서 'npm install 모듈명'만 입력하면, 설치된 모듈은 자동으로 dependency 항목에 추가된다.
- npm 문서 : npm install saves any specified packages into dependencies by default.

<h2>--save 옵션</h2>

- -P, --save-prod : package.json의 dependencies에 패키지를 등록한다. (default)
- -D, --save-dev : package.json의 denDependencies에 패키지를 등록한다.
- -O, --save-optional: package.json의 optionalDependencies에 패키지를 등록한다.
- --no-save: dependencies에 패키지를 등록하지 않는다.
