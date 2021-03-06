---
title: 121-best-time-to-buy-and-sell-stock
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---


# problem
[121-best-time-to-buy-and-sell-stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/#/description)

# solution

## solution 1.DP

time out 
```cpp
    int maxProfit(vector<int>& prices) {
        if (prices.empty())
            return 0;
        vector<int> result(prices.size(),0);
        for (int i = 1; i < prices.size(); i++)
            for (int j = i-1; j>=0;j--)
                if (prices[j] < prices[i])
                    result[i] = max(result[i],result[j] + prices[i] - prices[j]);
        return *max_element(result.begin(),result.end());
    }
```

## solution 2. Dp
使用坐标记录最小值;
```cpp
    int maxProfit(vector<int>& prices) {
        if (prices.empty())
            return 0;
        vector<int> result(prices.size(),0);
        int min_elem = 0;
        for (int i = 1; i < prices.size(); i++)
        {
            if (prices[i] > prices[min_elem])
                result[i] = result[min_elem] + prices[i] - prices[min_elem];
            else
                min_elem = i;
        }
        return *max_element(result.begin(),result.end());
    }

```