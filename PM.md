# NPM vs YARN



## yarn의 탄생 배경 
<br/>

![yarn](https://ih0.redbubble.net/image.270043317.1488/flat,800x800,070,f.jpg)

- 페이스북은 코드베이스가 커지면서 npm을 사용할 때 일관성, 보안, 성능에 문제를 겪게 되었고 Google, Exponent, Tilde의 개발자들과 함께 2016년에 npm client를 대체할 새로운 패키지 매니저 Yarn을 만들었다. 이미 널리 쓰이고 있는 npm과 비교했을 때, 더 빠르고 안정적이라고 주장했다.

- yarn이 처음 나왔을때 npm이 가지고 있는 다음문제를 해결할 수 있었다
	- `yarn.lock`파일을 생성해 패키지의 디펜던시 유지를 좀 더 안정적으로 할 수 있었다
	- 패키지 다운 속도가 약 2~3배정도 빨랐다(발전된 캐싱처리 / 불필요한 다운로드 감소)
		- 사실상 패키지는 npm registry에서 다운로드 
	- 위와 같은 개선으로 인터넷 연결없이도 캐싱된 패키지 설치 가능

## 뒤이은 npm5 의 등장 
- `yarn`을 의식한 듯 `yarn`이 가지고 있는 특징과 함께 업데이트
- `package-lock.json` 의 생성으로 디펜던시를 보장 
- `--save` default로 사용 (개발자의 편의성을 도모)
- 다운로드 속도 개선 (npm4보다 약 3배 속도 개선)
![npm에서 제시한 속도 개선 이미지](https://cdn-images-1.medium.com/max/2000/0*K1Wb1ERhtAHLRG0m.)

## npm5과 yarn 의 비교 
 * 속도: 일반적으로 `yarn`이 속도면에서 `npm`보다 우수함

	- 같은 패키지를 다운 받았을 때 비교  
  ![속도비교](https://cdn-images-1.medium.com/max/1600/1*lYNSr1oI_PE6umJuOVgxmA.png)
  	- 같은 패키지를 다운 받았을 때 비교 #2 (With Cache & With rock file)
	
  
```sh
# via npm 
Run #1 ================================
added 1065 packages in 17.319s
real0m17.991s
user0m25.921s
sys0m10.794s
Run #2 ================================
added 1065 packages in 17.106s
real0m17.765s
user0m25.680s
sys0m10.824s
Run #3 ================================
added 1065 packages in 17.531s
real0m18.281s
user0m25.949s
sys0m10.757s
```

```sh
# via yarn 
Run #1 ================================
Done in 8.43s.
real0m8.933s
user0m6.986s
sys0m5.994s
Run #2 ================================
Done in 8.37s.
real0m8.868s
user0m6.898s
sys0m6.113s
Run #3 ================================
Done in 8.10s.
real0m8.560s
user0m6.628s
sys0m6.018s
```
 * determinism
  - 자바 스크립트 패키지 관리의 맥락에서 `determinism` package.json과 companion lock 파일이 주어지면 항상 정확히 동일한 node_modules 폴더를 얻는 것으로 정의
  - `determinism`을 보장하는 것은 모두 두 패키지 모두 `lock`파일에 의존
  - `yarn`의 `lock`파일의 형태 

```sh
has-flag@^1.0.0:
version "1.0.0"
resolved "https://registry.yarnpkg.com/has-flag/-/has-flag-1.0.0.tgz#9d9e793165ce017a00f00418c43f942a7b1d11fa"
supports-color@^3.2.3:
version "3.2.3"
resolved "https://registry.yarnpkg.com/supports-color/-/supports-color-3.2.3.tgz#65ac0504b3954171d8a64946b2ae3cbb8a5f54f6"
dependencies:
has-flag "^1.0.0" 
```  
	- `npm`의 `lock` 파일의 형태 
	  
```sh
{
  "name": "react-example",
  "version": "1.0.0",
  "lockfileVersion": 1,
  "dependencies": {
    "has-flag": {
      "version": "1.0.0",
      "resolved": "https://registry.npmjs.org/has-flag/-/has-flag-1.0.0.tgz",
      "integrity": "sha1-nZ55MWXOAXoA8AQYxD+UKnsdEfo="
    },
    "supports-color": {
      "version": "3.2.3",
      "resolved": "https://registry.npmjs.org/supports-color/-/supports-color-3.2.3.tgz",
      "integrity": "sha1-ZawFBLOVQXHYpklGsq48u4pfVPY="
    }
  }
}
}
```

 - `yarn`과 `npm`에서 `determinism`은 알고리즘은 서로 다르고 위 파일처럼 디펜던시를 기술하는 방법도 서로 다르다.
 -  `determinism` 측면에서는 좀 더 밀집하고 견고한 구조로 `lock`파일을 유지 하고 `hoisting`의 정확성을 가지고 있는 있는 `npm`이 더욱 유리하다고 양측 문서에서 설명하고 있다.



## 결론
- 다른 기능을 추가 하지 않는 한, 패키지 다운속도는 `yarn`이 우수하다
- `determinism` 측면에서 좀 더 밀집하고 안정성을 보장하는 `lock`파일을 기술하고 있는 `npm`이 유리하다.
- `npm` 의 문제를 개선하고 발전시킨 `yarn`이 처음에 나왔을 때는 무조건 써야하는 패키지매니저 였지만, `npm@5`가 나온 이후로 사실상 두 패키지매니저의 차이는 커보이지 않는다. 각자의 선호와 팀의 요구사항에 맞게 잘 골라서 쓰면 될 것 같다

## Reference

- [determinism](https://yarnpkg.com/blog/2017/05/31/determinism/)
- [npm-5-yarn-killer](https://medium.com/netscape/npm-5-yarn-killer-ba69737b24d0)
- [does-npm5-deprecate-yarn](https://blog.scottlogic.com/2017/06/06/does-npm5-deprecate-yarn.html)
- [npm5 vs yarn speed](https://blog.oharagroup.net/npm-v5-3-0-vs-yarn-0-27-5-speed-c9d3be07b557)

