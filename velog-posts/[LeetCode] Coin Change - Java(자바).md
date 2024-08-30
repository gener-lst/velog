<h2 id="문제">문제</h2>
<p>Coin Change(<a href="https://leetcode.com/problems/coin-change">https://leetcode.com/problems/coin-change</a>)</p>
<blockquote>
<h4 id="문제-설명">문제 설명</h4>
<p>You are given an integer array <code>coins</code> representing coins of different denominations and an integer <code>amount</code> representing a total amount of money.</p>
</blockquote>
<p>Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return <code>-1</code>.</p>
<blockquote>
</blockquote>
<p>You may assume that you have an infinite number of each kind of coin.</p>
<blockquote>
<h4 id="문제-해석">문제 해석</h4>
<p>여러 종류의 동전을 나타내는 정수 배열 coins가 주어집니다. 또한, amount라는 총 금액이 주어집니다.</p>
</blockquote>
<p>이 금액을 만들기 위해 필요한 최소 동전의 수를 반환하세요. 만약 이 금액을 주어진 동전으로 만들 수 없다면 -1을 반환하세요.</p>
<blockquote>
</blockquote>
<p>각 동전의 개수는 무한히 많다고 가정할 수 있습니다.</p>
<blockquote>
<h4 id="제한사항">제한사항</h4>
</blockquote>
<ul>
<li>1 &lt;= coins.length &lt;= 12</li>
<li>1 &lt;= coins[i] &lt;= 231 - 1</li>
<li>0 &lt;= amount &lt;= 104</li>
</ul>
<blockquote>
<h4 id="입출력-예">입출력 예</h4>
</blockquote>
<p><strong>Example 1:</strong></p>
<ul>
<li><strong>Input:</strong> coins = [1,2,5], amount = 11</li>
<li><strong>Output:</strong> 3</li>
<li><strong>Explanation:</strong> 11 = 5 + 5 + 1<blockquote>
</blockquote>
</li>
<li><em>Example 2:*</em></li>
<li><strong>Input:</strong> coins = [2], amount = 3</li>
<li><strong>Output:</strong> -1<blockquote>
</blockquote>
</li>
<li><em>Example 3:*</em></li>
<li><strong>Input:</strong> coins = [1], amount = 0</li>
<li><strong>Output:</strong> -1</li>
</ul>
<h2 id="풀이">풀이</h2>
<h3 id="문제-파악">문제 파악</h3>
<ul>
<li>동전의 종류(coins)와 목표 금액(amount)이 주어졌을 때, 목표 금액을 만들기 위해 필요한 최소 동전 개수를 구하는 문제</li>
<li>주어진 동전 내의 조합으로 목표 금액을 만들 수 없을 경우 -1을 반환</li>
</ul>
<h3 id="접근-방법">접근 방법</h3>
<ul>
<li>문제의 답은 목표 금액을 만들 수 있는 동전의 조합 중 동전의 개수가 최소가 되는 값이며, 이를 위해 특정 금액 별 구성 동전의 개수가 최소인 경우 구하는 점화식을 구해야 한다. 이 경우, 다음과 같은 점화식을 유도할 수 있다.</li>
</ul>
<p>$$
F(n) = \min\left(…\mathrm{F}(n-\mathrm{coins}[i])\right) + 1 \
F(0) = 0
$$</p>
<ul>
<li>해당 점화식을 바탕으로 Bottom-Up 방식의 코드를 구현하면 다음과 같다.</li>
</ul>
<ol>
<li>금액을 가리키는 인덱스에 값으로 동전 개수를 저장하는 배열 생성하고 모든 값을 Integer.MAX_VALUE로 초기화. 0번째 값에는 0을 저장</li>
<li>for 문 내에서 목표 금액까지의 각 금액을 만들 수 있는 최소 동전 개수를 각각 저장/갱신함<ul>
<li>조합 가능한 금액(인덱스)와 해당 금액을 만들 수 있는 최소 동전 개수(값)으로 이루어진 배열 dp 완성</li>
</ul>
</li>
<li>배열[목표 금액]의 값이 Integer.MAX_VALUE가 아닐 경우(값이 갱신되었을 경우), 해당 값이 목표 금액을 만들기 위해 필요한 최소 동전 개수가 됨<ul>
<li>배열[목표 금액]의 값이 Integer.MAX_VALUE일 경우, -1 반환</li>
</ul>
</li>
</ol>
<h3 id="코드-구현">코드 구현</h3>
<pre><code class="language-java">import java.util.*;

class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0;
        for (int i = 0; i &lt; amount; i++) {
            if (dp[i] == Integer.MAX_VALUE) continue;
            for (int coin : coins) {
                // Prevent overflow by checking if i + coin will overflow
                if (coin &gt; 0 &amp;&amp; i &lt;= amount - coin) {
                    dp[i + coin] = Math.min(dp[i + coin], dp[i] + 1);
                }
            }
        }
        return (dp[amount] == Integer.MAX_VALUE) ? -1 : dp[amount];
    }
}
</code></pre>