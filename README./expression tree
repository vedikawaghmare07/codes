# Node Class
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None


# Check Operator
def is_operator(x):
    return x in "+-*/"


# Operator Precedence
def precedence(x):
    if x in "*/":
        return 2
    if x in "+-":
        return 1
    return 0


# Infix to Postfix
def infix_to_postfix(exp):
    stack = []
    postfix = []
    i = 0

    while i < len(exp):

        if exp[i].isspace():
            i += 1
            continue

        if exp[i].isdigit() or exp[i] == '.':
            num = ""

            while i < len(exp) and (exp[i].isdigit() or exp[i] == '.'):
                num += exp[i]
                i += 1

            postfix.append(num)
            continue

        elif exp[i] == '(':
            stack.append(exp[i])

        elif exp[i] == ')':
            while stack and stack[-1] != '(':
                postfix.append(stack.pop())

            if stack:
                stack.pop()

        elif is_operator(exp[i]):
            while (stack and stack[-1] != '(' and
                   precedence(stack[-1]) >= precedence(exp[i])):
                postfix.append(stack.pop())

            stack.append(exp[i])

        i += 1

    while stack:
        postfix.append(stack.pop())

    return postfix


# Build Expression Tree
def build_tree(postfix):
    stack = []

    for item in postfix:
        node = Node(item)

        if not is_operator(item):
            stack.append(node)

        else:
            node.right = stack.pop()
            node.left = stack.pop()
            stack.append(node)

    return stack.pop()


# In-order Traversal
def inorder(root):
    if root:
        if is_operator(root.value):
            print("(", end="")

        inorder(root.left)
        print(root.value, end="")
        inorder(root.right)

        if is_operator(root.value):
            print(")", end="")


# Pre-order Traversal
def preorder(root):
    if root:
        print(root.value, end=" ")
        preorder(root.left)
        preorder(root.right)


# Post-order Traversal
def postorder(root):
    if root:
        postorder(root.left)
        postorder(root.right)
        print(root.value, end=" ")


# Evaluation
def evaluate(root):
    if not is_operator(root.value):
        return float(root.value)

    left = evaluate(root.left)
    right = evaluate(root.right)

    if root.value == '+':
        return left + right

    elif root.value == '-':
        return left - right

    elif root.value == '*':
        return left * right

    elif root.value == '/':
        return left / right


# Main Function
expression = input("Enter expression: ")

postfix = infix_to_postfix(expression)

root = build_tree(postfix)

print("\nPostfix Expression:", " ".join(postfix))

print("In-order   :", end=" ")
inorder(root)

print("\nPre-order  :", end=" ")
preorder(root)

print("\nPost-order :", end=" ")
postorder(root)

print("\nEvaluation :", evaluate(root))
