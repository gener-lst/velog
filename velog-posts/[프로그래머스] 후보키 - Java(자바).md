<h2 id="문제">문제</h2>
<p>후보키(<a href="https://school.programmers.co.kr/learn/courses/30/lessons/42890">https://school.programmers.co.kr/learn/courses/30/lessons/42890</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>프렌즈대학교 컴퓨터공학과 조교인 제이지는 네오 학과장님의 지시로, 학생들의 인적사항을 정리하는 업무를 담당하게 되었다.</p>
</blockquote>
<p>그의 학부 시절 프로그래밍 경험을 되살려, 모든 인적사항을 데이터베이스에 넣기로 하였고, 이를 위해 정리를 하던 중에 후보키(Candidate Key)에 대한 고민이 필요하게 되었다.</p>
<blockquote>
</blockquote>
<p>후보키에 대한 내용이 잘 기억나지 않던 제이지는, 정확한 내용을 파악하기 위해 데이터베이스 관련 서적을 확인하여 아래와 같은 내용을 확인하였다.</p>
<blockquote>
</blockquote>
<ul>
<li>관계 데이터베이스에서 릴레이션(Relation)의 튜플(Tuple)을 유일하게 식별할 수 있는 속성(Attribute) 또는 속성의 집합 중, 다음 두 성질을 만족하는 것을 후보 키(Candidate Key)라고 한다.<ul>
<li>유일성(uniqueness) : 릴레이션에 있는 모든 튜플에 대해 유일하게 식별되어야 한다.</li>
<li>최소성(minimality) : 유일성을 가진 키를 구성하는 속성(Attribute) 중 하나라도 제외하는 경우 유일성이 깨지는 것을 의미한다. 즉, 릴레이션의 모든 튜플을 유일하게 식별하는 데 꼭 필요한 속성들로만 구성되어야 한다.<blockquote>
</blockquote>
제이지를 위해, 아래와 같은 학생들의 인적사항이 주어졌을 때, 후보 키의 최대 개수를 구하라.<blockquote>
</blockquote>
<img alt="" src="https://velog.velcdn.com/images/gener-lst/post/f8e7901e-196e-4772-852b-f5fc967a2bb5/image.PNG" /><blockquote>
</blockquote>
위의 예를 설명하면, 학생의 인적사항 릴레이션에서 모든 학생은 각자 유일한 &quot;학번&quot;을 가지고 있다. 따라서 &quot;학번&quot;은 릴레이션의 후보 키가 될 수 있다.
그다음 &quot;이름&quot;에 대해서는 같은 이름(&quot;apeach&quot;)을 사용하는 학생이 있기 때문에, &quot;이름&quot;은 후보 키가 될 수 없다. 그러나, 만약 [&quot;이름&quot;, &quot;전공&quot;]을 함께 사용한다면 릴레이션의 모든 튜플을 유일하게 식별 가능하므로 후보 키가 될 수 있게 된다.
물론 [&quot;이름&quot;, &quot;전공&quot;, &quot;학년&quot;]을 함께 사용해도 릴레이션의 모든 튜플을 유일하게 식별할 수 있지만, 최소성을 만족하지 못하기 때문에 후보 키가 될 수 없다.
따라서, 위의 학생 인적사항의 후보키는 &quot;학번&quot;, [&quot;이름&quot;, &quot;전공&quot;] 두 개가 된다.<blockquote>
</blockquote>
릴레이션을 나타내는 문자열 배열 relation이 매개변수로 주어질 때, 이 릴레이션에서 후보 키의 개수를 return 하도록 solution 함수를 완성하라.</li>
</ul>
</li>
</ul>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>relation은 2차원 문자열 배열이다.</li>
<li>relation의 컬럼(column)의 길이는 1 이상 8 이하이며, 각각의 컬럼은 릴레이션의 속성을 나타낸다.</li>
<li>relation의 로우(row)의 길이는 1 이상 20 이하이며, 각각의 로우는 릴레이션의 튜플을 나타낸다.</li>
<li>relation의 모든 문자열의 길이는 1 이상 8 이하이며, 알파벳 소문자와 숫자로만 이루어져 있다.</li>
<li>relation의 모든 튜플은 유일하게 식별 가능하다.(즉, 중복되는 튜플은 없다.)</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
<table>
<thead>
<tr>
<th align="left">relation</th>
<th align="left">result</th>
</tr>
</thead>
<tbody><tr>
<td align="left">[[&quot;100&quot;,&quot;ryan&quot;,&quot;music&quot;,&quot;2&quot;], <br />[&quot;200&quot;,&quot;apeach&quot;,&quot;math&quot;,&quot;2&quot;], <br />[&quot;300&quot;,&quot;tube&quot;,&quot;computer&quot;,&quot;3&quot;], <br />[&quot;400&quot;,&quot;con&quot;,&quot;computer&quot;,&quot;4&quot;], <br />[&quot;500&quot;,&quot;muzi&quot;,&quot;music&quot;,&quot;3&quot;], <br />[&quot;600&quot;,&quot;apeach&quot;,&quot;music&quot;,&quot;2&quot;]]</td>
<td align="left">2</td>
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
<td align="left">문제에 주어진 릴레이션과 같으며, 후보 키는 2개이다.</td>
<td align="left"></td>
</tr>
</tbody></table>
</blockquote>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li><code>후보키</code> ⇒ <code>유일성</code>과 <code>최소성</code>을 만족하면서, 관계 데이터베이스에서 릴레이션의 튜플을 유일하게 식별할 수 있는 속성 또는 속성의 집합<ul>
<li><code>유일성</code> ⇒ 릴레이션에 있는 모든 튜플이 유일하게 식별되도록하는 특성</li>
<li><code>최소성</code> ⇒ 후보키의 한 속성이라도 제외될 경우 유일성이 깨지는 특성</li>
</ul>
</li>
<li>주어진 릴레이션에서 유일성과 최소성을 만족하는 후보키의 최대 개수를 찾아라<br />    

</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>방문여부, 릴레이션의 행열의 길이, 키의 모든 조합을 저장할 list, list의 요소들에 대해 유일성과 최소성 검사를 하고 난 최종 후보키를 저장할 list2를 선언 및 초기화</li>
</ul>
<ol>
<li><p>행의 길이 만큼 combine 메서드와 validate 메서드를 실행</p>
</li>
<li><p>combine(): dfs를 백트래킹하여 속성키가 될 수 있는 모든 index의 조합을 list에 저장</p>
</li>
<li><p>validate(): 개별 index 조합을 분리하여 조합 내 각 index를 저장하는 배열 생성. set을 생성하고 해당 배열을 이용하여 해당 조합에 모든 릴레이션의 값을 문자열로 만들어 set에 저장하고 모든 값을 저장했을 때 set의 길이와 실제 열의 길이(릴레이션 개수)와 비교 </p>
<p> → 길이가 다를 경우 중복된 데이터가 존재한다는 의미 → 해당 속성키 조합으로는 유일성 충족x</p>
<ul>
<li><p>유일성 조건을 통과할 경우, list2에 있는 후보키의 index 조합을 가져와 분리하고 유일성 조건을 통과한 data와 비교하고 각 요소가 포함되어 있을 때마다, cnt++. </p>
<p>→ cnt와 가져온 후보키의 index 조합을 분리한 배열의 길이가 같을 경우 최소성 검사 flag를 true</p>
<p>→ 위의 경우 data의 속성키 조합이 가져온 후보키의 속성 조합 +a라는 의미이므로 최소성 충족x</p>
</li>
<li><p>최소성 조건도 통과했을 경우 해당 index 조합을 list2에 추가 </p>
</li>
</ul>
</li>
<li><p>후보키 조합들을 모두 저장한 list2의 길이를 답으로 반환</p>
<br />

</li>
</ol>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public static boolean[] visited;
    public static int colLength;
    public static int rowLength;
    public static Set&lt;String&gt; list = new HashSet&lt;&gt;();
    public static List&lt;String&gt; list2 = new ArrayList&lt;&gt;();

    public int solution(String[][] relation) {
        colLength = relation[0].length;
        rowLength = relation.length;
        visited = new boolean[colLength];

        for (int i = 1; i &lt;= colLength; i++) {
            combine(0, i, relation);
            validate(relation);
            list.clear();
        }

        return list2.size();
    }

    public void combine(int start, int combNum, String[][] relation) {
        if (combNum == 0) {
            String temp = &quot;&quot;;
            for (int i = 0; i &lt; colLength; i++) {
                if (visited[i]) {
                    temp += i;
                }
            }
            list.add(temp);
        }

        for (int i = start; i &lt; colLength; i++) {
            if (!visited[i]) {
                visited[i] = true;
                combine(start + 1, combNum - 1, relation);
                visited[i] = false;
            }
        }
    }

    public void validate(String[][] relation) {
        //유일성 판단하기
        for (String data : list) {
            String[] temp = data.split(&quot;&quot;);
            int[] arr = new int[temp.length];
            for (int i = 0; i &lt; temp.length; i++) {
                int c = Integer.parseInt(temp[i]);
                arr[i] = c;
            }
            //유일성 판단하기위한 set
            Set&lt;String&gt; set = new HashSet&lt;&gt;();
            for (int i = 0; i &lt; rowLength; i++) {
                String cdd = &quot;&quot;;
                for (String data2 : temp) {
                    int c = Integer.parseInt(data2);
                    cdd += relation[i][c];
                }
                set.add(cdd);
            }
            //만약 유일하다면 최소성 검사
            if (set.size() == rowLength) {
                boolean flag = false;
                for (String data3 : list2) {
                    int cnt = 0;
                    String[] temp3 = data3.split(&quot;&quot;);
                    for (String data4 : temp3) {
                        if (data.contains(data4)) {
                            cnt++;
                        }
                    }
                    if (cnt == data3.length()) {
                        flag = true;
                    }
                }
                if (!flag) {
                    list2.add(data);
                }
            }
        }
    }
}</code></pre>