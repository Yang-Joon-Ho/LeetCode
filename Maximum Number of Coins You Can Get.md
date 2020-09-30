[문제](https://leetcode.com/problems/maximum-number-of-coins-you-can-get/)
---------------

<br>
<br>

### 1. 코드

```cpp
class Solution {
public:
    int maxCoins(vector<int>& piles) {
        
        int answer = 0;
        
        sort(piles.begin(), piles.end(), greater<>());
        
        for(int i = 1, len = piles.size(); len > 0 ; i += 2, len -= 3) {
            answer += piles[i];
        }
        
        return answer;
    }
};
```

<br>

### 2. 코멘트
  
    문제 설명 : 동전 묶음에서 alice, 나, 그리고 밥 순서로 동전 하나씩을 가져갈 때, 
    내가 가장 높은 합계를 얻을 수 있는 경우의 동전 합계를 구하라 
    모든 동전 중에서 3개씩을 묶어서 한명씩 가져가므로 piles = [9,8,7,6,5,1,2,3,4] 라고 했을 때, 
    최적해를 가질 수 있는 동전 묶음은 각각 
    
    (9,8,1), (7,6,2), (5,4,3) 이다. 여기서 '나'는 alice 다음으로 동전을 가져갈 수 있으므로 
    8 + 6 + 4가 내가 가질수 있는 동전의 최대합이다. 
    
    이를 쉽게 생각 해 보면, 동전 가치 내림차순으로 정렬 했을 때, 나는 i = 1 부터 i + 2씩 건너뛰면서 동전을 가져가면 된다. 
    그런데 여기서 세 개씩 가져간다고 했으므로 
    
    총 동전 개수 - 3씩 하면 된다. 

