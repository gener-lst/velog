<h2 id="문제">문제</h2>
<p>게임 맵 최단거리(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/1844">https://school.programmers.co.kr/learn/courses/30/lessons/1844</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>ROR 게임은 두 팀으로 나누어서 진행하며, 상대 팀 진영을 먼저 파괴하면 이기는 게임입니다. 따라서, 각 팀은 상대 팀 진영에 최대한 빨리 도착하는 것이 유리합니다.</p>
</blockquote>
<p>지금부터 당신은 한 팀의 팀원이 되어 게임을 진행하려고 합니다. 다음은 5 x 5 크기의 맵에, 당신의 캐릭터가 (행: 1, 열: 1) 위치에 있고, 상대 팀 진영은 (행: 5, 열: 5) 위치에 있는 경우의 예시입니다.</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/6edb2268-a218-4c38-9f5b-1aed5badad40/image.PNG" /></p>
<blockquote>
</blockquote>
<p>위 그림에서 검은색 부분은 벽으로 막혀있어 갈 수 없는 길이며, 흰색 부분은 갈 수 있는 길입니다. 캐릭터가 움직일 때는 동, 서, 남, 북 방향으로 한 칸씩 이동하며, 게임 맵을 벗어난 길은 갈 수 없습니다.
아래 예시는 캐릭터가 상대 팀 진영으로 가는 두 가지 방법을 나타내고 있습니다.</p>
<blockquote>
</blockquote>
<ul>
<li>첫 번째 방법은 11개의 칸을 지나서 상대 팀 진영에 도착했습니다.
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/07dee400-2842-4361-a237-413b34d8fa37/image.PNG" /><blockquote>
</blockquote>
</li>
<li>두 번째 방법은 15개의 칸을 지나서 상대팀 진영에 도착했습니다.
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/b553839f-387a-4f94-9b4e-6debacef7bab/image.PNG" /><blockquote>
</blockquote>
위 예시에서는 첫 번째 방법보다 더 빠르게 상대팀 진영에 도착하는 방법은 없으므로, 이 방법이 상대 팀 진영으로 가는 가장 빠른 방법입니다.<blockquote>
</blockquote>
만약, 상대 팀이 자신의 팀 진영 주위에 벽을 세워두었다면 상대 팀 진영에 도착하지 못할 수도 있습니다. 예를 들어, 다음과 같은 경우에 당신의 캐릭터는 상대 팀 진영에 도착할 수 없습니다.<blockquote>
</blockquote>
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/637ab4f9-fc5a-4955-a8d4-f615255b2be4/image.PNG" /><blockquote>
</blockquote>
게임 맵의 상태 maps가 매개변수로 주어질 때, 캐릭터가 상대 팀 진영에 도착하기 위해서 지나가야 하는 칸의 개수의 최솟값을 return 하도록 solution 함수를 완성해주세요. 단, 상대 팀 진영에 도착할 수 없을 때는 -1을 return 해주세요.</li>
</ul>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>maps는 n x m 크기의 게임 맵의 상태가 들어있는 2차원 배열로, n과 m은 각각 1 이상 100 이하의 자연수입니다.<ul>
<li>n과 m은 서로 같을 수도, 다를 수도 있지만, n과 m이 모두 1인 경우는 입력으로 주어지지 않습니다.</li>
</ul>
</li>
<li>maps는 0과 1로만 이루어져 있으며, 0은 벽이 있는 자리, 1은 벽이 없는 자리를 나타냅니다.</li>
<li>처음에 캐릭터는 게임 맵의 좌측 상단인 (1, 1) 위치에 있으며, 상대방 진영은 게임 맵의 우측 하단인 (n, m) 위치에 있습니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<table>
<thead>
<tr>
<th align="left">maps</th>
<th align="left">answer</th>
</tr>
</thead>
<tbody><tr>
<td align="left">[[1,0,1,1,1],[1,0,1,0,1],[1,0,1,1,1],[1,1,1,0,1],[0,0,0,0,1]]</td>
<td align="left">11</td>
</tr>
<tr>
<td align="left">[[1,0,1,1,1],[1,0,1,0,1],[1,0,1,1,1],[1,1,1,0,0],[0,0,0,0,1]]</td>
<td align="left">-1</td>
</tr>
</tbody></table>
<blockquote>
<h4 id="입출력-예-설명">입출력 예 설명</h4>
<p>입출력 예 #1
주어진 데이터는 다음과 같습니다.</p>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/bb5ec3cc-4222-4eea-bda7-c935f0fcc14c/image.PNG" /></p>
<blockquote>
</blockquote>
<p>캐릭터가 적 팀의 진영까지 이동하는 가장 빠른 길은 다음 그림과 같습니다.</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/faaf3ff3-ef16-4e39-b792-4d9bf450c145/image.PNG" /></p>
<blockquote>
</blockquote>
<p>따라서 총 11칸을 캐릭터가 지나갔으므로 11을 return 하면 됩니다.</p>
<blockquote>
</blockquote>
<p>입출력 예 #2
문제의 예시와 같으며, 상대 팀 진영에 도달할 방법이 없습니다. 따라서 -1을 return 합니다.</p>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>주어진 진영 maps는 [n x m]의 2차원 배열이고, 1 &lt;= n, m &lt;= 100의 범위 내 자연 수</li>
<li>(1, 1)에서 출발하고 (n, m)에 도착할 때까지 최단거리를 구하는 문제<ul>
<li>최단거리 문제이므로 bfs를 사용해서 접근. 거리만 계산하면 되므로 2차원 배열에서 계산의 편의성을 위해 (0, 0)에서 (n-1, m-1)까지의 최단거리를 구하자.</li>
</ul>
</li>
</ul>
<br />    

<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>현재 위치에서 인접한 상하좌우 칸으로 접근하기 위한 방향 계산용 배열 dr/dc, maps의 행열 길이를 저장할 rowLength/colLength, 해당 칸의 방문여부를 저장할 2차원 배열 visited를 초기화</li>
<li>시작점 정보(행 좌표: 0, 열 좌표: 0, 거리: 1)를 queue에 예약하고 방문 표시 후 bfs 시작</li>
<li>루프 내에서 현재 위치의 상하좌우 칸이 유효한지 검사하고 방문한 적이 없는 칸이라면 해당 칸을 다음 칸으로 하는 bfs 실행을 위해 queue에 예약하고 방문 표시</li>
<li>bfs 루프의 종료 조건은 queue가 빌 경우 또는 도착점에 도착했을 경우<ul>
<li>queue가 비어있을 경우 접근할 수 있는 다음 칸이 없다는 의미이므로 루프에서 벗어나 -1을 return</li>
<li>현재 위치가 도착점이라면 현재 위치까지의 거리를 계산한 dist를 return -&gt; bfs로 실행했으므로 제일 먼저 도착한 시점의 dist가 최단거리가 됨</li>
</ul>
</li>
</ul>
<br />

<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int solution(int[][] maps) {
        int[] dr = {1, -1, 0, 0};
        int[] dc = {0, 0, 1, -1};
        int rowLength = maps.length;
        int colLength = maps[0].length;
        boolean[][] visited = new boolean[rowLength][colLength];

        Queue&lt;int[]&gt; queue = new ArrayDeque();
        queue.offer(new int[]{0,0,1});
        visited[0][0] = true;

        while(!queue.isEmpty()) {
            int[] cur = queue.poll();
            int r = cur[0];
            int c = cur[1];
            int dist = cur[2];

            if(r == rowLength - 1 &amp;&amp; c == colLength - 1) {
                return dist;
            }

            for(int i = 0; i &lt; 4; i++) {
                int nr = r + dr[i];
                int nc = c + dc[i];
                if(0 &lt;= nr &amp;&amp; nr &lt; rowLength &amp;&amp; 0 &lt;= nc &amp;&amp; nc &lt; colLength &amp;&amp; maps[nr][nc] == 1) {
                    if(!visited[nr][nc]) {
                        queue.offer(new int[]{nr, nc, dist + 1});
                        visited[nr][nc] = true;
                    }
                }
            }
        }
        return -1;
    }
}</code></pre>