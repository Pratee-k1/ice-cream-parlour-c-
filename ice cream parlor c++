#include <stdio.h>
#include <vector>
#include <algorithm>
#define NOT_FOUND -1
using namespace std;

struct ice_cream {
    int cost;
    int idx;

    ice_cream() {}
    ice_cream(int cost, int idx):cost(cost), idx(idx) {}
};

bool operator <(const ice_cream &a, const ice_cream &b) {
    return a.cost < b.cost || (a.cost == b.cost && a.idx < b.idx);
}

int search(int l, int r, int need, vector <ice_cream> &v) {
    while(l <= r) {
        int mid = (l + r) / 2;
        if (v[mid].cost == need) {
            return v[mid].idx;
        } else if (v[mid].cost < need) {
            l = mid + 1;
        } else {
            r = mid - 1;
        }
    }
    return NOT_FOUND;
}

int main(void) {
    int t;
    int m, n;
    int cost;
    vector <ice_cream> v;

    scanf(" %d", &t);
    for (int test = 0; test < t; test++) {
        scanf(" %d", &m);
        scanf(" %d", &n);
        v.clear();
        for (int i = 0; i < n; i++) {
            scanf(" %d", &cost);
            v.push_back(ice_cream(cost, i + 1));
        }
        sort(v.begin(), v.end());
        for (int i = 0; i < (int)v.size(); i++) {
            int cost = v[i].cost;
            int need = m - cost;
            int idx = search(i + 1, (int)v.size() - 1, need, v);
            if (idx != NOT_FOUND) {
                printf("%d %d\n", min(v[i].idx, idx), max(v[i].idx, idx));
                break;
            }
        }
    }
    return 0;
}
