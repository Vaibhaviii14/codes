# codes

<<<<<<<<0/1 Knapsack>>>>>>>
#include <bits/stdc++.h>
using namespace std;

int knapsack(int wt[], int val[], int n, int W) {
    int dp[100][100];

    for (int i = 0; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            if (i == 0 || w == 0)
                dp[i][w] = 0;
            else if (wt[i - 1] <= w)
                dp[i][w] = max(val[i - 1] + dp[i - 1][w - wt[i - 1]],
                               dp[i - 1][w]);
            else
                dp[i][w] = dp[i - 1][w];
        }
    }

    return dp[n][W];
}

int main() {
    int val[] = {60, 100, 120};
    int wt[] = {10, 20, 30};
    int W = 50;
    int n = 3;

    cout << knapsack(wt, val, n, W);

    return 0;
}



<<<<<<<<<Prims>>>>>>>>>>
#include <bits/stdc++.h>
using namespace std;

int main() {
    int n;
    cin >> n;

    int cost[10][10];

    // Input adjacency matrix
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            cin >> cost[i][j];

    int visited[10] = {0};
    visited[0] = 1;

    int minCost = 0;

    for (int edge = 0; edge < n - 1; edge++) {
        int min = INT_MAX, a = -1, b = -1;

        for (int i = 0; i < n; i++) {
            if (visited[i]) {
                for (int j = 0; j < n; j++) {
                    if (!visited[j] && cost[i][j] < min) {
                        min = cost[i][j];
                        a = i;
                        b = j;
                    }
                }
            }
        }

        cout << a << " - " << b << " = " << min << endl;

        minCost += min;
        visited[b] = 1;
    }

    cout << "Minimum Cost = " << minCost;

    return 0;
}






<<<<<<Kruskals>>>>>>>
#include <bits/stdc++.h>
using namespace std;

int parent[10];

int find(int x) {
    if (parent[x] == x)
        return x;
    return find(parent[x]);
}

int main() {
    int n, cost[10][10];
    cin >> n;

    for (int i = 0; i < n; i++) {
        parent[i] = i;
        for (int j = 0; j < n; j++) {
            cin >> cost[i][j];
        }
    }

    int minCost = 0;

    for (int e = 0; e < n - 1; e++) {
        int min = INT_MAX, a, b;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (find(i) != find(j) && cost[i][j] < min) {
                    min = cost[i][j];
                    a = i;
                    b = j;
                }
            }
        }

        parent[find(a)] = find(b);
        cout << a << " - " << b << " = " << min << endl;
        minCost += min;
    }

    cout << "Minimum Cost = " << minCost;
}



<<<<<<<Kruskals>>>>>>>
#include <bits/stdc++.h>
using namespace std;

int parent[10];

int find(int x) {
    if (parent[x] == x)
        return x;
    return find(parent[x]);
}

int main() {
    int n, cost[10][10];
    cin >> n;

    for (int i = 0; i < n; i++) {
        parent[i] = i;
        for (int j = 0; j < n; j++) {
            cin >> cost[i][j];
        }
    }

    int minCost = 0;

    for (int e = 0; e < n - 1; e++) {
        int min = INT_MAX, a, b;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (find(i) != find(j) && cost[i][j] < min) {
                    min = cost[i][j];
                    a = i;
                    b = j;
                }
            }
        }

        parent[find(a)] = find(b);
        cout << a << " - " << b << " = " << min << endl;
        minCost += min;
    }

    cout << "Minimum Cost = " << minCost;
}

<<<<<<<<<<<mcm>>>>>>>>>>>>


#include <bits/stdc++.h>
using namespace std;

int mcm(int a[], int n) {
    int dp[10][10];

    for (int i = 1; i < n; i++)
        dp[i][i] = 0;

    for (int len = 2; len < n; len++) {
        for (int i = 1; i < n - len + 1; i++) {
            int j = i + len - 1;
            dp[i][j] = INT_MAX;

            for (int k = i; k < j; k++) {
                int cost = dp[i][k] + dp[k + 1][j]
                         + a[i - 1] * a[k] * a[j];

                dp[i][j] = min(dp[i][j], cost);
            }
        }
    }

    return dp[1][n - 1];
}

int main() {
    int a[] = {10, 20, 30, 40, 30};
    int n = 5;

    cout << mcm(a, n);

    return 0;
}



