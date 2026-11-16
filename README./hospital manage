from collections import deque

# Node Class
class Node:
    def __init__(self, patient_id, patient_name):
        self.patient_id = patient_id
        self.patient_name = patient_name
        self.left = None
        self.right = None


# Binary Search Tree Class
class BST:
    def __init__(self):
        self.root = None

    # 1. INSERTION
    def insert(self, patient_id, patient_name):
        new_node = Node(patient_id, patient_name)

        if self.root is None:
            self.root = new_node
            return

        current = self.root

        while True:
            if patient_id < current.patient_id:
                if current.left is None:
                    current.left = new_node
                    return
                else:
                    current = current.left

            elif patient_id > current.patient_id:
                if current.right is None:
                    current.right = new_node
                    return
                else:
                    current = current.right

            else:
                print("Patient ID already exists.")
                return

    # 2. SEARCH
    def search(self, patient_id):
        current = self.root

        while current is not None:
            if patient_id == current.patient_id:
                return current

            elif patient_id < current.patient_id:
                current = current.left

            else:
                current = current.right

        return None

    # 3. DELETE
    def delete(self, patient_id):
        self.root = self._delete_node(self.root, patient_id)

    def _delete_node(self, root, patient_id):
        if root is None:
            return root

        if patient_id < root.patient_id:
            root.left = self._delete_node(
                root.left, patient_id
            )

        elif patient_id > root.patient_id:
            root.right = self._delete_node(
                root.right, patient_id
            )

        else:
            # Case 1: No left child
            if root.left is None:
                return root.right

            # Case 2: No right child
            elif root.right is None:
                return root.left

            # Case 3: Two children
            successor = self._find_min(root.right)

            root.patient_id = successor.patient_id
            root.patient_name = successor.patient_name

            root.right = self._delete_node(
                root.right, successor.patient_id
            )

        return root

    # Find Minimum Node
    def _find_min(self, node):
        current = node

        while current.left is not None:
            current = current.left

        return current

    # 4. INORDER TRAVERSAL
    def inorder(self, node):
        if node is not None:
            self.inorder(node.left)

            print(
                node.patient_id,
                "-",
                node.patient_name,
                end=" | "
            )

            self.inorder(node.right)

    # 5. PREORDER TRAVERSAL
    def preorder(self, node):
        if node is not None:
            print(
                node.patient_id,
                "-",
                node.patient_name,
                end=" | "
            )

            self.preorder(node.left)
            self.preorder(node.right)

    # 6. POSTORDER TRAVERSAL
    def postorder(self, node):
        if node is not None:
            self.postorder(node.left)
            self.postorder(node.right)

            print(
                node.patient_id,
                "-",
                node.patient_name,
                end=" | "
            )

    # 7. DEPTH OF TREE
    def depth(self, node):
        if node is None:
            return 0

        left_depth = self.depth(node.left)
        right_depth = self.depth(node.right)

        return 1 + max(left_depth, right_depth)

    # 8. MIRROR TREE
    def create_mirror(self, node):
        if node is None:
            return None

        mirror_node = Node(
            node.patient_id,
            node.patient_name
        )

        mirror_node.left = self.create_mirror(node.right)
        mirror_node.right = self.create_mirror(node.left)

        return mirror_node

    # 9. COPY TREE
    def copy_tree(self, node):
        if node is None:
            return None

        new_node = Node(
            node.patient_id,
            node.patient_name
        )

        new_node.left = self.copy_tree(node.left)
        new_node.right = self.copy_tree(node.right)

        return new_node

    # 10. DISPLAY LEAF NODES
    def display_leaf_nodes(self, node):
        if node is None:
            return

        if node.left is None and node.right is None:
            print(
                node.patient_id,
                "-",
                node.patient_name,
                end=" | "
            )
            return

        self.display_leaf_nodes(node.left)
        self.display_leaf_nodes(node.right)

    # 11. LEVEL-WISE DISPLAY
    def level_order(self, node):
        if node is None:
            return

        queue = deque()
        queue.append(node)

        while queue:
            current = queue.popleft()

            print(
                current.patient_id,
                "-",
                current.patient_name,
                end=" | "
            )

            if current.left is not None:
                queue.append(current.left)

            if current.right is not None:
                queue.append(current.right)

        print()


# MAIN PROGRAM
bst = BST()

# Insert Patient Records
n = int(input("Enter number of patients: "))

for i in range(n):
    print("\nEnter details of Patient", i + 1)

    patient_id = int(input("Enter Patient ID: "))
    patient_name = input("Enter Patient Name: ")

    bst.insert(patient_id, patient_name)


# Display Original BST
print("\n========== ORIGINAL BST ==========")

print("\nInorder Traversal:")
bst.inorder(bst.root)

print("\n\nPreorder Traversal:")
bst.preorder(bst.root)

print("\n\nPostorder Traversal:")
bst.postorder(bst.root)


# Search
print("\n\n========== SEARCH ==========")

search_id = int(input("Enter Patient ID to search: "))
result = bst.search(search_id)

if result is not None:
    print(
        "Patient Found:",
        result.patient_id,
        "-",
        result.patient_name
    )
else:
    print("Patient not found.")


# Depth
print("\n========== TREE DEPTH ==========")
print("Depth of tree:", bst.depth(bst.root))


# Leaf Nodes
print("\n========== LEAF NODES ==========")
bst.display_leaf_nodes(bst.root)


# Level Order
print("\n\n========== LEVEL-WISE DISPLAY ==========")
bst.level_order(bst.root)


# Copy Tree
print("\n========== COPY OF TREE ==========")

copy_root = bst.copy_tree(bst.root)

print("Inorder traversal of copied tree:")
bst.inorder(copy_root)


# Mirror Tree
print("\n\n========== MIRROR TREE ==========")

mirror_root = bst.create_mirror(bst.root)

print("Inorder traversal of mirror tree:")
bst.inorder(mirror_root)


# Delete Patient
print("\n\n========== DELETE ==========")

delete_id = int(input("Enter Patient ID to delete: "))

print("Deleting Patient ID:", delete_id)

bst.delete(delete_id)

print("\nInorder traversal after deletion:")
bst.inorder(bst.root)

print("\n\nLevel-wise display after deletion:")
bst.level_order(bst.root)
