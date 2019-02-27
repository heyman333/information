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

### 주의점

1.  production에 코드푸쉬를 하기 전에 반드시 staging에서 코드푸쉬 적용 테스트 후 staging -> production으로 promote 할 것

### Reference

- https://docs.microsoft.com/en-us/appcenter/distribution/codepush/react-native
