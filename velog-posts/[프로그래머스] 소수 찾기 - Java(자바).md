<h2 id="문제">문제</h2>
<p>소수 찾기(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/42839">https://school.programmers.co.kr/learn/courses/30/lessons/42839</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.</p>
</blockquote>
<p>각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.</p>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>numbers는 길이 1 이상 7 이하인 문자열입니다.</li>
<li>numbers는 0~9까지 숫자만으로 이루어져 있습니다.</li>
<li>&quot;013&quot;은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
<table>
<thead>
<tr>
<th align="left">numbers</th>
<th align="left">return</th>
</tr>
</thead>
<tbody><tr>
<td align="left">&quot;17&quot;</td>
<td align="left">3</td>
</tr>
<tr>
<td align="left">&quot;011&quot;</td>
<td align="left">2</td>
</tr>
<tr>
<td align="left">#### 입출력 예 설명</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">예제 #1</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">[1, 7]으로는 소수 [7, 17, 71]를 만들 수 있습니다.</td>
<td align="left"></td>
</tr>
</tbody></table>
</blockquote>
<p>예제 #2
[0, 1, 1]으로는 소수 [11, 101]를 만들 수 있습니다.</p>
<ul>
<li>11과 011은 같은 숫자로 취급합니다.</li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>숫자들을 조합하여 만들 수 있는 소수가 몇개인지 알아내는 문제</li>
</ul>
<ol>
<li>숫자를 조합하기 : 재귀를 이용하여 순열 구하는 방식으로 구현</li>
<li>소수를 판별하기 :  $2$ ~ $\sqrt{M}$ 사이의 값들로 숫자 $M$을 나눠서 하나라도 나누어 떨어지는 숫자가 있는지 확인하는 방식으로 구현</li>
</ol>
<br />    

<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>방문 여부 판단하는 visited, 조합할 수 있는 모든 수를 저장하는 ans 선언</li>
</ul>
<ol>
<li>solution 함수: visited, ans, 소수의 수를 저장할 answer를 초기화. dfs를 통해 ans를 완성하고 ans 전체 수에 대해 소수인지 isPrime으로 검사하고 소수이면 answer++. </li>
<li>dfs 함수: numbers의 길이 만큼 for문을 돌리면서 해당 index의 자리 수를 더한 문자열을 int 타입으로 바꾸고 ans에 중복없이 추가. dfs를 재귀호출하며 끝까지 수행 후 방문여부를 false로 바꾸고 backTracking. 재귀 호출 종료 조건으로 dfs의 호출횟수(즉, 문자열 자리수 추가 횟수) &gt; numbers 문자열의 길이를 둠</li>
<li>isPrime 함수: 주어진 수 num에 대해 소수인지 판단 → 2보다 작다면 소수x, 2부터 <strong>√</strong>num보다 작은 자연수 i까지의 범위에 대해 num이 i로 나머지 없이 나눠진다면 소수x. 위 조건을 통과하면 true 반환<br />

</li>
</ol>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.ArrayList;

class Solution {
    public static boolean[] visited;
    public static ArrayList&lt;Integer&gt; ans;
    public int solution(String numbers) {
        visited = new boolean[7];
        ans = new ArrayList&lt;&gt;();
        int answer = 0;

        dfs(0, numbers, &quot;&quot;);

        for (Integer num : ans) {
            if (isPrime(num)) {
                answer++;
            }
        }
        return answer;
    }

    public void dfs(int depth, String numbers, String s) {
        if (depth &gt; numbers.length()) {
            return;
        }

        for (int i = 0; i &lt; numbers.length(); i++) {
            if(!visited[i]) {
                visited[i] = true;
               int next = Integer.parseInt(s + numbers.charAt(i));
                if (!ans.contains(next)) {
                    ans.add(next);
                }
                dfs(depth + 1, numbers, s + numbers.charAt(i));
                visited[i] = false;
            }
        }
    }

    private boolean isPrime(int num) {
        if (num &lt; 2) {
            return false;
        }
         for (int i = 2; i * i &lt;= num; i++) {
            if (num % i == 0) {
                return false;
            }
        }

        return true;
    }
}</code></pre>