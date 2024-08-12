<h2 id="문제">문제</h2>
<p>게임 맵 최단거리(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/49189">https://school.programmers.co.kr/learn/courses/30/lessons/49189</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>n개의 노드가 있는 그래프가 있습니다. 각 노드는 1부터 n까지 번호가 적혀있습니다. 1번 노드에서 가장 멀리 떨어진 노드의 갯수를 구하려고 합니다. 가장 멀리 떨어진 노드란 최단경로로 이동했을 때 간선의 개수가 가장 많은 노드들을 의미합니다.
노드의 개수 n, 간선에 대한 정보가 담긴 2차원 배열 vertex가 매개변수로 주어질 때, 1번 노드로부터 가장 멀리 떨어진 노드가 몇 개인지를 return 하도록 solution 함수를 작성해주세요.</p>
</blockquote>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>노드의 개수 n은 2 이상 20,000 이하입니다.</li>
<li>간선은 양방향이며 총 1개 이상 50,000개 이하의 간선이 있습니다.</li>
<li>vertex 배열 각 행 [a, b]는 a번 노드와 b번 노드 사이에 간선이 있다는 의미입니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<table>
<thead>
<tr>
<th align="left">n</th>
<th align="left">vertex</th>
<th align="left">return</th>
</tr>
</thead>
<tbody><tr>
<td align="left">6</td>
<td align="left">[[3, 6], [4, 3], [3, 2], [1, 3], [1, 2], [2, 4], [5, 2]]</td>
<td align="left">3</td>
</tr>
</tbody></table>
<blockquote>
<h4 id="입출력-예-설명">입출력 예 설명</h4>
<p>예제의 그래프를 표현하면 아래 그림과 같고, 1번 노드에서 가장 멀리 떨어진 노드는 4,5,6번 노드입니다.
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/542ce1b1-4fec-4b2d-a3d1-940425f0e6e8/image.PNG" /></p>
</blockquote>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>문제에서 주어진 정보는 노드의 개수(n)과 간선의 정보를 담은 배열(edge)</li>
<li>간선의 배열(edge)을 노드 간의 연결 정보를 담은 배열로 변환하여 인접 리스트로 문제를 풀이</li>
<li>1번 노드를 출발점이라고 가정할 때 출발점에서 각 노드까지의 최단거리를 구해야 하므로 bfs로 풀이</li>
<li>각 노드까지의 최단거리를 모두 구하고 이 중 가장 큰 값이 몇 개 존재하는지 count하고 반환</li>
</ul>
<br />    

<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>인접 리스트를 담을 graph와 방문여부를 담을 visited를 해시맵으로 초기화</li>
<li>노드의 개수(n)과 간선의 배열(edge)를 이용하여 graph에 각 노드 별 정보를 추가하여 인접 리스트로 변환 후 bfs 실행</li>
<li>bfs: <ol>
<li>queue와 최대 거리를 저장할 변수 maxDist, 최대 거리인 노드의 개수를 저장할 변수 count를 초기화</li>
<li>시작 노드인 1과 현재 거리인 0을 queue에 예약하고 방문 표시 후 bfs 루프 시작</li>
<li>현재 노드까지의 거리(dist)가 최대 거리(maxDist)보다 크다면, maxDist를 dist로 갱신. maxDist와 dist가 같다면, count를 1 증가 </li>
<li>인접 리스트에서 현재 노드와 인접한 노드에 방문한 적 있는지 확인 후 방문한 적이 없다면 방문 표시 후 queue에 해당 노드와 거리 + 1을 예약<ol start="5">
<li>모든 노드를 탐색 후 루프가 종료되면 count를 return</li>
</ol>
</li>
</ol>
</li>
</ul>
<br />

<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

public class Solution {
    Map&lt;Integer, List&lt;Integer&gt;&gt; graph = new HashMap&lt;&gt;();
    Map&lt;Integer, Boolean&gt; visited = new HashMap&lt;&gt;();

    public int solution(int n, int[][] edge) {
        for (int i = 1; i &lt;= n; i++) {
            graph.put(i, new ArrayList&lt;&gt;());
            visited.put(i, false);
        }
        for (int[] e : edge) {
            graph.get(e[0]).add(e[1]);
            graph.get(e[1]).add(e[0]);
        }

        return bfs(1);
    }

    private int bfs(int node) {
       Queue&lt;int[]&gt; queue = new ArrayDeque&lt;&gt;();
       queue.offer(new int[]{node, 0});
       visited.put(node, true);

       int maxDist = 0;
       int count = 0;

       while (!queue.isEmpty()) {
           int cur[] = queue.poll();
           int curVertex = cur[0];
           int dist = cur[1];

           if(maxDist &lt; dist) {
               maxDist = dist;
               count = 1;
           } else if(maxDist == dist) count ++;

           for(int nextVertex: graph.get(curVertex)) {
               if(!visited.get(nextVertex)) {
                   visited.put(nextVertex, true);
                   queue.offer(new int[]{nextVertex, dist + 1});
               }
           }
       }

       return count;
    }
}</code></pre>