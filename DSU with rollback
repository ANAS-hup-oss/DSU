class DSU {
public:
    vector<int> parent, size;

    struct Change {
        int rootX, rootY;
        int sizeX;
    };

    vector<Change> history;

    DSU(int n) {
        parent.resize(n);
        size.resize(n, 1);

        for (int i = 0; i < n; i++)
            parent[i] = i;
    }

    int find(int x) {
        while (parent[x] != x)
            x = parent[x];

        return x;
    }

    bool merge(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);

        if (rootX == rootY) {
            history.push_back({-1, -1, -1});
            return false;
        }

        if (size[rootX] < size[rootY])
            swap(rootX, rootY);

        // Save old state
        history.push_back({
            rootX,
            rootY,
            size[rootX]
        });

        parent[rootY] = rootX;
        size[rootX] += size[rootY];

        return true;
    }

    void rollback() {
        auto [rootX, rootY, oldSize] = history.back();
        history.pop_back();

        // merge didn't change anything
        if (rootX == -1)
            return;

        parent[rootY] = rootY;
        size[rootX] = oldSize;
    }

    bool same_set(int x, int y) {
        return find(x) == find(y);
    }

    int getSize(int x) {
        return size[find(x)];
    }

    int snapshot() {
        return history.size();
    }

    void rollback(int snap) {
        while ((int)history.size() > snap)
            rollback();
    }
};
