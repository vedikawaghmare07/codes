# Experiment No. 7: Minimum Spanning Tree

n = int(input("Enter number of offices: "))
m = int(input("Enter number of connections: "))

edges = []

print("Enter connections: office1 office2 cost")

for i in range(m):
    u, v, w = map(int, input().split())
    edges.append((u, v, w))


# Prim's Algorithm
def prim():
    visited = [False] * n
    visited[0] = True

    mst = []
    cost = 0

    while len(mst) < n - 1:
        minimum = float('inf')
        edge = None

        for u, v, w in edges:
            if visited[u] != visited[v] and w < minimum:
                minimum = w
                edge = (u, v, w)

        if edge is None:
            print("Graph is not connected!")
            return

        u, v, w = edge

        visited[u] = True
        visited[v] = True

        mst.append(edge)
        cost += w

    print("\nPrim's MST:")

    for u, v, w in mst:
        print(u, "-", v, "Cost:", w)

    print("Total cost using Prim's:", cost)


# Kruskal's Algorithm
def kruskal():
    parent = list(range(n))

    mst = []
    cost = 0

    def find(x):
        while parent[x] != x:
            x = parent[x]
        return x

    for u, v, w in sorted(edges, key=lambda e: e[2]):

        a = find(u)
        b = find(v)

        if a != b:
            mst.append((u, v, w))
            cost += w
            parent[a] = b

        if len(mst) == n - 1:
            break

    if len(mst) != n - 1:
        print("\nGraph is not connected!")
        return

    print("\nKruskal's MST:")

    for u, v, w in mst:
        print(u, "-", v, "Cost:", w)

    print("Total cost using Kruskal's:", cost)


# Main Program
if n > 0:
    prim()
    kruskal()
else:
    print("Number of offices must be positive.")
