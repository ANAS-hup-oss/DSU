class DSU {
    public:
    vector<int> parent;
    vector<int> size;
    DSU(int n) {
        parent.resize(n);
        size.resize(n, 1);
        for (int i = 0; i < n; i++)
            parent[i] = i;
    }
    int find(int x) {
        if (parent[x] == x)return x;
        return parent[x]=find(parent[x]);
    }
    bool merge(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);

        if (rootX == rootY) return 0;

        if (size[rootX] < size[rootY])
            swap(rootX, rootY);

        parent[rootY] = rootX;
        size[rootX] += size[rootY];
        return 1;
    }

    bool same_set(int x, int y) {
        return find(x) == find(y);
    }

    int getSize(int x) {
        return size[find(x)];
    }
};
