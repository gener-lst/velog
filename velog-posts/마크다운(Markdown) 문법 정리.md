<h2 id="1-마크다운markdown이란">1. 마크다운(Markdown)이란?</h2>
<blockquote>
<p>마크다운(Markdown)은 일반 텍스트 기반의 경량 마크업 언어다. 일반 텍스트로 서식이 있는 문서를 작성하는 데 사용되며, 일반 마크업 언어에 비해 문법이 쉽고 간단한 것이 특징이다. HTML과 리치 텍스트(RTF) 등 서식 문서로 쉽게 변환되기 때문에 응용 소프트웨어와 함께 배포되는 README 파일이나 온라인 게시물 등에 많이 사용된다. 
- 위키백과</p>
</blockquote>
<h3 id="마크다운의-장단점">마크다운의 장단점</h3>
<h4 id="nbspnbsp장점">&amp;nbsp&amp;nbsp장점</h4>
<pre><code>1. 쉽고 직관적이다.
2. 가독성이 좋다.
3. 다양한 플랫폼에서 지원된다.
4. 버전 관리 시스템과 호환성이 좋다. (git/gitHub)</code></pre><h4 id="nbspnbsp단점">&amp;nbsp&amp;nbsp단점</h4>
<pre><code>1. 다른 마크업 언어에 비해 제한된 기능으로 복잡한 레이아웃이나 스타일의 표현이 어렵다.
    -&gt; 이로 인해 HTML을 완전히 대체하기는 어렵다.
2. 표준이 없기 때문에 각 플랫폼 또는 소프트웨어마다 약간의 차이가 있을 수 있다.</code></pre><h2 id="2-마크다운-문법">2. 마크다운 문법</h2>
<h3 id="제목">제목</h3>
<p><code>h1 ~ h6</code>까지 표현할 수 있다. #의 개수를 다르게 하여 작성 가능하다.</p>
<pre><code>#        h1
##        h2     
###        h3
####    h4
#####    h5
######    h6</code></pre><h3 id="강조">강조</h3>
<p>글자 강조 표현은 굵게(Bold), 이텔릭(Italic), 취소선이 있다.</p>
<p>입력</p>
<pre><code>**굵게**
_이텔릭_
~~취소선~~</code></pre><p>출력</p>
<p><strong>굵게</strong>
<em>이텔릭</em>
<del>취소선</del></p>
<h3 id="체크박스">체크박스</h3>
<p>체크박스는 <code>[ ]</code>의 형태로 표현가능하다. 체크표시를 넣으려면 <code>[x]</code>로 표기해야되며 대괄호 앞뒤로 한 칸씩 여백을 입력해야 한다.</p>
<ul>
<li><input disabled="" type="checkbox" /> </li>
<li><input checked="" disabled="" type="checkbox" /> </li>
</ul>
<h3 id="수평선">수평선</h3>
<p>문단 간 구분선으로 사용되는 수평선은 <code>&lt;hr/&gt;</code> 태그를 직접 입력하여 표현할 수 있으며, <code>***</code>, <code>---</code>, <code>___</code>의 기호로도 표현가능하다.</p>
<p>입력</p>
<pre><code>문단1

&lt;hr/&gt;
문단2

***
문단3

---
문단4

___</code></pre><p>출력</p>
<p>문단1</p>
<hr />
문단2

<hr />
<p>문단3</p>
<hr />
<p>문단4</p>
<hr />
<h3 id="블럭인용">블럭인용</h3>
<p><code>&gt;</code>을 인용된 내용을 다루는 문단 앞에 입력한다. 여러 개 중첩이 가능하다.</p>
<p>입력 </p>
<pre><code>&gt; 인용 문단
&gt;&gt; 1개 중첩
&gt;&gt;&gt; 2개 중첩</code></pre><p>출력</p>
<blockquote>
<p>인용 문단</p>
<blockquote>
<p>1개 중첩</p>
<blockquote>
<p>2개 중첩</p>
</blockquote>
</blockquote>
</blockquote>
<h3 id="코드블럭">코드블럭</h3>
<p>코드블럭은 <code>tab</code> 또는 <code>```</code>으로 작성할 수 있다. 코드가 한 줄이라면 <code>tab</code> 뒤에(앞 줄 개행이 필요함), 코드가 여러 줄이라면 <code>```</code> 사이에 작성한다. 코드가 여러 줄일 경우, 사용하는 언어를 기입하여 해당 언어의 syntax highlighting을 반영할 수 있다. 인라인에도 코드 삽입이 가능하다. 코드를 인라인으로 표기하면,</p>
<blockquote>
<p>출력문은 <code>print('Hello World!')</code> 형태이다.</p>
</blockquote>
<p>처럼 표기된다.</p>
<h4 id="한-줄-예시">한 줄 예시</h4>
<p>입력</p>
<p>(tab) print('Hello World!') ;</p>
<p>출력</p>
<pre><code>print('Hello World!') ;</code></pre><h4 id="여러-줄-예시">여러 줄 예시</h4>
<p>입력</p>
<pre><code>``` javascript
let sayHi = function () {
    console.log('Hello World!');
    }
sayHi(); ```</code></pre><p>출력</p>
<pre><code class="language-javascript">let sayHi = function () {
    console.log('Hello World!');
    }
