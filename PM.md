## yarn
- 페이스북은 코드베이스가 커지면서 npm을 사용할 때 일관성, 보안, 성능에 문제를 겪게 되었고 Google, Exponent, Tilde의 개발자들과 함께 2016년에 npm client를 대체할 새로운 패키지 매니저 Yarn을 만들었다. 이미 널리 쓰이고 있는 npm과 비교했을 때, 더 빠르고 안정적이라고 표방

- yarn이 처음 나왔을때 npm이 가지고 있는 다음문제를 해결 할 수 있었다.
 - yarn,lock파일을 생성해 패키지의 디펜던시 유지를 좀 더 안정적으로 할 수 있었다
 - 패키지 다운 속도가 약 2~3배정도 빨랐다( 발전된 캐싱처리 / 불필요한 다운로드 감소)
 - 위와 같은 개선으로 인터넷 연결없이도 캐싱된 패키지 설치 가능

## npm5 의 등장 
 - package-lock.json 의 생성으로 디펜던시 보장 
 - 다운로드 속도 개선 (npm4보다 약 3배 속도 개선)
 - `--save` default로 사용 (개발자의 편의성을 도모)

## npm5 vs yarn 
 - [비교글1](https://medium.com/netscape/npm-5-yarn-killer-ba69737b24d0)
 - [비교글2](https://blog.scottlogic.com/2017/06/06/does-npm5-deprecate-yarn.html)
 - [속도 비교글](https://blog.oharagroup.net/npm-v5-3-0-vs-yarn-0-27-5-speed-c9d3be07b557)


## 결론
 - 캐싱되어 있을때 `yarn`이 속도면에서 우수하다
 - 디페던시의 안정성은 `npm`에서 더 보장된다
 - yarn에서 패키지 호이스팅의 문제가 있음 
 - 더욱 자세하고 밀집한 `package-lock.json`파일
  - 호이스팅: A의 디펜던시와 B의 디펜던시가 겹칠때 한개만 설치
  - [determinism](https://yarnpkg.com/blog/2017/05/31/determinism/)

