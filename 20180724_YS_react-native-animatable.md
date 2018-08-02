# react-native-animatable

Declarative transitions and animations for React Native

 - react-native의 복잡한 `Animated`를 복잡한 계산없이 declarative한 방법으로 사용 할수 있게 해주는 라이브러리


## Declarative Usage (example)

```js
<Animatable.Text animation="slideInDown" iterationCount={5} direction="alternate">Up and down you go</Animatable.Text>
<Animatable.Text animation="pulse" easing="ease-out" iterationCount="infinite" style={{ textAlign: 'center' }}>❤️</Animatable.Text>
```
![example view](https://cloud.githubusercontent.com/assets/378279/10716023/9f4a6670-7b00-11e5-944c-d52a1dcf0884.gif)

## Compare to Original API 

 - Spinning Text using `Animated`

 ```js
 constructor(props) {
    super(props);
    this.spinValue = new Animated.Value(0);
  }

  componentDidMount() {
    this.spin();
  }

  spin() {
    this.spinValue.setValue(0);
    Animated.timing(this.spinValue, {
      toValue: 1,
      duration: 4000,
      easing: Easing.linear,
    }).start(() => this.spin());
  }

  render() {
    const spin = this.spinValue.interpolate({
      inputRange: [0, 1],
      outputRange: ['0deg', '360deg'],
    });

    return (
      <Container>
        <Animated.Text style={{ transform: [{ rotate: spin }] }}>Spin Text</Animated.Text>
      </Container>
    );
  }
 
 ```
 
 - Spinning Text using `react-native-animatable`

	```js
	 import * as Animatable from 'react-native-animatable';
	
     <Animatable.Text
       animation="rotate"
       easing="linear"
       iterationCount="infinite"
       duration={4000}
     >
       Spinning Text!
     </Animatable.Text>
	```
	
![sample image](https://raw.githubusercontent.com/heyman333/information/master/images/ezgif.com-video-to-gif-4.gif)


## Advantage

 - 다른 뷰와 특별한 인터랙션이 필요없는 애니메이션 같은경우 복잡하고 긴 코드 없이 선언적으로 애니메이션 뷰를 만들 수 있다.
 - 결과적으로 적절한 라이브러리의 사용은 시간과 코드 사용량 감소

## Reference
 - [react-native-animatable](https://github.com/oblador/react-native-animatable)
 - ![example view](https://user-images.githubusercontent.com/378279/36341974-f697e5d8-13f6-11e8-8e2a-21d8c2a4b340.gif)
