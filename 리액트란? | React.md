<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>리액트란? | React</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li><a href="#ui를-만들기-위한">UI를 만들기 위한</a>
<ul>
<li><a href="#자바스크립트-라이브러리">자바스크립트 라이브러리</a></li>
<li><a href="#리액트를-배우기-전에">리액트를 배우기 전에</a></li>
<li><a href="#리액트-사용하기">리액트 사용하기</a></li>
<li><a href="#리액트-사용하기-1">리액트 사용하기</a></li>
<li><a href="#앞으로-배울-개념">앞으로 배울 개념</a></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <pre><code>A JavaScript library for building user interfaces
</code></pre>
<p>공식 문서에 따르면 리액트는 UI를 만들기 위한 자바스크립트 라이브러리라고 설명되어 있습니다. 이 문장 만으로도 리액트가 무엇인지 이해가 되는 분들이 있는 반면 '이게 무슨 소리지?'라는 생각이 드는 분들도 있을 겁니다.</p>
<p>조금 풀어서 이야기하자면 리액트는 웹 애플리케이션의 프론트엔드 코드를 작성하는데 사용되는 도구입니다. <strong>가상DOM</strong>과 <strong>컴포넌트</strong>라는 개념을 사용하여 자바스크립트 코드를 조금 더 편리하게 작성할 수 있도록 도와줍니다.</p>
<p>조금 더 자세한 설명을 위해 위의 문장을 2개의 부분으로 나눠 보겠습니다.</p>
<ul>
<li>UI를 만들기 위한</li>
<li>자바스크립트 라이브러리</li>
</ul>
<h1 id="ui를-만들기-위한">UI를 만들기 위한</h1>
<pre><code>UI = user interface = 사용자 인터페이스
</code></pre>
<p>우리가 사용하는 웹사이트들은 개발자가 미리 작성해 서버에 저장해 놓은 코드들 입니다. 사용자가 www로 시작하는 주소를 입력해 서버에 정보를 요청하면 서버는 저장된 코드를 브라우저에 보내주고 브라우저는 이 코드를 화면에 그려줍니다. 이 때 화면에 출력된 웹페이지를 UI라고 하며 UI는 사용자 입력에 따라 변하기도 합니다.</p>
<p>그러므로 'UI를 만든다’는 것은 웹페이지가 어떤 내용을 담고 있으며, 어떻게 배치되고, 텍스트 입력이나 마우스 클릭같은 동작들이 발생했을 때 어떻게 변경될 것인지에 대한 코드를 작성하는 일이라고 볼 수 있습니다. 즉 뷰(view)와 관련된 코드를 작성하는 것이므로 ‘프론트엔드 코드를 작성한다’ 혹은 '클라이언트 측 코드를 작성한다’와 동일한 의미로 볼 수는 없습니다.</p>
<h2 id="자바스크립트-라이브러리">자바스크립트 라이브러리</h2>
<pre><code>라이브러리 = 도구
</code></pre>
<p>자바스크립트 라이브러리란 자바스크립트를 조금 더 쉽게 사용할 수 있도록 도와주는 도구를 말합니다. 우리는 이 도구의 내부가 어떻게 생겼는지, 어떤 원리로 작동 되는지에 대해서 알 필요가 없으며 정확한 사용 방법만 익히면 됩니다.</p>
<p>라이브러리이기 때문에 프레임워크보다는 가볍게 사용할 수 있지만 위에서 언급했듯이 뷰와 관련된 코드를 작성하는데 사용되는 라이브러리이기 때문에 추가적인 기능들을 구현하기 위해서 다른 도구들을 함께 사용해야 합니다.</p>
<h2 id="리액트를-배우기-전에">리액트를 배우기 전에</h2>
<p>리액트를 배우기 전에 다음과 같은 내용에 대해 알고 있어야 합니다.</p>
<ul>
<li>HTML</li>
<li>CSS</li>
<li>JavaScript(ES6)</li>
<li>Node.js</li>
</ul>
<h2 id="리액트-사용하기">리액트 사용하기</h2>
<p>All your files and folders are presented as a tree in the file explorer. You can switch from one to another by clicking a file in the tree.</p>
<h2 id="리액트-사용하기-1">리액트 사용하기</h2>
<p>You can rename the current file by clicking the file name in the navigation bar or by clicking the <strong>Rename</strong> button in the file explorer.</p>
<h2 id="앞으로-배울-개념">앞으로 배울 개념</h2>
<p>You can delete the current file by clicking the <strong>Remove</strong> button in the file explorer. The file will be moved into the <strong>Trash</strong> folder and automatically deleted after 7 days of inactivity.</p>

    </div>
  </div>
</body>

</html>
