<h1>Apache POI</h1>

<h2>정의</h2>

- 아파치 POI(Apache POI)는 아파치 소프트웨어 재단에서 만든 라이브러리로서 마이크로소프트 오피스 파일 포맷을 순수 자바 언어로서 읽고 쓰는 기능을 제공한다.

- 주로 워드, 엑셀, 파워포인트와 파일을 지원하며 최근의 오피스 포맷인 Office Open XML File Formats(OOXML, *.docs, *.xlsx, *.pptx)이나 아웃룩, 비지오, 퍼블리셔 등으로 지원 파일 포맷을 늘려가고 있다.

<h2>아키텍처</h2>

- POIFS(Prro Obfusation Implementation File System) : OLE 2 Compound document 파일 포맷을 읽고 쓰는 컴포넌트
- HSSF(Horrible SpreadSheet Format) : 엑셀 파일 포맷. 97부터 지원
- XSSF(XML SpreadSheet Format) : 엑셀 2007부터 지원하는 포맷인 *.xlsx 파일
- HPSF(Horrible Property Set Format) : 오피스 파일의 문서요약 정보를 읽는데 사용
- HWPF(Horrible Word Processor Format) : 워드 97(*.doc). 아직 초기단계
- HSLF(Horrible Slid Layout Format) : 파워포인트
- HDGF(Horrible DiaGram Format) : 비지오 파일
- HPBF(Horrible PuBlisher Format) : 퍼블리셔 파일
- HSMF(Horrible Stupid Mail Format) : *.msg파일
- DDF(Dreadful Drawing Format) : 오피스에서 사용되는 이미지 파일
* HSSF 컴포넌트가 가장 안정적이고 많은 기능을 지원


<h2>참고 사이트</h2>
- https://sarc.io/index.php/development/840-apache-poi
- https://ko.wikipedia.org/wiki/%EC%95%84%ED%8C%8C%EC%B9%98_POI
