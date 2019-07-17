---
title: 상태 끌어올리기
seoTitle: 상태 끌어올리기 | React | ohoo
seoDescription: description for search engines
isFree: true
---


때로는 여러 개의 컴포넌트가 동일한 데이터를 반영할 필요가 있습니다. 우리는 가장 가까운 공통 조상에게 공유된 상태를 끌어올리는 방법을 추천합니다. 이것이 어떻게 작동하는지 살펴봅시다.

이번 섹션에서 우리는 주어진 온도에서 물이 끓는지 아닌지를 계산해주는 온도 계산기를 만들 것입니다.

BoilingVerdict라는 이름을 가진 컴포넌트로 시작합니다. 이 컴포넌트는 celsius 온도를 prop으로 갖고 물이 끓기에 충분한지 아닌지를 프린트합니다.
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
우리는 
우리는 





















































