<h2 id="문제">문제</h2>
<p>거리두기 확인하기(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/81302">https://school.programmers.co.kr/learn/courses/30/lessons/81302</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>개발자를 희망하는 죠르디가 카카오에 면접을 보러 왔습니다.</p>
</blockquote>
<p>코로나 바이러스 감염 예방을 위해 응시자들은 거리를 둬서 대기를 해야하는데 개발 직군 면접인 만큼
아래와 같은 규칙으로 대기실에 거리를 두고 앉도록 안내하고 있습니다.</p>
<blockquote>
<blockquote>
</blockquote>
</blockquote>
<ol>
<li>대기실은 5개이며, 각 대기실은 5x5 크기입니다.</li>
<li>거리두기를 위하여 응시자들 끼리는 맨해튼 거리1가 2 이하로 앉지 말아 주세요.</li>
<li>단 응시자가 앉아있는 자리 사이가 파티션으로 막혀 있을 경우에는 허용합니다.<blockquote>
</blockquote>
예를 들어,<blockquote>
</blockquote>
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/196269e3-2cd6-4ca0-9cca-b4b9ecb3f21b/image.PNG" /><blockquote>
</blockquote>
5개의 대기실을 본 죠르디는 각 대기실에서 응시자들이 거리두기를 잘 기키고 있는지 알고 싶어졌습니다. 자리에 앉아있는 응시자들의 정보와 대기실 구조를 대기실별로 담은 2차원 문자열 배열 <code>places</code>가 매개변수로 주어집니다. 각 대기실별로 거리두기를 지키고 있으면 1을, 한 명이라도 지키지 않고 있으면 0을 배열에 담아 return 하도록 solution 함수를 완성해 주세요.</li>
</ol>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li><code>places</code>의 행 길이(대기실 개수) = 5<ul>
<li><code>places</code>의 각 행은 하나의 대기실 구조를 나타냅니다.</li>
</ul>
</li>
<li><code>places</code>의 열 길이(대기실 세로 길이) = 5</li>
<li><code>places</code>의 원소는 <code>P</code>,<code>O</code>,<code>X</code>로 이루어진 문자열입니다.<ul>
<li><code>places</code> 원소의 길이(대기실 가로 길이) = 5</li>
<li><code>P</code>는 응시자가 앉아있는 자리를 의미합니다.</li>
<li><code>O</code>는 빈 테이블을 의미합니다.</li>
<li><code>X</code>는 파티션을 의미합니다.</li>
</ul>
</li>
<li>입력으로 주어지는 5개 대기실의 크기는 모두 5x5 입니다.</li>
<li>return 값 형식<ul>
<li>1차원 정수 배열에 5개의 원소를 담아서 return 합니다.</li>
<li><code>places</code>에 담겨 있는 5개 대기실의 순서대로, 거리두기 준수 여부를 차례대로 배열에 담습니다.</li>
<li>각 대기실 별로 모든 응시자가 거리두기를 지키고 있으면 1을, 한 명이라도 지키지 않고 있으면 0을 담습니다.</li>
</ul>
</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<p><img alt="" src="https://velog.velcdn.com/images/gener-lst/post/4d2908e5-6fc1-4f70-a711-ce6b07d69ade/image.PNG" /></p>
<blockquote>
<h4 id="입출력-예-설명">입출력 예 설명</h4>
<p><strong>입출력 예 #1</strong>
첫 번째 대기실</p>
</blockquote>
<table>
<thead>
<tr>
<th align="left">No.</th>
<th align="left">0</th>
<th align="left">1</th>
<th align="left">2</th>
<th align="left">3</th>
<th align="left">4</th>
</tr>
</thead>
<tbody><tr>
<td align="left">0</td>
<td align="left">P</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">1</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">X</td>
<td align="left">O</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">O</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">O</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">P</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">X</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">* 모든 응시자가 거리두기를 지키고 있습니다.</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<blockquote>
</blockquote>
<p>두 번째 대기실</p>
<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">No.</th>
<th align="left">0</th>
<th align="left">1</th>
<th align="left">2</th>
<th align="left">3</th>
<th align="left">4</th>
</tr>
</thead>
<tbody><tr>
<td align="left">0</td>
<td align="left"><strong>P</strong></td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left"><strong>P</strong></td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">1</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left"><strong>P</strong></td>
<td align="left">X</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left"><strong>P</strong></td>
<td align="left">X</td>
<td align="left">X</td>
<td align="left">X</td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">X</td>
<td align="left">X</td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left"><strong>P</strong></td>
<td align="left"><strong>P</strong></td>
</tr>
<tr>
<td align="left">* (0, 0) 자리의 응시자와 (2, 0) 자리의 응시자가 거리두기를 지키고 있지 않습니다.</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">* (1, 2) 자리의 응시자와 (0, 3) 자리의 응시자가 거리두기를 지키고 있지 않습니다.</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
<tr>
<td align="left">* (4, 3) 자리의 응시자와 (4, 4) 자리의 응시자가 거리두기를 지키고 있지 않습니다.</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<blockquote>
</blockquote>
<p>세 번째 대기실</p>
<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">No.</th>
<th align="left">0</th>
<th align="left">1</th>
<th align="left">2</th>
<th align="left">3</th>
<th align="left">4</th>
</tr>
</thead>
<tbody><tr>
<td align="left">0</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">O</td>
<td align="left">P</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">1</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">O</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">X</td>
<td align="left">O</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">O</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">* 모든 응시자가 거리두기를 지키고 있습니다.</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<blockquote>
</blockquote>
<p>네 번째 대기실</p>
<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">No.</th>
<th align="left">0</th>
<th align="left">1</th>
<th align="left">2</th>
<th align="left">3</th>
<th align="left">4</th>
</tr>
</thead>
<tbody><tr>
<td align="left">0</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">1</td>
<td align="left">X</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">O</td>
<td align="left">X</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
<td align="left">O</td>
</tr>
<tr>
<td align="left">* 대기실에 응시자가 없으므로 거리두기를 지키고 있습니다.</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<blockquote>
</blockquote>
<p>다섯 번째 대기실</p>
<blockquote>
</blockquote>
<table>
<thead>
<tr>
<th align="left">No.</th>
<th align="left">0</th>
<th align="left">1</th>
<th align="left">2</th>
<th align="left">3</th>
<th align="left">4</th>
</tr>
</thead>
<tbody><tr>
<td align="left">0</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">1</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">2</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">3</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
</tr>
<tr>
<td align="left">4</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
<td align="left">X</td>
<td align="left">P</td>
</tr>
<tr>
<td align="left">* 모든 응시자가 거리두기를 지키고 있습니다.</td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
</tr>
</tbody></table>
<blockquote>
</blockquote>
<p>두 번째 대기실을 제외한 모든 대기실에서 거리두기가 지켜지고 있으므로, 배열 [1, 0, 1, 1, 1]을 return 합니다.</p>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>주어진 대기실 5개는 [5 x 5] 사이즈이며, 대기실 하나는 P, X, O로만 이루어진 문자열 5개가 저장된 배열로 주어진다.<ul>
<li>대기실의 행 길이 = places[i].length = 5(배열의 길이)</li>
<li>대기실의 열 길이 = places[i][j].length() = 5(문자열의 길이)</li>
</ul>
</li>
<li>각 대기실에 대해 응시자(&quot;P&quot;) 간 맨해튼 거리(|가로 거리| + |새로 거리|)가 2 이하가 되지 않도록 모두 지켜지고 있으면 1을, 아니라면 0을 답으로 반환한다.</li>
<li>응시자(&quot;P&quot;) 간 거리의 측정에는 빈 테이블(”O”)로 뚫려있는 범위만 계산하고 파티션(”X”)으로 막혀있으면 계산되지 않는다.</li>
<li>5개의 대기실에 대한 거리두기 준수 여부를 0, 1로 이루어진 배열로 도출한다.<br />    

</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>Solution(): 모든 대기실에 대해 각각 check 함수를 실행하고 0 또는 1의 값을 answer 배열에 저장하고 반환</li>
<li>check(): for 문 내에서 대기실 내 응시자(&quot;P&quot;)를 찾고 응시자의 수 만큼 bfs를 실행하고 실행 결과로 false가 반환되면 0을, false가 반환되지 않고 반복문이 끝나면 1을 반환</li>
<li>bfs(): 대기실 내 응시자(&quot;P&quot;)의 위치를 시작점으로 거리(dist)가 2 이내의 접근가능한 모든 칸을 확인하고 해당 거리 내에 다른 응시자(&quot;P&quot;)가 있다면 false, 없다면 true 반환<ul>
<li>다음 칸에 대한 접근가능 조건<pre><code>  1. 대기실 범위 내에서 현재 칸의 상하좌우에 위치한 칸</code></pre><ol start="2">
<li>파티션(&quot;X&quot;)로 막혀있지 않은 칸</li>
<li>탐색되지 않은(visited[nr][nc] == false) 칸</li>
<li>탐색 시작 위치에서 거리가 2이내인 칸<br />

</li>
</ol>
</li>
</ul>
</li>
</ul>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

public class Solution {
    public int[] solution(String[][] places) {
        int[] answer = new int[5];
        for (int i = 0; i &lt; 5; i++) {
            answer[i] = check(places[i]);
        }
        return answer;
    }

    private int check(String[] place) {
        for (int i = 0; i &lt; 5; i++) {
            if (place[i].contains(&quot;P&quot;)) {
                for (int j = 0; j &lt; 5; j++) {
                    if (place[i].charAt(j) == 'P') {
                        if (!bfs(i, j, place)) return 0;
                    }
                }
            }
        }
        return 1;
    }

    private boolean bfs(int sr, int sc, String[] place) {
        int[] dr = {0, 0, 1, -1};
        int[] dc = {1, -1, 0, 0};

        Queue&lt;int[]&gt; queue = new ArrayDeque&lt;&gt;();
        boolean[][] visited = new boolean[5][5];
        queue.offer(new int[]{sr, sc, 0});
        visited[sr][sc] = true;

        while (!queue.isEmpty()) {
            int[] cur = queue.poll();
            int r = cur[0];
            int c = cur[1];
            int dist = cur[2];

            if (dist &gt; 0 &amp;&amp; place[r].charAt(c) == 'P') return false;

            for (int i = 0; i &lt; 4; i++) {
                int nr = r + dr[i];
                int nc = c + dc[i];

                if (nr &gt;= 0 &amp;&amp; nc &gt;= 0 &amp;&amp; nr &lt; 5 &amp;&amp; nc &lt; 5 &amp;&amp; !visited[nr][nc]) {
                    if (dist + 1 &lt;= 2 &amp;&amp; place[nr].charAt(nc) != 'X') {
                        queue.offer(new int[]{nr, nc, dist + 1});
                        visited[nr][nc] = true;
                    }
                }
            }
        }
        return true;
    }
}</code></pre>