---
title: 상태 끌어올리기
seoTitle: 상태 끌어올리기 | React | ohoo
seoDescription: description for search engines
isFree: true
---


때로는 여러 개의 컴포넌트가 동일한 데이터를 반영할 필요가 있습니다. 우리는 가장 가까운 공통 조상에게 공유된 상태를 끌어올리는 방법을 추천합니다. 이것이 어떻게 작동하는지 살펴봅시다.

이번 섹션에서 우리는 주어진 온도에서 물이 끓는지 아닌지를 계산해주는 온도 계산기를 만들 것입니다.

BoilingVerdict라는 이름을 가진 컴포넌트로 시작합니다. 이 컴포넌트는 섭씨 온도를 prop으로 갖고 물이 끓기에 충분한지 아닌지 합니다.
```
function BoilingVerdict(props) {
  if (props.celsius >= 100) {
    return <p>The water would boil.</p>;
  }
  return <p>The water would not boil.</p>;
}
```

다음으로 Calculator라는 이름의 컴포넌트를 작성합니다. 이 컴포넌트는 온도를 적을 수 있는 input을 렌더링하고 그 값은 this.state.temperature에서 유지됩니다.

현재 input 값에 따라 BoilingVerdict를 렌더링합니다.


## Adding a Second Input
섭씨 온도를 적는 input 뿐만 아니라 화씨 온도를 적는 input을 적고 그 둘을 동기화합니다.

Calculator에서 TemperatureInput 컴포넌트를 분리하는 것으로 시작할 수 있습니다. 우리는 여기에 "c"나 "f" 값을 갖는 scale prop을 추가할 것입니다.
```
const scaleNames = {
  c: 'Celsius',
  f: 'Fahrenheit'
};

class TemperatureInput extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
    this.state = {temperature: ''};
  }

  handleChange(e) {
    this.setState({temperature: e.target.value});
  }

  render() {
    const temperature = this.state.temperature;
    const scale = this.props.scale;
    return (
      <fieldset>
        <legend>Enter temperature in {scaleNames[scale]}:</legend>
        <input value={temperature}
               onChange={this.handleChange} />
      </fieldset>
    );
  }
}
```

이제 Calculator는 두 개의 분리된 TemperatureInput을 렌더링하도록 변경됩니다.
```
class Calculator extends React.Component {
  render() {
    return (
      <div>
        <TemperatureInput scale="c" />
        <TemperatureInput scale="f" />
      </div>
    );
  }
}
```

이제 우리는 두 개의 input을 가지고 있지만 그들 중 하나에 온도가 입력될 때 다른 하나는 업데이트가 되지 않습니다. 이것은 앞서 둘을 동기화한다고 했던 것과 모순됩니다.

또한 우리는 Calculator로부터 BoilingVerdict를 보여줄 수 없습니다. Calculator는 TemperatureInput 내부에 숨겨져 있기 때문에 현재 온도를 알 수 없습니다.


## Writing Conversion Functions
우리는 섭씨 온도를 화씨 온도로 바꾸고 화씨 온도를 섭씨 온도로 바꾸는 2개의 함수를 작성할 것입니다.
```
function toCelsius(fahrenheit) {
  return (fahrenheit - 32) * 5 / 9;
}

function toFahrenheit(celsius) {
  return (celsius * 9 / 5) + 32;
}
```

이 두 개의 함수는 숫자를 변환합니다. 우리는 인수로 문자열 temperature와 변환 함수를 가져와 문자열 반환하는 다른 함수를 작성할 것입니다. 우리는 그 함수를 다른 입력값을 기반으로 입력값을 계산하기 위해 사용할 것입니다.

그 함수는 유효하지 않은 온도에 빈 문자열을 반환하며 소수점 이하 세번째 자리 수를 결과로 반환합니다.
```
function tryConvert(temperature, convert) {
  const input = parseFloat(temperature);
  if (Number.isNaN(input)) {
    return '';
  }
  const output = convert(input);
  const rounded = Math.round(output * 1000) / 1000;
  return rounded.toString();
}
```

