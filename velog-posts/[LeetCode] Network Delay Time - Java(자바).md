<h2 id="문제">문제</h2>
<p>Network Delay Time(<a href="https://leetcode.com/problems/network-delay-time/submissions/1369959470/">https://leetcode.com/problems/network-delay-time/submissions/1369959470/</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>You are given a network of <code>n</code> nodes, labeled from <code>1</code> to <code>n</code>. You are also given <code>times</code>, a list of travel times as directed edges times[i] = ($$u_{i}$$, $$v_{i}$$, $$w_{i}$$), where $$u_{i}$$ is the source node, $$v_{i}$$ is the target node, and $$w_{i}$$ is the time it takes for a signal to travel from source to target.</p>
</blockquote>
<p>We will send a signal from a given node <code>k</code>. Return the <strong>minimum</strong> time it takes for all the <code>n</code> nodes to receive the signal. If it is impossible for all the <code>n</code> nodes to receive the signal, return <code>-1</code>.</p>
<blockquote>
<h4 id="문제-해석">문제 해석</h4>
</blockquote>
<ul>
<li>1~n개의 노드로 구성된 네트워크가 제공된다.</li>
<li>[출발 노드 번호, 도착 노드 번호, 걸리는 시간]이 저장된 2차원 배열 times도 제공된다.</li>
<li>노드 k에서 신호를 보낼 때, 모든 노드에 신호가 도달하는 최소 시간을 반환하라. 만약 모든 노드에 신호가 도달하는 것이 불가능하면 -1을 반환하라.</li>
</ul>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>1 &lt;= k &lt;= n &lt;= 100</li>
<li>1 &lt;= times.length &lt;= 6000</li>
<li>times[i].length == 3</li>
<li>1 &lt;= ui, vi &lt;= n</li>
<li>ui != vi</li>
<li>0 &lt;= wi &lt;= 100</li>
<li>All the pairs (ui, vi) are unique. (i.e., no multiple edges.)</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<p><strong>Example 1:</strong></p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/23da5d65-7770-4299-bc41-d70f69c0a709/image.png" /></p>
<blockquote>
</blockquote>
<ul>
<li><strong>Input:</strong> times = [[2, 1, 1], [2, 3, 1], [3, 4, 1]], n = 4, k = 2</li>
<li><strong>Output:</strong> 2<blockquote>
</blockquote>
</li>
<li><em>Example 2:*</em><blockquote>
</blockquote>
</li>
<li><strong>Input:</strong> times = [[1, 2, 1]], n = 2, k = 1</li>
<li><strong>Output:</strong> 1<blockquote>
</blockquote>
</li>
<li><em>Example 3:*</em><blockquote>
</blockquote>
</li>
<li><strong>Input:</strong> times = [[1, 2, 1]], n = 2, k = 2</li>
<li><strong>Output:</strong> -1</li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>times 배열은 노드와 노드 간의 간선에 대한 이동시간을 담은 배열<ul>
<li>해당 배열을 인접 리스트로 변환해 노드 별 정보를 저장하도록 한다.</li>
</ul>
</li>
<li>문제에서 요구하는 최소 시간은 다익스트라로 구한 노드 별로 도달하는 모든 시간 중 최대 시간과 같음<ul>
<li>다익스트라로 도출된 최대 시간이 모든 노드에 도달할 경우의 시간이 됨    </li>
</ul>
</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ol>
<li>출발/도착 노드와 이동 시간에 대한 배열을 인접 리스트로 변환</li>
<li>다익스트라 실행 시 먼저 각 노드에 도달할 때 걸리는 시간을 저장할 time 배열을 선언하고 모든 값을 Integer.MAX_VALUE로 초기화</li>
<li>우선 순위 큐를 초기화하고 큐에 시작 노드와, 소요시간 0을 주고 다익스트라 로직 시작<ul>
<li>dijkstra(): 현재 노드의 정보를 저장하고 현재 노드에서 접근할 수 있는 노드들에 대해 걸리는 시간이 기존에 저장한 시간보다 적게 걸릴 경우 distance 배열의 값을 갱신하고 큐에 해당 노드를 add</li>
</ul>
</li>
<li>다익스트라 실행 루프가 끝났을 경우 find 함수에 distance 배열과 노드의 수 n를 주고 실행<ul>
<li>find(): 배열 내에 MAX_VALUE 값이 있다면 -1(도달하지 못한 노드가 존재한다는 의미), 없다면 maxTime을 배열 내 최대값으로 갱신하고(배열이 모든 노드에 도달할 때 최소 시간을 저장해둔 것이므로 이 중 최대값은 모든 노드에 도달할 때의 시간을 의미) maxTime 반환</li>
</ul>
</li>
</ol>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int networkDelayTime(int[][] times, int n, int k) {
        Map&lt;Integer, List&lt;int[]&gt;&gt; graph = new HashMap&lt;&gt;();
        for (int i = 1; i &lt;= n; i++) {
            graph.put(i, new ArrayList&lt;&gt;());
        }

        for(int[] time : times) {
            // u -&gt; v 로 가는 경로와 가중치 w를 그래프에 추가
            graph.get(time[0]).add(new int[]{time[1], time[2]});
        }

        return dijkstra(graph, k, n);
    }

    private int dijkstra(Map&lt;Integer, List&lt;int[]&gt;&gt; graph, int start, int n) {
        int[] distance = new int[n + 1];
        Arrays.fill(distance, Integer.MAX_VALUE);
        distance[start] = 0;

        PriorityQueue&lt;int[]&gt; pq = new PriorityQueue&lt;&gt;(Comparator.comparing(a -&gt; a[1]));
        pq.add(new int[]{start, 0});

        while (!pq.isEmpty()) {
            int[] cur = pq.poll();
            int node = cur[0];
            int time = cur[1];

            if (time &gt; distance[node]) continue;

            // 인접 노드 확인
            for (int[] edge : graph.get(node)) {
                int nextNode = edge[0];
                int nextTime = time + edge[1];

                if (nextTime &lt; distance[nextNode]) {
                    distance[nextNode] = nextTime;
                    pq.add(new int[]{nextNode, nextTime});
                }
            }
        }
        return find(distance, n);
    }

    private int find(int[] distance, int n) {
        int maxTime = 0;
        for (int i = 1; i &lt;= n; i++) {
            if (distance[i] == Integer.MAX_VALUE) {
                return -1;
            }
            maxTime = Math.max(maxTime, distance[i]);
        }

        return maxTime;
    }
}</code></pre>