<h2 id="문제">문제</h2>
<p>미로 탈출(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/159993">https://school.programmers.co.kr/learn/courses/30/lessons/159993</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>1 x 1 크기의 칸들로 이루어진 직사각형 격자 형태의 미로에서 탈출하려고 합니다. 각 칸은 통로 또는 벽으로 구성되어 있으며, 벽으로 된 칸은 지나갈 수 없고 통로로 된 칸으로만 이동할 수 있습니다. 통로들 중 한 칸에는 미로를 빠져나가는 문이 있는데, 이 문은 레버를 당겨서만 열 수 있습니다. 레버 또한 통로들 중 한 칸에 있습니다. 따라서, 출발 지점에서 먼저 레버가 있는 칸으로 이동하여 레버를 당긴 후 미로를 빠져나가는 문이 있는 칸으로 이동하면 됩니다. 이때 아직 레버를 당기지 않았더라도 출구가 있는 칸을 지나갈 수 있습니다. 미로에서 한 칸을 이동하는데 1초가 걸린다고 할 때, 최대한 빠르게 미로를 빠져나가는데 걸리는 시간을 구하려 합니다.</p>
</blockquote>
<p>미로를 나타낸 문자열 배열 <code>maps</code>가 매개변수로 주어질 때, 미로를 탈출하는데 필요한 최소 시간을 return 하는 solution 함수를 완성해주세요. 만약, 탈출할 수 없다면 -1을 return 해주세요.</p>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>5 ≤ <code>maps</code>의 길이 ≤ 100</li>
<li>5 ≤ <code>maps[i]</code>의 길이 ≤ 100<ul>
<li><code>maps[i]</code>는 다음 5개의 문자들로만 이루어져 있습니다.    <ul>
<li>S : 시작 지점</li>
<li>E : 출구</li>
<li>L : 레버</li>
<li>O : 통로</li>
<li>X : 벽</li>
</ul>
</li>
<li>시작 지점과 출구, 레버는 항상 다른 곳에 존재하며 한 개씩만 존재합니다.</li>
<li>출구는 레버가 당겨지지 않아도 지나갈 수 있으며, 모든 통로, 출구, 레버, 시작점은 여러 번 지나갈 수 있습니다.</li>
</ul>
</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
<table>
<thead>
<tr>
<th align="left">maps</th>
<th align="left">result</th>
</tr>
</thead>
<tbody><tr>
<td align="left">[&quot;SOOOL&quot;,&quot;XXXXO&quot;,&quot;OOOOO&quot;,&quot;OXXXX&quot;,&quot;OOOOE&quot;]</td>
<td align="left">16</td>
</tr>
<tr>
<td align="left">[&quot;LOOXS&quot;,&quot;OOOOX&quot;,&quot;OOOOO&quot;,&quot;OOOOO&quot;,&quot;EOOOO&quot;]</td>
<td align="left">-1</td>
</tr>
<tr>
<td align="left">#### 입출력 예 설명</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">입출력 예 #1</td>
<td align="left"></td>
</tr>
</tbody></table>
</blockquote>
<p>주어진 문자열은 다음과 같은 미로이며</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/765d71ad-9abc-4333-97e4-f9609d4c0346/image.PNG" /></p>
<blockquote>
</blockquote>
<p>다음과 같이 이동하면 가장 빠른 시간에 탈출할 수 있습니다.</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/19d0fa51-eca4-4218-a3d0-f699440230b2/image.PNG" /></p>
<blockquote>
</blockquote>
<p>4번 이동하여 레버를 당기고 출구까지 이동하면 총 16초의 시간이 걸립니다. 따라서 16을 반환합니다.</p>
<blockquote>
</blockquote>
<p>입출력 예 #2</p>
<blockquote>
</blockquote>
<p>주어진 문자열은 다음과 같은 미로입니다.</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/eb088040-3ab3-4162-bb24-7db994589422/image.PNG" /></p>
<blockquote>
</blockquote>
<p>시작 지점에서 이동할 수 있는 공간이 없어서 탈출할 수 없습니다. 따라서 -1을 반환합니다.</p>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>2번의 BFS 탐색이 필요<ol>
<li>시작 지점에서 레버까지의 최단거리 구하기</li>
<li>레버에서부터 출구까지의 최단거리 구하기</li>
<li>구한 두 최단거리를 더한 뒤 답으로 반환<br />    

</li>
</ol>
</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ol>
<li>인접한 상하좌우의 cell로 접근하기 위한 배열 dr/dc, map의 행열 길이 rowLength/colLength, 방문여부를 저장할 visited와 최단거리를 담을 answer 세팅</li>
<li>map 전체를 이중 for문으로 돌면서 시작 지점(’S’), 레버(’L’), 출구(’E’)의 좌표를 배열[row, col]로 저장하고 bfs()를 시작 지점부터 레버 위치까지 1번, 레버 위치부터 출구까지 1번 시행해서 각각의 최단 거리를 구함 </li>
<li>bfs 내의 루프에서 현재 위치가 목표 지점인지 검사하고 인접한 상하좌우의 칸이 유효한 위치인지 벽(’X’)인지 여부와 해당 칸에 대한 방문여부를 검사하고 해당 조건을 모두 통과했을 경우 큐에 해당 칸을 예약</li>
<li>3번을 반복하여 목표 지점에 도달할 경우 거리 dist를, 도달할 수 없다면 -1을 반환<ul>
<li>반환된 -1은 그대로 main 함수에서 -1로 반환됨</li>
</ul>
</li>
<li>시작 지점부터 레버 위치까지의 최단 거리와 레버 위치부터 출구까지의 최단 거리를 더한 값을 답으로 반환<br />

</li>
</ol>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

public class Solution {
    int[] dr = {-1, 1, 0, 0};
    int[] dc = {0, 0, 1, -1};
    int rowLength = 0;
    int colLength = 0;
    boolean[][] visited;
    int answer = 0;

    public int solution(String[] maps) {
        rowLength = maps.length;
        colLength = maps[0].length();
        int[] startLocation = new int[2];
        int[] leverLocation = new int[2];
        int[] endLocation = new int[2];

        for(int i = 0; i &lt; rowLength; i++) {
            for(int j = 0; j &lt; colLength; j++) {
                char ch = maps[i].charAt(j);
                if (ch == 'S') {
                    startLocation[0] = i;
                    startLocation[1] = j;
                } else if (ch == 'L') {
                    leverLocation[0] = i;
                    leverLocation[1] = j;
                } else if (ch == 'E') {
                    endLocation[0] = i;
                    endLocation[1] = j;
                }
            }
        }

        int leverDist = bfs(maps, startLocation, leverLocation);
        if (leverDist == -1) return -1; // 레버에 도달할 수 없는 경우

        int exitDist = bfs(maps, leverLocation, endLocation);
        if (exitDist == -1) return -1; // 출구에 도달할 수 없는 경우

        answer = leverDist + exitDist;
        return answer;
    }

    private int bfs(String[] maps, int[] start, int[] target) {
        visited = new boolean[rowLength][colLength];
        Queue&lt;int[]&gt; queue = new LinkedList&lt;&gt;();
        queue.offer(new int[]{start[0], start[1], 0});
        visited[start[0]][start[1]] = true;

        while(!queue.isEmpty()) {
            int[] cur = queue.poll();
            int r = cur[0];
            int c = cur[1];
            int dist = cur[2];

            if(r == target[0] &amp;&amp; c == target[1]) {
                return dist;
            }

            for(int i = 0; i &lt; 4; i++) {
                int nr = r + dr[i];
                int nc = c + dc[i];
                if(0 &lt;= nr &amp;&amp; nr &lt; rowLength &amp;&amp; 0 &lt;= nc &amp;&amp; nc &lt; colLength &amp;&amp; maps[nr].charAt(nc) != 'X' &amp;&amp; !visited[nr][nc]) {
                    queue.offer(new int[]{nr, nc, dist + 1});
                    visited[nr][nc] = true;
                }
            }
        }
        return -1; // 목표 지점에 도달할 수 없는 경우
    }
}</code></pre>