예를 들면 tryConvert('abc', toCelsius)는 빈 문자열을 반환하고, tryConvert('10.22', toFahrenheit)는 '50.396'을 반환합니다.


## Lifting State Up
현재 두 TemperatureInput 컴포넌트는 로컬 상태에서 독립적으로 그 값을 유지합니다.
```
class TemperatureInput extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
    this.state = {temperature: ''};
  }

  handleChange(e) {
    this.setState({temperature: e.target.value});
  }

  render() {
    const temperature = this.state.temperature;
    // ...  
```

그러나 우리는 이 두 개의 input이 서로 동기화되길 원합니다. 우리가 섭씨 input을 업데이터했을 때 화씨 input은 변환된 온도롤 반영하거나 반대여야 합니다.

리액트에서 공유 상태는 그것을 필요로 하는 컴포넌트들의 가장 가까운 공통 조상으로 올라감에 의해 달성됩니다. 우리는 이것을 "상태 끌어올리기"라고 합니다. 우리는 TemperatureInput에서 내부 상태를 제거한 대신에 Calculator로 이동시킬 것입니다.

Calculator가 공유 상태를 갖게 되면 그것은 두 개의 input에서 현재 온도에 대한 "진실의 근원"이 됩니다. 그것은 그들이 서로 일치하는 값을 갖도록 합니다. 두 TemperatureInput 컴포넌트의 props는 동일한 부모 컴포넌트 Calculator에서 왔기 때문에 그 두 개의 input은 항상 동기화됩니다.

이것이 단계적으로 어떻게 작동하는지 살펴봅시다.

첫 번째로 우리는 TemperatureInput 컴포넌트에서 this.state.temperature를 this.props.temperature로 변경합니다. 비록 우리는 미래에 Calculator로부터 그것을 전달할 필요가 있지만 당분간은 this.props.temperature가 존재하는 척 해봅시다.
```
render() {
    // Before: const temperature = this.state.temperature;
    const temperature = this.props.temperature;
    // ...
```

우리는 props가 읽기 전용이라는 것을 알고 있습니다. temperature가 로컬 상태에 있을 때 TemperatureInput은 그것을 변경하기 위해 this.setState()을 호출할 것입니다. 그러나 temperature가 부모로부터 prop으로 왔기 때문에 TemperatureInput은 그것을 제어할 수 없습니다.

리액트에서 이것은 제어 컴포넌트를 만드는 것에 의해 해결됩니다. DOM처럼 \<input>은 value와 onChange prop을 둘 다 받아들이므로 TemperatureInput은 그의 부모 Calculator로부터 temperature와 onTemperatureChange props를 받아들입니다.

이제 TemperatureInput이 그것의 온도를 업데이트하려고 할 때 그것은 this.props.onTemperatureChange를 호출합니다.
```
handleChange(e) {
    // Before: this.setState({temperature: e.target.value});
    this.props.onTemperatureChange(e.target.value);
    // ...
```

onTemperatureChange prop은 그 부모 컴포넌트 Calculator에 의해 temperature prop과 함께 제공될 것입니다. 그것은 로컬 상태를 변경하고 새로운 값을 가진 두 개의 input을 리렌더링함에 의해 변화를 관리합니다. 우리는 새로운 Calculator가 실행되는 것을 곧 보게 될 것입니다.

Calculator의 변경에 대해 살펴보기에 앞서 TemperatureInput에 어떤 변화가 있는지 다시 한 번 살펴보겠습니다. 우리는 그것으로부터 로컬 상태를 제거하고 this.state.temperature를 읽는 대신에 this.props.temperature를 읽고 있습니다. 변경하려고 할 때 this.setState()를 호출하는 대신에 우리는 Calculator에 의해 제공되는 this.props.onTemperatureChange()를 호출합니다.
```
class TemperatureInput extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
  }

  handleChange(e) {
    this.props.onTemperatureChange(e.target.value);
  }

  render() {
    const temperature = this.props.temperature;
    const scale = this.props.scale;
    return (
      <fieldset>
        <legend>Enter temperature in {scaleNames[scale]}:</legend>
        <input value={temperature}
               onChange={this.handleChange} />
      </fieldset>
    );
  }
}
```

















































