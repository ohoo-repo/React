---
title: 폼
seoTitle: 폼 | React | ohoo
seoDescription: description for search engines
isFree: true
---


HTML 폼 엘리먼트는 리액트의 다른 DOM 엘리먼트들과 약간 다르게 작동합니다. 왜냐하면 폼 엘리먼트는 몇몇 내부 상태(state)를 갖기 때문입니다. 예를 들면 일반적인 HTML에서 폼은 하나의 이름(name)을 받아들입니다.
```
<form>
  <label>
    Name:
    <input type="text" name="name" />
  </label>
  <input type="submit" value="Submit" />
</form>
```

이 폼은 사용자가 폼을 제출했을 때 새로운 페이지로 이동하는 기본적인 HTML 폼 동작을 갖습니다. 만일 리액트에서 이 동작을 원한다면 그냥 작동하도록 두면 됩니다. 하지만 대부분의 경우에 폼의 제출을 처리하고 사용자가 폼에 입력한 데이터애 접근하는 자바스크립트 함수를 갖는 것이 편리합니다. 이를 위한 일반적인 방법은 controlled components라고 불리는 기술을 사용하는 것입니다.


## Controlled Components

HTML에서 \<input>, <textarea> 그리고 <select>와 같은 폼 엘리먼트는 일반적으로 그들 자신의 상태를 유지하고 사용자 입력에 따라서 그것을 업데이트합니다. 리액트에서 변경이 가능한 상태(state)는 보통 컴포넌트의 state 속성에 의해 유지되며 오직 setState()에 의해서만 업데이트됩니다.

우리는 리액트 state를 유일한 진실의 소스로 만들어 그 둘을 결합할 수 있습니다. 그런 다음 폼을 렌더링한 리액트 컴포넌트는 사용자 입력에 의해 발생하는 일들을 컨트롤합니다. 이러한 방식으로 리액트에 의해 그 값이 제어되는 input 폼 엘리먼트는 controlled component라고 불립니다.

예를 들어 이전 예제에서 제출된 이름을 기록하길 원한다면 우리는 controlled component로서 폼을 작성할 수 있습니다.
```
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

폼 엘리먼트에 value 속성이 설정되었기 때문에 표시된 값은 항상 리액트 상태를 진실의 소스로 만드는 this.state.value일 것입니다. handleChange는 키를 누를 때마다 리액트 상태를 업데이트하므로 표시된 값은 사용자가 타이핑을 할 때마다 업데이트될 것입니다.

controlled component를 사용하면 모든 상태 변화는 그것과 연관된 핸들러 함수를 가질 것입니다. 이는 사용자 입력을 변경하거나 유효성 검사하는 것을 쉽게 만듭니다. 예를 들어 이름을 모두 대문자로 작성하고 싶다면 우리는 handleChange를 다음과 같이 작성할 수 있습니다.
```
handleChange(event) {
  this.setState({value: event.target.value.toUpperCase()});
}
```

---

## The textarea Tag
HTML에서 \<textarea> 엘리먼트는 그것의 하위 엘리먼트에 의해 그 텍스트를 정의합니다.
```
<textarea>
  Hello there, this is some text in a text area
</textarea>
```

리액트에서 \<textarea>는 대신 value 속성을 사용합니다. 이러한 방식으로 \<textarea>를 사용하는 폼은 한 줄로 된 input을 사용하는 폼과 매우 비슷하게 작성될 수 있습니다.
```
class EssayForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 'Please write an essay about your favorite DOM element.'
    };

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('An essay was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Essay:
          <textarea value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

this.state.value는 생성자에서 초깃값을 설정한다는 점에 유의하세요. 그러므로 text area는 그 안의 텍스트로 시작합니다.

---

## The select Tag









---

내가 입력한 값이 화면에 다시 출력되도록 

* input
  * text
  * checkbox
  * radio
  * file
* textarea
* select

* 여러 개의 input

## input

#### text
```
import React from "react";

const App = () => {
  return (
    <div>
      <p>좋아하는 동물의 이름을 적어주세요.</p>
      <form>
        <label>
          Name:
          <input type="text" />
        </label>
        <input type="submit" value="Submit" />
      </form>
    </div>
  );
};

export default App;
```

submit 버튼을 클릭할 때 발생하는 onSubmit 이벤트와 상태의 초깃값이 input의 입력값으로 변하는 onChange 이벤트가 발생하게 됩니다.
상태의 변화가 있으므로 함수형 컴포넌트를 class형 컴포넌트로 바꿔줍니다.

```
// 초깃값 설정
constructor(props) {
    super(props);
    this.state = {
      value: ""
    };
  }

<input type="text" value={this.state.value} />
```


```
// onChange 이벤트
  // onChange 속성 추가
  <input
    type="text"
    value={this.state.value}
    onChange={this.handleChange}
  />
  
  // handleChange 메서드
  handleChange(e) {
    this.setState({
      value: e.target.value
    });
  }
  
  // 이벤트 핸들러 바인딩
  this.handleChange = this.handleChange.bind(this);
```


```
// onSubmit 이벤트
  // onSubmit 속성 추가
  <form onSubmit={this.handleSubmit}>
  
  // handleSubmit 메서드
  handleSubmit(e) {
    alert(this.state.value);
    e.preventDefault();
  }
  
  // 이벤트 핸들러 바인딩
  this.handleSubmit = this.handleSubmit.bind(this);
```

```
// 결과
import React from "react";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: "",
      name: ""
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(e) {
    this.setState({
      value: e.target.value
    });
  }

  handleSubmit(e) {
    alert(this.state.value);
    e.preventDefault();
  }

  render() {
    return (
      <div>
        <p>좋아하는 동물의 이름을 적어주세요.</p>
        <form onSubmit={this.handleSubmit}>
          <label>
            Name:
            <input
              type="text"
              value={this.state.value}
              onChange={this.handleChange}
            />
          </label>
          <input type="submit" value="Submit" />
        </form>
      </div>
    );
  }
}

export default App;
```

#### radio





## textarea
```
import React from "react";

class App extends React.Component {
  render() {
    return (
      <div>
        <p>추가사항을 적어주세요.</p>
        <form>
          <label>
            <input type="textarea" style={{ width: 200, height: 200 }} />
          </label>
          <input type="submit" value="Submit" />
        </form>
      </div>
    );
  }
}

export default App;
```

```
// 상태 초깃값 설정
constructor(props) {
  super(props);
  this.state = {
    value: "여기에 추가사항을 적어주세요."
  };
}
  
<input
  type="textarea"
  style={{ width: 200, height: 200 }}
  value={this.state.value}
/>  
```

```
// onChange 속성 추가
<input
  type="textarea"
  style={{ width: 200, height: 200 }}
  value={this.state.value}
  onChange={this.handleChange}
/>
            
handleChange(e) {
  this.setState({
    value: e.target.value
  });
}
  
this.handleChange = this.handleChange.bind(this);
```

```
// onSubmit 속성 추가
<form onSubmit={this.handleSubmit}>

handleSubmit(e) {
  alert(this.state.value);
  e.preventDefault();
}
  
this.handleSubmit = this.handleSubmit.bind(this);
```





