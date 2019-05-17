---
title: 폼
seoTitle: 폼 | React | ohoo
seoDescription: description for search engines
isFree: true
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





