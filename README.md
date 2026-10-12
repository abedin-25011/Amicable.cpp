# Amicable.cpp
Assignment

#include <bits/stdc++.h>
using namespace std;

int main()
{
    vector<pair<int, int>> tests;
    int L, R, maxR = 0;

    while (cin >> L >> R)
    {
        if (L == 0 && R == 0)
            break;

        tests.push_back({L, R});
        maxR = max(maxR, R);
    }

    vector<int> sum(maxR + 1, 0);

    for (int i = 1; i <= maxR / 2; i++)
    {
        for (int j = 2 * i; j <= maxR; j += i)
            sum[j] += i;
    }

    for (auto t : tests)
    {
        int count = 0;
        L = t.first;
        R = t.second;

        for (int i = L; i <= R; i++)
        {
            int j = sum[i];

            if (j > i && j <= R && sum[j] == i)
                count++;
        }

        cout << count << '\n';
    }

    return 0;
}

