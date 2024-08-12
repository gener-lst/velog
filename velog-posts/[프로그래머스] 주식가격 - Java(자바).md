<h2 id="문제">문제</h2>
<p>주식가격(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/42584">https://school.programmers.co.kr/learn/courses/30/lessons/42584</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>초 단위로 기록된 주식가격이 담긴 배열 prices가 매개변수로 주어질 때, 가격이 떨어지지 않은 기간은 몇 초인지를 return 하도록 solution 함수를 완성하세요.</p>
</blockquote>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>prices의 각 가격은 1 이상 10,000 이하인 자연수입니다.</li>
<li>prices의 길이는 2 이상 100,000 이하입니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<table>
<thead>
<tr>
<th align="left">prices</th>
<th align="left">return</th>
</tr>
</thead>
<tbody><tr>
<td align="left">[1, 2, 3, 2, 3]</td>
<td align="left">[4, 3, 1, 1, 0]</td>
</tr>
</tbody></table>
<blockquote>
<h4 id="입출력-예-설명">입출력 예 설명</h4>
</blockquote>
<ul>
<li>1초 시점의 ₩1은 끝까지 가격이 떨어지지 않았습니다.</li>
<li>2초 시점의 ₩2은 끝까지 가격이 떨어지지 않았습니다.</li>
<li>3초 시점의 ₩3은 1초뒤에 가격이 떨어집니다. 따라서 1초간 가격이 떨어지지 않은 것으로 봅니다.</li>
<li>4초 시점의 ₩2은 1초간 가격이 떨어지지 않았습니다.</li>
<li>5초 시점의 ₩3은 0초간 가격이 떨어지지 않았습니다.</li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>주어진 배열 prices에 대해: 1 &lt;= prices[i] &lt;= $10^4$, 2 &lt;= prices.length &lt;= $10^5$</li>
<li>이중 for문으로 접근할 경우: 각 초별 시점(index)에서의 가격을 서로 비교하고 비교 횟수만큼 count한 값을 배열로 저장하고 반환한다.</li>
<li>stack으로 접근할 경우: 각 초별 시점(index)에서의 가격을 앞 순번부터 stack에 저장하고 다음 시점의 가격과 크기 비교 후 시점 차이(stack 내의 index 차이)에 대한 값을 배열에 저장하고 반환한다.</li>
</ul>
<br />    

<h3 id="접근-방법">접근 방법</h3>
<h4 id="이중-for-문">이중 for 문</h4>
<ul>
<li>이중 for문 내에서 각 초별 시점을 index(i, j)로 가정하고 해당 시점의 가격을 for문을 돌며 서로 비교</li>
<li>가격하락이 없는 기간을 초로 표현하기 위해 answer[i]에 값을 증가</li>
<li>j시점의 가격이 i시점의 가격보다 낮아질 경우 break를 통해 가격이 떨어지지 않은 기간을 현재 값으로 확정</li>
</ul>
<h4 id="stack-활용">stack 활용</h4>
<ul>
<li>for문 내에서 각 초별 시점을 index(i)로 가정하고 0을 push하고 반복문 시작</li>
<li>반복문의 이전 단계에서 push된 stack의 맨 위 index(j)의 가격과 i번째 index의 가격을 비교하고 stack 맨 위 저장된 index의 가격이 더 클 경우 i와 j의 차이를 answer 배열에 저장하고 stack.pop(). 아니라면 while 문을 빠져나와 for문의 다음 단계로 이동 </li>
<li>for문 종료 후에도 stack이 비어있지 않으면 stack에 저장된 남은 index 값들에 대해 계산 후 answer 배열에 저장</li>
</ul>
<br />

<h3 id="코드-구현">코드 구현</h3>
<h4 id="이중-for문">이중 for문</h4>
<pre><code class="language-java">class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];

        for (int i = 0; i &lt; prices.length; i++) {
            for (int j = i + 1; j &lt; prices.length; j++) {
                answer[i]++;
                if (prices[i] &gt; prices[j]) {
                    break;
                }
            }
        }
        return answer;
    }
}</code></pre>
<h4 id="stack-활용-1">stack 활용</h4>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int[] solution(int[] prices) {
        int[] answer = new int[prices.length];
        Deque&lt;Integer&gt; stack = new ArrayDeque&lt;&gt;();

        for (int i = 0; i &lt; prices.length; i++) {
            while (!stack.isEmpty()) {
                int j = stack.peek();
                if (prices[j] &gt; prices[i]) {
                    answer[j] = i - j;
                    stack.pop();
                } 
                else break;
            }

            stack.push(i);
        }

        while (!stack.isEmpty()) {
            int i = stack.pop();
            answer[i] = prices.length - i - 1;
        }

        return answer;
    }
}</code></pre>