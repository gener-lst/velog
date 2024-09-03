<h2 id="문제">문제</h2>
<p>석유 시추(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/250136">https://school.programmers.co.kr/learn/courses/30/lessons/250136</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>세로길이가 <code>n</code> 가로길이가 <code>m</code>인 격자 모양의 땅 속에서 석유가 발견되었습니다. 석유는 여러 덩어리로 나누어 묻혀있습니다. 당신이 시추관을 수직으로 단 하나만 뚫을 수 있을 때, 가장 많은 석유를 뽑을 수 있는 시추관의 위치를 찾으려고 합니다. 시추관은 열 하나를 관통하는 형태여야 하며, 열과 열 사이에 시추관을 뚫을 수 없습니다.</p>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/1aa790a0-bec7-4344-b890-cd1e43cddbdc/image.PNG" /></p>
<blockquote>
</blockquote>
<p>예를 들어 가로가 8, 세로가 5인 격자 모양의 땅 속에 위 그림처럼 석유가 발견되었다고 가정하겠습니다. 상, 하, 좌, 우로 연결된 석유는 하나의 덩어리이며, 석유 덩어리의 크기는 덩어리에 포함된 칸의 수입니다. 그림에서 석유 덩어리의 크기는 왼쪽부터 8, 7, 2입니다.</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/a8903ad7-b338-4f71-8b97-5809bdb92d55/image.PNG" /></p>
<blockquote>
</blockquote>
<p>시추관은 위 그림처럼 설치한 위치 아래로 끝까지 뻗어나갑니다. 만약 시추관이 석유 덩어리의 일부를 지나면 해당 덩어리에 속한 모든 석유를 뽑을 수 있습니다. 시추관이 뽑을 수 있는 석유량은 시추관이 지나는 석유 덩어리들의 크기를 모두 합한 값입니다. 시추관을 설치한 위치에 따라 뽑을 수 있는 석유량은 다음과 같습니다.</p>
<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">시추관의 위치</th>
<th align="left">획득한 덩어리</th>
<th align="left">총 석유량</th>
</tr>
</thead>
<tbody><tr>
<td align="left">1</td>
<td align="left">[8]</td>
<td align="left">8</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">[8]</td>
<td align="left">8</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">[8]</td>
<td align="left">8</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">[7]</td>
<td align="left">7</td>
</tr>
<tr>
<td align="left">5</td>
<td align="left">[7]</td>
<td align="left">7</td>
</tr>
<tr>
<td align="left">6</td>
<td align="left">[7]</td>
<td align="left">7</td>
</tr>
<tr>
<td align="left">7</td>
<td align="left">[7, 2]</td>
<td align="left">9</td>
</tr>
<tr>
<td align="left">8</td>
<td align="left">[2]</td>
<td align="left">2</td>
</tr>
<tr>
<td align="left">오른쪽 그림처럼 7번 열에 시추관을 설치하면 크기가 7, 2인 덩어리의 석유를 얻어 뽑을 수 있는 석유량이 9로 가장 많습니다.</td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<blockquote>
</blockquote>
<p>석유가 묻힌 땅과 석유 덩어리를 나타내는 2차원 정수 배열 <code>land</code>가 매개변수로 주어집니다. 이때 시추관 하나를 설치해 뽑을 수 있는 가장 많은 석유량을 return 하도록 solution 함수를 완성해 주세요.</p>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>1 ≤ <code>land</code>의 길이 = 땅의 세로길이 = <code>n</code> ≤ 500<ul>
<li>1 ≤ <code>land[i]</code>의 길이 = 땅의 가로길이 = <code>m</code> ≤ 500</li>
<li><code>land[i][j]</code>는 <code>i+1</code>행 <code>j+1</code>열 땅의 정보를 나타냅니다.</li>
<li><code>land[i][j]</code>는 0 또는 1입니다.</li>
<li><code>land[i][j]</code>가 0이면 빈 땅을, 1이면 석유가 있는 땅을 의미합니다.<blockquote>
</blockquote>
정확성 테스트 케이스 제한사항</li>
</ul>
</li>
<li>1 ≤ <code>land</code>의 길이 = 땅의 세로길이 = <code>n</code> ≤ 100<ul>
<li>1 ≤ <code>land[i]</code>의 길이 = 땅의 가로길이 = <code>m</code> ≤ 500<blockquote>
</blockquote>
효율성 테스트 케이스 제한사항</li>
</ul>
</li>
<li>주어진 조건 외 추가 제한사항 없습니다.</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
<table>
<thead>
<tr>
<th align="left">land</th>
<th align="left">result</th>
</tr>
</thead>
<tbody><tr>
<td align="left">[[0, 0, 0, 1, 1, 1, 0, 0], [0, 0, 0, 0, 1, 1, 0, 0], [1, 1, 0, 0, 0, 1, 1, 0], [1, 1, 1, 0, 0, 0, 0, 0], [1, 1, 1, 0, 0, 0, 1, 1]]</td>
<td align="left">9</td>
</tr>
<tr>
<td align="left">[[1, 0, 1, 0, 1, 1], [1, 0, 1, 0, 0, 0], [1, 0, 1, 0, 0, 1], [1, 0, 0, 1, 0, 0], [1, 0, 0, 1, 0, 1], [1, 0, 0, 0, 0, 0], [1, 1, 1, 1, 1, 1]]</td>
<td align="left">16</td>
</tr>
<tr>
<td align="left">#### 입출력 예 설명</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">입출력 예 #1</td>
<td align="left"></td>
</tr>
<tr>
<td align="left">문제의 예시와 같습니다.</td>
<td align="left"></td>
</tr>
</tbody></table>
</blockquote>
<p>입출력 예 #2</p>
<blockquote>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/663e24a7-0d0d-4a90-953f-9e4c8236de62/image.PNG" /></p>
<blockquote>
</blockquote>
<p>시추관을 설치한 위치에 따라 뽑을 수 있는 석유는 다음과 같습니다.</p>
<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">시추관의 위치</th>
<th align="left">획득한 덩어리</th>
<th align="left">총 석유량</th>
</tr>
</thead>
<tbody><tr>
<td align="left">1</td>
<td align="left">[12]</td>
<td align="left">12</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">[12]</td>
<td align="left">12</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">[3, 12]</td>
<td align="left">15</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">[2, 12]</td>
<td align="left">14</td>
</tr>
<tr>
<td align="left">5</td>
<td align="left">[2, 12]</td>
<td align="left">14</td>
</tr>
<tr>
<td align="left">6</td>
<td align="left">[2, 1, 1, 12]</td>
<td align="left">16</td>
</tr>
<tr>
<td align="left">6번 열에 시추관을 설치하면 크기가 2, 1, 1, 12인 덩어리의 석유를 얻어 뽑을 수 있는 석유량이 16으로 가장 많습니다. 따라서 <code>16</code>을 return 해야 합니다.</td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>석유 덩어리에 포함된 칸의 수는 1의 값을 가지는 인접한 칸의 수이다.</li>
<li>시추관이 각 열마다 지나가기 때문에 석유 덩어리의 칸 수가 가장 많이 위치하는 열을 찾고 해당 열에서 얻을 수 있는 석유량을 반환</li>
</ul>
<ol>
<li>각 열 별로 지나가는 칸 중 석유가 존재하는 칸에서 시작하는 DFS를 통해 열 별로 획득할 수 있는 총 석유량을 구하고 최대치를 갱신</li>
<li>각 열 별로 지나가는 칸 중 석유가 존재하는 칸에서 시작하는 BFS를 통해 해당 칸으로부터 얻을 수 있는 총 석유량을 구하고 각 열을 Set에 저장하여 열 인덱스 별로 얻을 수 있는 총량을 Map에 저장  <br />

</li>
</ol>
<h3 id="접근-방법">접근 방법</h3>
<h4 id="풀이1">풀이1</h4>
<ol>
<li>column 별로 석유가 존재하는 칸(1인 칸)에서 dfs를 시행하기 위해 이중 for문의 첫 변수를 column으로 두고 column 별로 visited와 count 초기화 </li>
<li>column 별 dfs() 시행:<ul>
<li>시작점에서부터 인접한 칸이 유효한 칸이면서 방문하지 않은 석유 칸이라면 해당 칸에서 시작하는 dfs() 재귀 호출 -&gt; 이 부분에서 효율성 문제가 발생한 듯? </li>
<li>재귀 호출된 함수 종료시, 1을 반환하고 재귀 호출 횟수만큼(탐색한 칸의 횟수만큼) count에 더해진 후 해당 count를 최초 dfs를 시행한 solution 함수 내의 count에 저장</li>
</ul>
</li>
<li>column 별로 구한 석유 칸 수를 기존 최대 석유 칸 수 maxCount와 비교 후 갱신하고 최종적으로 maxCount를 답으로 반환
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/6ac052f5-f8ba-4bfa-bdf5-4e39de2b080f/image.PNG" /></li>
</ol>
<ul>
<li>로직은 맞았는데 효율성에서 떨어졌다...</li>
</ul>
<h4 id="풀이2">풀이2</h4>
<ol>
<li>land 내의 모든 칸 중 석유가 존재하고 아직 방문하지 않은 칸에서 시작하는 bfs 시행</li>
<li>bfs(): <ul>
<li>bfs() 로직을 통해 해당 칸에서 상하좌우 방향으로 인접하는 석유 칸을 구하되 총 석유 칸 수와 지나는 열 저장</li>
<li>모든 탐색 종료 후 시작 칸과 인접한 총 석유 칸 수 count 반환</li>
</ul>
</li>
<li>totalCount에 column 별로 bfs를 통해 구한 석유 칸을 저장하되 기존에 저장된 값이 있으면 해당 값에 추가</li>
<li>모든 칸에 대해 bfs와 totalCount의 갱신이 끝났다면, column 별로 저장된 석유 칸의 값을 비교/갱신하여 answer에 저장하고 답으로 반환
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/3e588e8e-a205-48ae-b6d7-b20bd9d30405/image.PNG" /></li>
</ol>
<ul>
<li>성공!<br />

</li>
</ul>
<h3 id="코드-구현">코드 구현</h3>
<p>코드1(column 별 DFS - 효율성 테스트 실패)</p>
<pre><code class="language-java">class Solution {
    public static int[] dc = new int[] {0, 0, 1, -1};
    public static int[] dr = new int[] {1, -1, 0, 0};

    public int solution(int[][] land) {
        boolean[][] visited;
        int maxCount = 0;

        for(int c = 0; c &lt; land[0].length; c++) {
            visited = new boolean[land.length][land[0].length];
            int count = 0;
            for(int r = 0; r &lt; land.length; r++) {
                if(land[r][c] == 1 &amp;&amp; !visited[r][c]) {
                    count += dfs(r, c, land, visited);
                }
            }
            maxCount = Math.max(maxCount, count);
        }

        return maxCount;
    }

    private int dfs(int r, int c, int[][] land, boolean[][] visited) {
        visited[r][c] = true;
        int count = 1;

        for(int i = 0; i &lt; 4; i++) {
            int nr = r + dr[i];
            int nc = c + dc[i];

            if(nr &gt;= 0 &amp;&amp; nc &gt;= 0 &amp;&amp; nr &lt; land.length &amp;&amp; nc &lt; land[0].length &amp;&amp; !visited[nr][nc] &amp;&amp; land[nr][nc] == 1) {
                count += dfs(nr, nc, land, visited);
            }
        }

        return count;
    }
}</code></pre>
<p>코드2(BFS)</p>
<pre><code class="language-java">import java.util.*;

public class Solution {
    public static boolean[][] visited;
    public static int[] dr = {1, 0, -1, 0};
    public static int[] dc = {0, 1, 0, -1};

    public int solution(int[][] land) {
        visited = new boolean[land.length][land[0].length];
        Map&lt;Integer, Integer&gt; totalCount = new HashMap&lt;&gt;();

        int answer = 0;

        for (int r = 0; r &lt; land.length; r++) {
            for (int c = 0; c &lt; land[0].length; c++) {
                if (land[r][c] == 1 &amp;&amp; !visited[r][c]) {
                    Set&lt;Integer&gt; cols = new HashSet&lt;&gt;();
                    int count = bfs(r, c, land, cols);

                    for (int col : cols) {
                        totalCount.put(col, totalCount.getOrDefault(col, 0) + count);
                    }
                }
            }
        }

        for (int value : totalCount.values()) {
            answer = Math.max(answer, value);
        }

        return answer;
    }

    private int bfs(int r, int c, int[][] land, Set&lt;Integer&gt; cols) {
        Queue&lt;int[]&gt; queue = new LinkedList&lt;&gt;();
        queue.offer(new int[]{r, c});
        visited[r][c] = true;

        int count = 0;
        while (!queue.isEmpty()) {
            int[] cur = queue.poll();
            int cr = cur[0];
            int cc = cur[1];
            count++;
            cols.add(cc);

            for (int i = 0; i &lt; 4; i++) {
                int nr = cr + dr[i];
                int nc = cc + dc[i];
                if (nr &gt;= 0 &amp;&amp; nr &lt; land.length &amp;&amp; nc &gt;= 0 &amp;&amp; nc &lt; land[0].length &amp;&amp; land[nr][nc] == 1 &amp;&amp; !visited[nr][nc]) {
                    queue.offer(new int[]{nr, nc});
                    visited[nr][nc] = true;
                }
            }
        }
        return count;
    }
}
</code></pre>