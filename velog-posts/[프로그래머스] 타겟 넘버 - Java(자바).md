<h2 id="문제">문제</h2>
<p>타겟 넘버(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/43165">https://school.programmers.co.kr/learn/courses/30/lessons/43165</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
</blockquote>
<p>n개의 음이 아닌 정수들이 있습니다. 이 정수들을 순서를 바꾸지 않고 적절히 더하거나 빼서 타겟 넘버를 만들려고 합니다. 예를 들어 [1, 1, 1, 1, 1]로 숫자 3을 만들려면 다음 다섯 방법을 쓸 수 있습니다.</p>
<pre><code>-1+1+1+1+1 = 3
+1-1+1+1+1 = 3
+1+1-1+1+1 = 3
+1+1+1-1+1 = 3
+1+1+1+1-1 = 3</code></pre><blockquote>
<p>사용할 수 있는 숫자가 담긴 배열 numbers, 타겟 넘버 target이 매개변수로 주어질 때 숫자를 적절히 더하고 빼서 타겟 넘버를 만드는 방법의 수를 return 하도록 solution 함수를 작성해주세요.</p>
</blockquote>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>주어지는 숫자의 개수는 2개 이상 20개 이하입니다.</li>
<li>각 숫자는 1 이상 50 이하인 자연수입니다.</li>
<li>타겟 넘버는 1 이상 1000 이하인 자연수입니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<table>
<thead>
<tr>
<th align="left">numbers</th>
<th align="left">target</th>
<th align="left">return</th>
</tr>
</thead>
<tbody><tr>
<td align="left">[1, 1, 1, 1, 1]</td>
<td align="left">3</td>
<td align="left">5</td>
</tr>
<tr>
<td align="left">[4, 1, 2, 1]</td>
<td align="left">4</td>
<td align="left">2</td>
</tr>
</tbody></table>
<blockquote>
<h4 id="입출력-예-설명">입출력 예 설명</h4>
</blockquote>
<ul>
<li>입출력 예 #1<blockquote>
</blockquote>
문제 예시와 같습니다.<blockquote>
</blockquote>
</li>
<li>입출력 예 #2<blockquote>
</blockquote>
</li>
<li>4+1-2+1 = 4</li>
<li>4-1+2-1 = 4
총 2가지 방법이 있으므로, 2를 return 합니다.</li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>numbers 배열 내의 숫자와 덧셈/뺄셈연산자를 사용해서 연산 수행</li>
<li>2 &lt;= numbers.length &lt;= 20, 1 &lt;= numbers[i] &lt;= 50, 1 &lt;= target &lt;= 1000</li>
<li>모든 연산 결과를 경우의 수로 나타내면 경우의 수는 $2^n$(n은 numbers.length) </li>
<li>dfs를 사용해서 모든 경우의 수를 완전 탐색<ul>
<li>dfs를 사용해서 완전탐색을 할 경우 최대 경우의 수는 $2^{20}$</li>
<li>모든 연산 결과에 대해 target과 일치하는지 확인하고 일치하는 수를 계산</li>
</ul>
</li>
</ul>
<br />    

<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>숫자 배열, 타겟 넘버, 깊이, 연산 결과를 매개변수로 받는 dfs 실행<ul>
<li>dfs 내에서 덧셈과 뺄셈 연산에 대해 각각 dfs를 재귀적으로 호출</li>
<li>재귀 호출의 종료 조건은 dfs의 탐색 깊이가 숫자 배열의 길이와 같을 경우(depth == numbers.length)<ul>
<li>이 때, 연산 결과와 타겟 넘버가 같은지 확인하고 같다면 1을, 다르다면 0을 return</li>
</ul>
</li>
<li>return 된 값은 dfs를 탈출하며 계속해서 count에 전달되어 더해짐</li>
<li>최초 호출된 dfs가 종료되면 모든 경우의 수에 대한 count를 답으로 return</li>
</ul>
</li>
</ul>
<br />

<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">class Solution {
    public int solution(int[] numbers, int target) {
        return dfs(numbers, target, 0, 0);
    }

    private int dfs(int[] numbers, int target, int depth, int sum) {
        if(depth == numbers.length) {
            return (target == sum) ? 1 : 0;
        }

        int count = 0;
        count += dfs(numbers, target, depth + 1, sum + numbers[depth]);
        count += dfs(numbers, target, depth + 1, sum - numbers[depth]);

        return count;
    }
}</code></pre>
<h4 id="참고">참고</h4>
<table>
<thead>
<tr>
<th>경우의 수</th>
<th>count 반환</th>
</tr>
</thead>
<tbody><tr>
<td><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/e1fb253c-30df-4538-9b34-a26cb09c9022/image.jpg" /></td>
<td><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/352228fc-2a85-4c33-9cf6-a013e3b6741b/image.jpg" /></td>
</tr>
</tbody></table>