<h2 id="문제">문제</h2>
<p>보물 지도(<a href="https://school.programmers.co.kr/learn/courses/15009/lessons/121690">https://school.programmers.co.kr/learn/courses/15009/lessons/121690</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>진수는 보물이 묻힌 장소와 함정이 표시된 보물 지도를 이용해 보물을 찾으려 합니다. 보물지도는 가로 길이가 <code>n</code>, 세로 길이가 <code>m</code>인 직사각형 모양입니다.</p>
</blockquote>
<p>맨 왼쪽 아래 칸의 좌표를 (1, 1)으로, 맨 오른쪽 위 칸의 좌표를 (n, m)으로 나타냈을 때, 보물은 (n, m) 좌표에 묻혀있습니다. 또한, 일부 칸에는 함정이 있으며, 해당 칸으로는 지나갈 수 없습니다.</p>
<blockquote>
</blockquote>
<p>진수는 처음에 (1, 1) 좌표에서 출발해 보물이 있는 칸으로 이동하려 합니다. 이동할 때는 [상,하,좌,우]로 인접한 네 칸 중 한 칸으로 걸어서 이동합니다. 한 칸을 걸어서 이동하는 데 걸리는 시간은 1입니다.</p>
<blockquote>
</blockquote>
<p>진수는 보물이 위치한 칸으로 수월하게 이동하기 위해 신비로운 신발을 하나 준비했습니다. 이 신발을 신고 뛰면 한 번에 두 칸을 이동할 수 있으며, 함정이 있는 칸도 넘을 수 있습니다. 하지만, 이 신발은 한 번밖에 사용할 수 없습니다. 신비로운 신발을 사용하여 뛰어서 두 칸을 이동하는 시간도 1입니다.</p>
<blockquote>
</blockquote>
<p>이때 진수가 출발점에서 보물이 위치한 칸으로 이동하는데 필요한 최소 시간을 구해야 합니다.</p>
<blockquote>
</blockquote>
<p>예를 들어, 진수의 보물지도가 아래 그림과 같을 때, 진수가 걸어서 오른쪽으로 3칸, 걸어서 위쪽으로 3칸 이동하면 6의 시간에 보물이 위치한 칸으로 이동할 수 있습니다. 만약, 오른쪽으로 걸어서 1칸, 위쪽으로 걸어서 1칸, 신비로운 신발을 사용하여 위로 뛰어 2칸, 오른쪽으로 걸어서 2칸 이동한다면 총 5의 시간에 보물이 위치한 칸으로 이동할 수 있으며, 이보다 빠른 시간 내에 보물이 있는 위치에 도착할 수 없습니다.</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/bae66b7d-5ad7-40fa-a581-af5e47e4d1ed/image.PNG" /></p>
<blockquote>
</blockquote>
<p>진수의 보물지도가 표현하는 지역의 가로 길이를 나타내는 정수 <code>n</code>, 세로 길이를 나타내는 정수 <code>m</code>, 함정의 위치를 나타내는 2차원 정수 배열 <code>hole</code>이 주어졌을 때, 진수가 보물이 있는 칸으로 이동하는데 필요한 최소 시간을 return 하는 solution 함수를 완성해주세요. <strong>단, 보물이 있는 칸으로 이동할 수 없다면, -1을 return 해야 합니다.</strong></p>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>1 ≤ n, m ≤ 1,000<ul>
<li>단, n * m이 3 이상인 경우만 입력으로 주어집니다.</li>
</ul>
</li>
<li>1 ≤ hole의 길이 ≤ n * m - 2<ul>
<li>hole[i]는 [a, b]의 형태이며, (a, b) 칸에 함정이 존재한다는 의미이며, 1 ≤ a ≤ n, 1 ≤ b ≤ m을 만족합니다.</li>
<li>같은 함정에 대한 정보가 중복해서 들어있지 않습니다.</li>
</ul>
</li>
<li>(1, 1) 칸과 (n, m) 칸은 항상 함정이 없습니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<table>
<thead>
<tr>
<th align="left">n</th>
<th align="left">m</th>
<th align="left">hole</th>
<th align="left">result</th>
</tr>
</thead>
<tbody><tr>
<td align="left">4</td>
<td align="left">4</td>
<td align="left">[[2, 3], [3, 3]]</td>
<td align="left">5</td>
</tr>
<tr>
<td align="left">5</td>
<td align="left">4</td>
<td align="left">[[1, 4], [2, 1], [2, 2], [2, 3], [2, 4], [3, 3], [4, 1], [4, 3], [5, 3]]</td>
<td align="left">-1</td>
</tr>
</tbody></table>
<blockquote>
<h4 id="입출력-예-설명">입출력 예 설명</h4>
<p>입출력 예 #1</p>
</blockquote>
<ul>
<li>본문의 예시와 같습니다.<blockquote>
</blockquote>
입출력 예 #2</li>
<li>보물지도를 그림으로 나타내면 아래와 같으며, 보물이 위치한 칸으로 이동할 수 없습니다. 따라서, -1을 return 해야 합니다.
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/87e31045-faa9-45be-80e2-aabce41921c0/image.PNG" /></li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>[n x m] 크기의 보물지도에서 (1, 1)에서부터 (n, m)까지 최단거리를 구하라<ul>
<li>최단거리를 구하는 문제이므로 bfs를 사용하여 풀이</li>
</ul>
</li>
<li>한 방향으로 한 번에 2칸을 이동할 수 있는 신발을 탐색하는 동안 한 번 사용 가능하다.<ul>
<li>함정으로 인해 도착까지 신발을 사용할 수 없는 경우가 아니라면 신발이 무조건 사용될 것이다.</li>
<li>신발 사용 여부에 따라 이동 범위가 달라지므로 신발 사용 여부를 저장하고 bfs 내에서 전달해야 한다.</li>
</ul>
</li>
<li>함정이 있는 칸은 기본적으로 지나갈 수 없지만, 신비로운 신발을 사용하면 1칸의 함정은 뛰어넘을 수 있다.</li>
<li>bfs 내에서 신발의 이동 범위를 포함한 경우의 수를 모두 실행하여 최단거리 도출<br />    

</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>bfs 내에서 다음 칸에 함정이 위치하는지 여부를 확인하기 위해서 함정의 위치 배열(int[][] hole)을 위치 별 함정 여부를 나타내는 배열(boolean[][] trap)로 변환</li>
<li>visited는 3차원 배열로 선언하여 방문 여부와 신발 사용 여부를 모두 저장한다.(같은 칸에 방문하더라도 신발 사용 여부에 따라 다른 경우의 수가 됨)</li>
<li>dr, dc 배열은 신발의 이동 범위까지 고려하여 다음 칸을 상하좌우로 1 ~ 2칸으로 설정할 수 있도록 초기화한다.</li>
<li>bfs():  <ul>
<li>시작점 정보를 queue에 add하며 bfs 실행 시작</li>
<li>현재 위치 정보를 저장하고, 신발을 사용했는지 여부에 따라 다음 칸을 지정하는 for문 내 인덱스 범위를 4 또는 8로 설정<ul>
<li>해당 인덱스 범위에 따라 다음 칸에 저장될 신발 사용 여부(nj)도 달라짐 </li>
</ul>
</li>
<li>다음 칸이 지도 내의 범위에 존재하고 방문 여부와 함정이 없다면 다음 칸에 대한 방문 여부를 true로 저장하고 queue에 다음 칸을 add</li>
<li>bfs 루프의 종료 조건은 현재 칸이 도착점(n, m)일 경우이며 해당 칸까지의 거리(dist)를 반환한다.</li>
<li>도착점에 도착하지 못할 경우(= 종료 조건에 도달하지 못하고 queue가 빌 경우) -1을 반환한다.</li>
</ul>
</li>
</ul>
<br />

<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int solution(int n, int m, int[][] hole) {
        boolean[][] trap = new boolean[n+1][m+1];
        for (int[] h : hole) {
            trap[h[0]][h[1]] = true;
        }

        boolean[][][] visited = new boolean[n+1][m+1][2];
        Queue&lt;int[]&gt; queue = new ArrayDeque&lt;&gt;();
        visited[1][1][0] = true;
        queue.add(new int[]{ 1, 1, 0, 0 });

        int[] dr = { 0, 1, 0, -1, 0, 2, 0, -2 };
        int[] dc = { 1, 0, -1, 0, 2, 0, -2, 0 };

        while (!queue.isEmpty()) {
            int[] cur = queue.remove();
            int r = cur[0], c = cur[1], jumped = cur[2], dist = cur[3];

            if (r == n &amp;&amp; c == m) return dist;

            for (int d = 0; d &lt; ((jumped == 1) ? 4 : 8); d++) {
                int nr = r + dr[d], nc = c + dc[d];
                int nj = (jumped == 1) ? 1 : (d / 4);

                if (nr &gt;= 1 &amp;&amp; nr &lt;= n &amp;&amp; nc &gt;= 1 &amp;&amp; nc &lt;= m) {
                    if (!visited[nr][nc][nj] &amp;&amp; !trap[nr][nc]) {
                        visited[nr][nc][nj] = true;
                        queue.add(new int[]{ nr, nc, nj, dist + 1 });
                    }
                }
            }
        }
        return -1;
    }
}</code></pre>