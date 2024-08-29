<h2 id="문제">문제</h2>
<p>네트워크(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/43162">https://school.programmers.co.kr/learn/courses/30/lessons/43162</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>네트워크란 컴퓨터 상호 간에 정보를 교환할 수 있도록 연결된 형태를 의미합니다. 예를 들어, 컴퓨터 A와 컴퓨터 B가 직접적으로 연결되어있고, 컴퓨터 B와 컴퓨터 C가 직접적으로 연결되어 있을 때 컴퓨터 A와 컴퓨터 C도 간접적으로 연결되어 정보를 교환할 수 있습니다. 따라서 컴퓨터 A, B, C는 모두 같은 네트워크 상에 있다고 할 수 있습니다.</p>
</blockquote>
<p>컴퓨터의 개수 n, 연결에 대한 정보가 담긴 2차원 배열 computers가 매개변수로 주어질 때, 네트워크의 개수를 return 하도록 solution 함수를 작성하시오.</p>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>컴퓨터의 개수 n은 1 이상 200 이하인 자연수입니다.</li>
<li>각 컴퓨터는 0부터 <code>n-1</code>인 정수로 표현합니다.</li>
<li>i번 컴퓨터와 j번 컴퓨터가 연결되어 있으면 computers[i][j]를 1로 표현합니다.</li>
<li>computer[i][i]는 항상 1입니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
<table>
<thead>
<tr>
<th align="left">n</th>
<th align="left">computers</th>
<th align="left">return</th>
</tr>
</thead>
<tbody><tr>
<td align="left">3</td>
<td align="left">[[1, 1, 0], [1, 1, 0], [0, 0, 1]]</td>
<td align="left">2</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">[[1, 1, 0], [1, 1, 1], [0, 1, 1]]</td>
<td align="left">1</td>
</tr>
<tr>
<td align="left">#### 입출력 예 설명</td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">예제 #1</td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">아래와 같이 2개의 네트워크가 있습니다.</td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/965a1c75-b372-4743-bef9-dfc9765dde00/image.PNG" /></p>
<blockquote>
</blockquote>
<p>예제 #2
아래와 같이 1개의 네트워크가 있습니다.</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/1057b906-f198-4c71-9584-36ed82fa3a14/image.PNG" /></p>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>노드의 개수와 간선의 정보가 주어진 문제에서 개별 네트워크의 개수를 구하라<ul>
<li>간선으로 연결되지 않은 노드의 집합을 개별 네트워크로 본다.</li>
</ul>
</li>
<li>dfs을 통해 연결된 모든 노드에 방문했음에도 방문하지 않은 노드가 존재한다면 다른 네트워크가 존재한다는 의미<ul>
<li>방문하지 않은 노드로부터 dfs 추가 실행</li>
</ul>
</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ol>
<li>방문 여부를 저장할 visited 배열을 초기화 후 false로 다 채움. for문 내 dfs 실행</li>
<li>dfs(): 현재 노드에 방문 여부를 true로 저장하고, 해당 노드와 연결된 다른 노드에 방문 여부를 확인하고 dfs 함수의 인자로 전달. 완전 탐색 후 solution 함수로 돌아감</li>
<li>for문 내에서 방문을 안 한 노드가 아직도 존재한다면, 네트워크의 개수를 1 추가하고, 해당 노드에 대해 dfs 추가로 실행</li>
<li>방문을 안 한 노드가 없을 때까지 로직 반복 후 네트워크 개수인 answer를 반환<br />

</li>
</ol>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int solution(int n, int[][] computers) {
        int answer = 0;
        boolean[] visited = new boolean[computers.length];

        Arrays.fill(visited, false);

        for(int i = 0; i &lt; computers.length; i++){
            if(visited[i] == false){
                answer++;
                dfs(i, visited, computers);
            }
        }
        return answer;
    }

    public void dfs(int node, boolean[] visited, int[][] computers){
        visited[node] = true;

        for(int i = 0; i &lt; computers.length; i++){
            if(visited[i] == false &amp;&amp; computers[node][i] == 1){
                dfs(i, visited, computers);
            }
        }
    }
}</code></pre>