---
title: 폼
seoTitle: 폼 | React | ohoo
seoDescription: description for search engines
isFree: true
---


HTML 폼 엘리먼트는 리액트의 다른 DOM 엘리먼트들과 약간 다르게 작동합니다. 왜냐하면 폼 엘리먼트는 몇몇 내부 상태(state)를 갖기 때문입니다. 다음 코드는 이름을 적는 HTML 폼입니다.
```
<form>
  <label>
    Name:
    <input type="text" name="name" />
  </label>
  <input type="submit" value="Submit" />
</form>
```

이 폼은 사용자가 폼을 제출했을 때 새로운 페이지로 이동하는 기본적인 HTML 폼 동작을 갖습니다. 만일 리액트에서 이 동작을 원한다면 그냥 작동하도록 두면 됩니다. 하지만 대부분의 경우에는 자바스크립트 함수로 제출된 폼을 처리하고 폼에 입력된 데이터를 다룹니다. 이를 위한 일반적인 방법은 controlled components를 사용하는 것입니다.


## Controlled Components

HTML에서 \<input>, \<textarea> 그리고 \<select>와 같은 폼 엘리먼트는 일반적으로 그들 자신의 상태를 유지하고 사용자 입력에 따라서 그것을 업데이트합니다. 리액트에서 변경이 가능한 상태(state)는 보통 컴포넌트의 state 속성에 의해 유지되며 오직 setState()에 의해서만 업데이트됩니다.

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

폼 엘리먼트에는 value 속성이 설정되어 있으며 표시된 값은 항상 리액트 상태를 진실의 소스로 만드는 this.state.value입니다. handleChange는 키를 누를 때마다 리액트 상태를 업데이트하므로 표시된 값은 사용자가 타이핑을 할 때마다 업데이트될 것입니다.

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

this.state.value는 생성자에서 초깃값을 설정한다는 점에 유의하세요. 그러므로 textarea는 그 안의 텍스트로 시작합니다.

---

## The select Tag
HTML에서 \<select>는 drop-down 목록을 생성합니다. 예를 들면 아래 HTML은 맛에 대한 drop-down 목록을 생성합니다.
```
<select>
  <option value="grapefruit">Grapefruit</option>
  <option value="lime">Lime</option>
  <option selected value="coconut">Coconut</option>
  <option value="mango">Mango</option>
</select>
```

selected 속성으로 인해 초깃값으로 Coconut 옵션이 선택되었다는 점에 유의하세요. 리액트에서는 selected 속성을 사용하는 대신에 루트 select 태그에서 value 속성을 사용합니다. controlled component에서는 한 곳에서 업데이트를 할 수 있으므로 이 방식이 조금 더 편리합니다. 


결과적으로 이것은 \<input type="text">, \<textarea> 그리고 \<select> 모두 비슷하게 작동하도록 합니다. 그들은 value 속성을 받아들여 여러분이 controlled component를 실행할 수 있도록 합니다. 


## The file input Tag
HTML에서 \<input type="file">은 사용자가 기계 장치의 스토리지에서 서버로 업로드되거나 파일 API를 통해 자바스크립트로 처리될 하나 혹은 그 이상의 파일을 선택하도록 합니다. 
```
<input type="file" />
```

그 값은 읽기 전용이므로 리액트에서 이것은 uncontrolled component입니다. 이는 나중에 다른 uncontrolled component들과 함께 설명될 것입니다.


## Handling Multiple Inputs
여러 개의 controlled input 엘리먼트를 처리해야할 때 여러분은 각 엘리먼트에 name 속성을 추가하고 핸들러 함수가 event.target.name 값에 따라 무엇을 할 지 선택하도록 할 수 있습니다.



## Controlled Input Null Value

controlled component에 value prop을 지정하면 사용자는 input을 변경할 수 없습니다. 만일 value를 지정했지만 input이 여전히 수정가능하다면 아마 value가 undefined 혹은 null로 설정되어 있을 것입니다.

다음 코드가 이를 잘 설명해줍니다.(처음에 input은 고정되어 있지만 약간의 시간이 지난 후에 수정이 가능해집니다.)
```
ReactDOM.render(<input value="hi" />, mountNode);

setTimeout(function() {
  ReactDOM.render(<input value={null} />, mountNode);
}, 1000);
```


## Alternatives to Controlled Components
데이터가 변경되는 모든 방법에 대한 이벤트 핸들러를 작성하고 리액트 컴포넌트를 통해서 모든 input state를 보내야 하므로 controlled components를 사용하는 일은 때로 번거로울 수도 있습니다. 이는 기존의 코드를 리액트로 바꾸거나 리액트 애플리케이션을 비-리액트 라이브러리와 통합할 때 특히 더 그렇습니다. 이러한 경우에는 input 폼을 실행하는 대체적인 기술인 uncontrolled components를 확인해볼 수 있습니다.


## Fully-Fledged Solutions
만일 여러분이 유효성 검사, 방문된 필드에 대한 추적 그리고 폼 제출 처리하기를 모두 포함한 완벽한 해결책을 찾고 있다면 Formik은 가장 인기있는 선택 중의 하나가 될 것입니다. 그러나 Formik은 controlled components와 상태 관리와 동일한 원리에 따라 작성되었습니다. 


## Uncontrolled Components
대부분의 상황에서 우리는 폼을 실행하기 위해 제어 컴포넌트를 사용하길 추천합니다. 제어 컴포넌트에서 폼 데이터는 리액트 컴포넌트에 의해 처리됩니다. 제어 컴포넌트를 사용하는 대신 비제어 컴포넌트를 사용할 수도 있는데 비제어 컴포넌트에서 폼 데이터는 DOM 자체에 의해 처리됩니다.

매번 상태 업데이트를 하기 위해 이벤트 핸드러를 사용하는 대신에 비제어 컴포넌트를 사용하기 위해서 여러분은 DOM에서 폼 값을 가져오는 ref를 사용할 수 있습니다.

예를 들면 이 코드는 비제어 컴포넌트에서 하나의 이름(name)을 받아들입니다.
```
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.handleSubmit = this.handleSubmit.bind(this);
    this.input = React.createRef();
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.input.current.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" ref={this.input} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

비제어 컴포넌트는 DOM에서 진실의 소스를 유지하기 때문에 리액트와 비-리액트 코드를 결합을 좀 더 쉽게 만들어 줍니다. 비제어 컴포넌트를 사용하면 코드를 더 적게 작성합니다.

언제 제어 혹은 비제어 컴포넌트를 사용해야 하는지 아직 명확하지 않다면 다음의 기사가 도움이 될 것입니다.
원문을 읽어보려면 https://goshakkk.name/controlled-vs-uncontrolled-inputs-react/


















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
      value: ""
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
    e.preventDefault();
    alert(this.state.value);
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

#### checkbox


#### radio
```
import React from "react";

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      sex: ""
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(e) {
    this.setState({ sex: e.target.value });
  }

  handleSubmit(e) {
    e.preventDefault();
    alert("A name was submitted: " + this.state.sex);
  }

  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          <label>
            Male:
            <input
              type="radio"
              value="male"
              checked={this.state.sex === "male"}
              onChange={this.handleChange}
            />
          </label>
          <label>
            Female:
            <input
              type="radio"
              value="female"
              checked={this.state.sex === "female"}
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





