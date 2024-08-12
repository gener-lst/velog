<h2 id="문제">문제</h2>
<p>괄호 회전하기(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/76502">https://school.programmers.co.kr/learn/courses/30/lessons/76502</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
</blockquote>
<p>다음 규칙을 지키는 문자열을 올바른 괄호 문자열이라고 정의합니다.</p>
<ul>
<li><code>()</code>, <code>[]</code>, <code>{}</code> 는 모두 올바른 괄호 문자열입니다.</li>
<li>만약 A가 올바른 괄호 문자열이라면, <code>(A)</code>, <code>[A]</code>, <code>{A}</code> 도 올바른 괄호 문자열입니다. 예를 들어, <code>[]</code> 가 올바른 괄호 문자열이므로, <code>([])</code> 도 올바른 괄호 문자열입니다.</li>
<li>만약 <code>A</code>, <code>B</code>가 올바른 괄호 문자열이라면, <code>AB</code> 도 올바른 괄호 문자열입니다. 예를 들어, <code>{}</code> 와 <code>([])</code> 가 올바른 괄호 문자열이므로, <code>{}([])</code> 도 올바른 괄호 문자열입니다.<blockquote>
</blockquote>
대괄호, 중괄호, 그리고 소괄호로 이루어진 문자열 <code>s</code>가 매개변수로 주어집니다. 이 <code>s</code>를 왼쪽으로 x (0 ≤ x &lt; (<code>s</code>의 길이)) 칸만큼 회전시켰을 때 <code>s</code>가 올바른 괄호 문자열이 되게 하는 x의 개수를 return 하도록 solution 함수를 완성해주세요.</li>
</ul>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>s의 길이는 1 이상 1,000 이하입니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<table>
<thead>
<tr>
<th align="left">numbers</th>
<th align="left">result</th>
</tr>
</thead>
<tbody><tr>
<td align="left"><code>&quot;[](){}&quot;</code></td>
<td align="left">3</td>
</tr>
<tr>
<td align="left"><code>&quot;}]()[{&quot;</code></td>
<td align="left">2</td>
</tr>
<tr>
<td align="left"><code>&quot;[)(]&quot;</code></td>
<td align="left">0</td>
</tr>
<tr>
<td align="left"><code>&quot;}}}&quot;</code></td>
<td align="left">0</td>
</tr>
</tbody></table>
<blockquote>
<h4 id="입출력-예-설명">입출력 예 설명</h4>
<p>입출력 예 #1</p>
</blockquote>
<ul>
<li>다음 표는 <code>&quot;[](){}&quot;</code> 를 회전시킨 모습을 나타낸 것입니다.<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">x</th>
<th align="left">s를 왼쪽으로 x칸만큼 회전</th>
<th align="left">올바른 괄호 문자열?</th>
</tr>
</thead>
<tbody><tr>
<td align="left">0</td>
<td align="left"><code>&quot;[](){}&quot;</code></td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">1</td>
<td align="left"><code>&quot;](){}[&quot;</code></td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left"><code>&quot;(){}[]&quot;</code></td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left"><code>&quot;){}[](&quot;</code></td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left"><code>&quot;{}[]()&quot;</code></td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">5</td>
<td align="left"><code>&quot;}[](){&quot;</code></td>
<td align="left">X</td>
</tr>
</tbody></table>
</li>
<li>올바른 괄호 문자열이 되는 x가 3개이므로, 3을 return 해야 합니다.<blockquote>
</blockquote>
입출력 예 #2</li>
<li>다음 표는 <code>&quot;}]()[{&quot;</code> 를 회전시킨 모습을 나타낸 것입니다<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">x</th>
<th align="left">s를 왼쪽으로 x칸만큼 회전</th>
<th align="left">올바른 괄호 문자열?</th>
</tr>
</thead>
<tbody><tr>
<td align="left">0</td>
<td align="left"><code>&quot;[](){}&quot;</code></td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">1</td>
<td align="left"><code>&quot;](){}[&quot;</code></td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left"><code>&quot;(){}[]&quot;</code></td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left"><code>&quot;){}[](&quot;</code></td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left"><code>&quot;{}[]()&quot;</code></td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">5</td>
<td align="left"><code>&quot;}[](){&quot;</code></td>
<td align="left">X</td>
</tr>
</tbody></table>
</li>
<li>올바른 괄호 문자열이 되는 x가 2개이므로, 2를 return 해야 합니다.<blockquote>
</blockquote>
입출력 예 #3</li>
<li>s를 어떻게 회전하더라도 올바른 괄호 문자열을 만들 수 없으므로, 0을 return 해야 합니다.<blockquote>
</blockquote>
입출력 예 #4</li>
<li>s를 어떻게 회전하더라도 올바른 괄호 문자열을 만들 수 없으므로, 0을 return 해야 합니다.</li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>stack을 이용하여 모든 괄호에 대해 쌍을 맞춰 pop시키고, stack을 모두 비울 수 있는지 여부에 따라 올바른 괄호 문자열인지 확인</li>
<li>주어진 괄호 문자열(s)의 길이는 1 &lt;= s &lt;= $10^3$ 이고 문자열의 회전은 s.length번 하게되므로 올바른 괄호 문자열인지 s.length번 검사하게 됨 </li>
</ul>
<br />    

<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>solution 함수: 괄호 문자열 s를 왼쪽으로 한 칸씩 회전시킬 때마다 isValid 함수를 통해 유효한 괄호 문자열인지 검사하고 유효한 괄호 문자열일 경우, answer에 +1을 해줌. 
s.length번 반복하고 answer를 return</li>
<li>isValid 함수:  <ol>
<li>s를 한 글자씩 순회하며 해당 글자가 열린 괄호([ &quot;(&quot;, &quot;{&quot;, &quot;[&quot; ])라면 stack에 push.</li>
<li>닫힌 괄호([ &quot;)&quot;, &quot;}&quot;, &quot;]&quot; ])라면, stack이 비었는지 먼저 확인<ul>
<li>stack이 비어있는데 닫힌 괄호가 나왔다는 것은 유효한 괄호 문자열이 아니라는 것을 의미 </li>
</ul>
</li>
<li>stack의 top에 저장된 요소가 같은 쌍의 열린 괄호인지 확인하고, 맞다면 pop</li>
<li>모든 문자열에 대한 검사가 끝난 후 stack이 비어있는지 여부를 반환<ul>
<li>stack이 비어있다면, 모든 괄호가 쌍을 이루었다는 의미이므로 유효한 괄호 문자열이라고 판단하여 true 반환. 반대의 경우 false 반환.   </li>
</ul>
</li>
</ol>
</li>
</ul>
<br />

<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int solution(String s) {
        int answer = 0;

        for (int i = 0; i &lt; s.length(); i++) {
            if (isValid(s)) answer += 1;
            s = s.substring(1) + s.charAt(0);
        }

        return answer;
    }

    public boolean isValid(String s) {
        Deque&lt;Character&gt; stack = new ArrayDeque&lt;&gt;();

        for (int i = 0; i &lt; s.length(); i++) {
            char ch = s.charAt(i);
            if (ch == '(' || ch == '[' || ch == '{') {
                stack.push(ch);
            } else {
                if (stack.isEmpty()) return false;
                if ((stack.peek() == '(' &amp;&amp; ch == ')') ||
                    (stack.peek() == '[' &amp;&amp; ch == ']') ||
                    (stack.peek() == '{' &amp;&amp; ch == '}')) {
                    stack.pop();
                }
            }
        }
        return stack.isEmpty();
    }
}</code></pre>