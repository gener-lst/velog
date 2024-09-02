<h2 id="문제">문제</h2>
<p>전력망 둘로 나누기(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/86971">https://school.programmers.co.kr/learn/courses/30/lessons/86971</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>n개의 송전탑이 전선을 통해 하나의 트리 형태로 연결되어 있습니다. 당신은 이 전선들 중 하나를 끊어서 현재의 전력망 네트워크를 2개로 분할하려고 합니다. 이때, 두 전력망이 갖게 되는 송전탑의 개수를 최대한 비슷하게 맞추고자 합니다.</p>
</blockquote>
<p>송전탑의 개수 n, 그리고 전선 정보 wires가 매개변수로 주어집니다. 전선들 중 하나를 끊어서 송전탑 개수가 가능한 비슷하도록 두 전력망으로 나누었을 때, 두 전력망이 가지고 있는 송전탑 개수의 차이(절대값)를 return 하도록 solution 함수를 완성해주세요.</p>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>n은 2 이상 100 이하인 자연수입니다.</li>
<li>wires는 길이가 <code>n-1</code>인 정수형 2차원 배열입니다.<ul>
<li>wires의 각 원소는 [v1, v2] 2개의 자연수로 이루어져 있으며, 이는 전력망의 v1번 송전탑과 v2번 송전탑이 전선으로 연결되어 있다는 것을 의미합니다.</li>
<li>1 ≤ v1 &lt; v2 ≤ n 입니다.
전력망 네트워크가 하나의 트리 형태가 아닌 경우는 입력으로 주어지지 않습니다.</li>
</ul>
</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
<table>
<thead>
<tr>
<th align="left">n</th>
<th align="left">wires</th>
<th align="left">result</th>
</tr>
</thead>
<tbody><tr>
<td align="left">9</td>
<td align="left">[[1,3],[2,3],[3,4],[4,5],[4,6],[4,7],[7,8],[7,9]]</td>
<td align="left">3</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">[[1,2],[2,3],[3,4]]</td>
<td align="left">0</td>
</tr>
<tr>
<td align="left">7</td>
<td align="left">[[1,2],[2,7],[3,7],[3,4],[4,5],[6,7]]</td>
<td align="left">1</td>
</tr>
<tr>
<td align="left">#### 입출력 예 설명</td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">입출력 예 #1</td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
</blockquote>
<ul>
<li>다음 그림은 주어진 입력을 해결하는 방법 중 하나를 나타낸 것입니다.<blockquote>
</blockquote>
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/96ac69e5-2bf1-45df-aa8a-5c858774b48a/image.PNG" /><blockquote>
</blockquote>
</li>
<li>4번과 7번을 연결하는 전선을 끊으면 두 전력망은 각 6개와 3개의 송전탑을 가지며, 이보다 더 비슷한 개수로 전력망을 나눌 수 없습니다.</li>
<li>또 다른 방법으로는 3번과 4번을 연결하는 전선을 끊어도 최선의 정답을 도출할 수 있습니다.<blockquote>
</blockquote>
입출력 예 #2</li>
<li>다음 그림은 주어진 입력을 해결하는 방법을 나타낸 것입니다.<blockquote>
</blockquote>
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/88577229-72e7-4f55-8dd1-e5dbe35c2e35/image.PNG" /><blockquote>
</blockquote>
</li>
<li>2번과 3번을 연결하는 전선을 끊으면 두 전력망이 모두 2개의 송전탑을 가지게 되며, 이 방법이 최선입니다.<blockquote>
</blockquote>
입출력 예 #3</li>
<li>다음 그림은 주어진 입력을 해결하는 방법을 나타낸 것입니다.<blockquote>
</blockquote>
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/41f7f153-c5c5-4bfc-a4b4-d744d5977d86/image.PNG" /><blockquote>
</blockquote>
</li>
<li>3번과 7번을 연결하는 전선을 끊으면 두 전력망이 각각 4개와 3개의 송전탑을 가지게 되며, 이 방법이 최선입니다.</li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>트리 구조로 연결된 송전탑을 최대한 비슷하게 2개의 부분으로 나누어야 함</li>
<li>간선 하나를 제거하였을 때 2개의 부분을 구성하는 노드의 개수 차이가 최소한으로 나도록 하는 경우의 수를 도출</li>
<li>트리 구조에서 탐색을 수행하면 부모 노드에서 자식 노드 순으로 탐색이 된다는 특징을 이용하여 간선을 제거하고 DFS를 수행하여 해당 부분의 노드 개수를 도출</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>주어진 간선에 대한 배열 wires를 해시맵 형태의 인접 리스트로 변형</li>
<li>각 경우의 수 도출을 위한 DFS 수행</li>
</ul>
<ol>
<li>인접 리스트 내 각 노드에 접근하여 간선을 직접 제거 후 dfs 실행</li>
<li>dfs 내에서 방문 여부를 체크하며 다음 노드를 방문하며 count++</li>
<li>dfs에서 계산한 count와 (전체 노드(n) - count)의 차이를 계산하고 기존의 min과 비교하여 갱신<ul>
<li>이 때, 간선을 제거해도 두 묶음으로 나뉘지 않는다면, dfs는 모든 노드를 다 돌고 count는 9가 됨</li>
</ul>
</li>
<li>제거한 간선 복구 후 다음 간선 제거(간선 개수 만큼 반복)</li>
</ol>
<ul>
<li>모든 노드에 대해 위 과정을 반복 후 최종적으로 갱신된 min을 답으로 반환<br />

</li>
</ul>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int solution(int n, int[][] wires) {
        Map&lt;Integer, List&lt;Integer&gt;&gt; graph = new HashMap&lt;&gt;();
        int min = n;

        for (int i = 1; i &lt;= n; i++) {
            graph.put(i, new ArrayList&lt;&gt;());
        }
        for (int[] e : wires) {
            graph.get(e[0]).add(e[1]);
            graph.get(e[1]).add(e[0]);
        }

        for (int[] e : wires) {
            int v1 = e[0];
            int v2 = e[1];

            boolean[] visited = new boolean[n + 1];

            graph.get(v1).remove(Integer.valueOf(v2));
            graph.get(v2).remove(Integer.valueOf(v1));

            int count = dfs(graph, 1, visited);

            int diff = Math.abs(count - (n - count));
            min = Math.min(min, diff);

            graph.get(v1).add(v2);
            graph.get(v2).add(v1);
        }
        return min;
    }

    private int dfs(Map&lt;Integer, List&lt;Integer&gt;&gt; graph, int v, boolean[] visited) {
        visited[v] = true;
        int count = 1;

        for (int next : graph.get(v)) {
            if (!visited[next]) {
                count += dfs(graph, next, visited);
            }
        }

        return count;
    }
}</code></pre>