---
layout: post
title:  "JSX & ES6 공부하기"
date:   2016-09-02
excerpt: "Studying JSX & ES6"
tag:
- JavaScript
- ES6
- JSX
comments: true
---

JSX & ES6 간단 정리
=======

**[React 공식 홈페이지](https://facebook.github.io/react/)**

들어가기에 앞서 JSX를 굳이 하는 이유는 JSX를 썼을 때 개발하기 수월하고(러닝 커브가 있을지라도) 많은 예제들이 JSX를 사용하기에 저도 굳이 한번 배워보고자 합니다.

## 1. JSX 정리

### JSX 개념

**JSX**란?
JavaScript + XML 의 합성으로 JSX 라는 이름이 생겼다고 합니다.
기존의 XML을 허용하기 위해서 사용하는 JavaScript의 확장 문법입니다.
JSX는 단순히 XML을 허용만 하는게 아니라, JavaScript의 대한 추가적인 기능도 제공합니다. 
사용법은 아래와 같습니다.
```
// JSX가 없을 때는 이렇게
React.createElement('a', {href: 'https://leop0ld.github.io/posts/study-jsx-and-es6/'}, 'JSX & ES6 간단 정리')
// JSX를 사용했을 때는 이렇게!
<a href="https://leop0ld.github.io/posts/study-jsx-and-es6/">JSX & ES6 간단 정리</a>
```

**[JSX와 HTML과의 차이점](https://facebook.github.io/react/docs/jsx-gotchas.html)** 링크 참조

### JSX 특징

1. JSX의 장점
 - **빠르다**. 컴파일링 되면서 최적화가 되기 때문에 빠르다
 - **익숙하다**. XML이나 HTML에 익숙한 사람들도 JSX 금방 익힐 수 있습니다.
 - **의미를 잘 나타낼 수 있다**. JavaScript 코드를 마크업 형태로 만들어서 의미를 잘 드러낼 수 있습니다.
 - **시각화가 잘된다**. 코드를 더욱 간결하고 읽기 쉽게 만들어준다.
 - **추상화 할 수 있다**. 서로 다른 JavaScript를 사용해도 같은 JSX를 지원하게 할 수 있다. JSX 트랜스파일러를 이용해서 마크업 -> JS 과정을 추상화 할 수 있어서 가능한 일입니다.

2. Nested Elements(감싸진 요소)

```html
<!-- Error -->
var HelloReact = React.createClass({
    render () {
        return (
		    <h1>Hello, React</h1>
		    <p>UI Library</p>
		);
	}
});
```

이렇게 작성하면 Error가 납니다.
Nested Elements, 즉 감싸진 요소들.
필수적으로 container element 안에 적어줘야 합니다.

```html
<!-- Correct -->
var HelloReact = React.createClass({
    render () {
      return (
    	    <div>
			    <h1>Hello, React</h1>
			    <p>UI Library</p>
		    </div>
		);
	}
});
```

이렇게 작성해주면 됩니다.
한번 감싸줘야 잘 알아듣습니다.


3. JavaScript Expression(자바스크립트 표현)

```html
var HelloReact = React.createClass({
	render () {
		let description = 'Welcome, Leop0ld!';
		return (
			<div>
				<h1>Hello, Leop0ld!</h1>
				<p>{description}</p>
			</div>
		);
	}
});
```

description 이라는 'Welcome, Leop0ld' 문자열을 가진 변수를 생성하고, JSX 내부에서는 {}(중괄호)로 감싸주면 그 값을 사용할 수 있습니다.

또한 JSX 내부에서는 if ~ else 구문이 사용이 불가능합니다.

```html
var HelloReact = React.createClass({
	render () {
		return (
			<div>
				<h1>Hello, Leop0ld!</h1>
				<p>{1 != 2 ? 'Leop0ld' : 'False'}</p>
			</div>
		);
	}
});
```

따라서 위와 같이 삼항연산자 를 사용합니다.
결과는 조건문이 참이면 :(콜론)을 기준으로 왼쪽, 거짓이면 오른쪽이 출력됩니다.

4. Inline Style(인라인 스타일)

key가 camelCase인 json 형식의 변수가 사용됩니다.(Python에서는 dictionary 형태)

```html
var HelloReact = React.createClass({
	render () {
		let description = 'Welcome, Leop0ld!';

		let leoStyle = {
			color: '#fff',
			backgroundColor: '#000',
			border: '10px solid pink',
			borderRadius: '10px'
		}
		return (
			<div>
				<h1 style={leoStyle}>Hello, Leop0ld!</h1>
				<p>{1 != 2 ? 'Leop0ld' : 'False'}</p>
			</div>
		);
	}
});
```

요렇게 -(대시) 를 사용하지 않고, camelCase로 적어서 style을 줄 수 있습니다. 물론 Inline Style로 들어갑니다!

5. Comment(주석)

6. Naming Convention(이름 규칙)


7. [React 공식 홈페이지](https://facebook.github.io/react/)
 - [링크](https://facebook.github.io/react/docs/displaying-data.html)에 JSX 부분 나와 있습니다. 개쩝니다. 영어 된다면 꼭 봅시다.

### JSX 문법

```html
var HelloReact = React.createClass({
    render () {
        return (
		    <div>
			    Hello, <a href="https://facebook.github.io/react/">React</a>
		    </div>
	    );
	}
});
```
return 함수의 인자 부분에 들어가있는 것이 바로 JSX입니다.
겉보기에는 HTML 같아보이지만 까고보면 JSX입니다.
(저런 것들을 Native JS로 변환시켜줍니다.)

**Addition - 확장자!**

JSX 파일의 확장자의 경우에 요즘은 .js 를 사용하는 추세로 전환되어 가고 있다고 합니다. 친구네 회사같은 경우에는 아직 .jsx를 사용하고 있는 회사도 있다고 합니다.

다양하게 다루고자 하면 너무 다양하게 다룰 수 있는 부분이라서 후에 진행하면서 추가할 것이 있다면 추가하도록 하겠습니다.

## 2. ES6 정리

### ES6 개념

### ES6 특징

### ES6 문법