sayHi();</code></pre>
<h3 id="목록">목록</h3>
<h4 id="순서-있는-목록">순서 있는 목록</h4>
<p>순서 있는 목록은 글머리에 <code>숫자</code> + <code>.</code> 으로 작성한다. 순서 있는 목록의 경우 작성한 순서에 상관없이 숫자의 내림차순으로 정렬된다. 소항목의 경우 <code>숫자</code> + <code>)</code> 으로 작성한다.</p>
<p>입력</p>
<pre><code>1. 첫번째 목록
1) 첫번째 소항목
2) 두번째 소항목
2. 두번째 목록
3. 세번째 목록</code></pre><p>출력</p>
<ol>
<li>첫번째 목록
1) 첫번째 소항목
2) 두번째 소항목</li>
<li>두번째 목록</li>
<li>세번째 목록</li>
</ol>
<h4 id="순서-없는-목록">순서 없는 목록</h4>
<p>순서 없는 목록은 글머리에 <code>-</code> / <code>*</code> / <code>+</code>으로 작성한다. </p>
<p>입력</p>
<pre><code>* 치킨
    + 피자
        - 햄버거</code></pre><p>출력</p>
<ul>
<li>치킨<ul>
<li>피자<ul>
<li>햄버거</li>
</ul>
</li>
</ul>
</li>
</ul>
<h3 id="표테이블">표(테이블)</h3>
<p><code>&lt;table&gt;</code>태그와 같은 표를 작성하기 위해서는 <code>|</code>과 줄바꿈을 통해 행과 열을 구분한다. <code>---</code>을 통해 헤더를 구분하고 해당 줄에 <code>:</code>을 좌측에 삽입하면 좌측 정렬, <code>:</code>을 우측에 삽입하면 우측 정렬, 양쪽 모두 삽입하면 중앙 정렬이 된다. 셀 내부의 내용에 글자 강조 표시도 적용 가능하다.</p>
<pre><code>|구문        |설명   |비고 |
|:---       |:---:  |---:|
|**Header** |_Title_|1   |
|`Paragraph`|Text   |2   |</code></pre><table>
<thead>
<tr>
<th align="left">구문</th>
<th align="center">설명</th>
<th align="right">비고</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><strong>Header</strong></td>
<td align="center"><em>Title</em></td>
<td align="right">1</td>
</tr>
<tr>
<td align="left"><code>Paragraph</code></td>
<td align="center">Text</td>
<td align="right">2</td>
</tr>
</tbody></table>
<h3 id="이미지-삽입">이미지 삽입</h3>
<p>이미지 삽입은 <code>![이미지 설명](이미지 소스 URL &quot;이미지 설명&quot;)</code>의 형식으로 입력한다.</p>
<p>입력</p>
<pre><code>![이미지 미리보기](https://velog.velcdn.com/images/gener-lst/post/image.png &quot;이미지 미리보기&quot;)</code></pre><p>출력
<img alt="포스트 미리보기" src="https://velog.velcdn.com/images/gener-lst/post/da905b42-f14f-47c1-aa3d-5c98d1bc7750/image.png" title="이미지 미리보기" /></p>
<h3 id="링크-삽입">링크 삽입</h3>
<p>링크 삽입은 바로 링크를 삽입하는 방식과 텍스트에 링크를 거는 방식으로 나뉜다. 이 때, 링크 주소 뒤에 <code>&quot;&quot;</code> 내부에 추가 설명을 작성할 수 있다.</p>
<p>입력</p>
<pre><code>https://velog.io/@gener-lst
[내 velog 바로가기](https://velog.io/@gener-lst &quot;개발자 지망생&quot;)</code></pre><p>출력</p>
<p><a href="https://velog.io/@gener-lst">https://velog.io/@gener-lst</a>
<a href="https://velog.io/@gener-lst" title="개발자 지망생">내 velog 바로가기</a></p>