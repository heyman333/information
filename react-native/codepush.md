### AppCenter 확인방법

1. 마이크로 소프트 앱센터 접속

2. App선택 후 Distribute -> CodePush 클릭

3. 코드푸쉬 이력 확인 가능

### 릴리즈 방법

1. `npm install -g appcenter-cli`

2. `appcenter codepush release-react -a <username>/<appname> -d Production -m --description "UI 수정"`

   - `-m`: 업데이트 강제

### 릴리즈 키 리스트 확인 방법

- `appcenter codepush deployment list -a <username>/<appname> --displayKeys`

### 주의점 (개인적인 생각)

- 코드푸시의 남발은 사용자로 부터 붎필요한 앱 업데이트를 받도록 강요한다. 따라서 정말 급한 hotfix가 아니라면 코드푸쉬 보다는 정식으로 앱 릴리즈(네이티브 배포)를 통해 업데이트 하는 것이 바람직해 보인다. 
- 앱 번들 버전과 현재 올라가 있는 코드푸쉬 버전과 상응하는 것이 없다면 기본적으로 내장된 js번들을 로드 하기 때문에 불필요한 소스 다운로드를 막을 수 있다.

### Reference

- https://docs.microsoft.com/en-us/appcenter/distribution/codepush/react-native
