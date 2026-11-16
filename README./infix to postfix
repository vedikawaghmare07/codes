#include <iostream>
#include <string>
#include <cctype>
#include <cmath>
using namespace std;

// Node for Singly Linked List
struct Node {
    char data;
    Node* next;

    Node(char value) {
        data = value;
        next = nullptr;
    }
};

// Stack ADT using Singly Linked List
class Stack {
private:
    Node* top;

public:

    // Constructor
    Stack() {
        top = nullptr;
    }

    // Check whether stack is empty
    bool isEmpty() {
        return top == nullptr;
    }

    // Push element into stack
    void push(char value) {
        Node* newNode = new Node(value);
        newNode->next = top;
        top = newNode;
    }

    // Remove and return top element
    char pop() {
        if (isEmpty()) {
            return '\0';
        }

        Node* temp = top;
        char value = temp->data;
        top = top->next;
        delete temp;

        return value;
    }

    // Return top element
    char peek() {
        if (isEmpty()) {
            return '\0';
        }

        return top->data;
    }

    // Destructor
    ~Stack() {
        while (!isEmpty()) {
            pop();
        }
    }
};

// Return precedence of operator
int precedence(char op) {
    if (op == '^')
        return 3;
    if (op == '*' || op == '/')
        return 2;
    if (op == '+' || op == '-')
        return 1;

    return 0;
}

// Check whether character is operator
bool isOperator(char ch) {
    return ch == '+' || ch == '-' ||
           ch == '*' || ch == '/' || ch == '^';
}

// Convert Infix Expression to Postfix
string infixToPostfix(string infix) {
    Stack st;
    string postfix = "";

    for (int i = 0; i < infix.length(); i++) {
        char ch = infix[i];

        // Ignore spaces
        if (ch == ' ')
            continue;

        // If operand, add directly
        if (isalnum(ch)) {
            postfix += ch;
            postfix += ' ';
        }

        // Opening bracket
        else if (ch == '(') {
            st.push(ch);
        }

        // Closing bracket
        else if (ch == ')') {
            while (!st.isEmpty() && st.peek() != '(') {
                postfix += st.pop();
                postfix += ' ';
            }

            if (!st.isEmpty() && st.peek() == '(') {
                st.pop();
            }
        }

        // If operator
        else if (isOperator(ch)) {
            while (!st.isEmpty() &&
                   st.peek() != '(' &&
                   (precedence(st.peek()) > precedence(ch) ||
                   (precedence(st.peek()) == precedence(ch) && ch != '^'))) {

                postfix += st.pop();
                postfix += ' ';
            }

            st.push(ch);
        }
    }

    // Pop remaining operators
    while (!st.isEmpty()) {
        postfix += st.pop();
        postfix += ' ';
    }

    return postfix;
}

// Evaluate Postfix Expression
double evaluatePostfix(string postfix) {
    double values[100];
    int top = -1;

    for (int i = 0; i < postfix.length(); i++) {
        char ch = postfix[i];

        // Ignore spaces
        if (ch == ' ')
            continue;

        // If operand
        if (isdigit(ch)) {
            values[++top] = ch - '0';
        }

        // If operator
        else if (isOperator(ch)) {
            double operand2 = values[top--];
            double operand1 = values[top--];

            double result = 0;

            switch (ch) {
                case '+':
                    result = operand1 + operand2;
                    break;

                case '-':
                    result = operand1 - operand2;
                    break;

                case '*':
                    result = operand1 * operand2;
                    break;

                case '/':
                    result = operand1 / operand2;
                    break;

                case '^':
                    result = pow(operand1, operand2);
                    break;
            }

            values[++top] = result;
        }
    }

    return values[top];
}

// Main Function
int main() {
    string infix;

    cout << "Enter an arithmetic expression: ";
    getline(cin, infix);

    // Convert Infix to Postfix
    string postfix = infixToPostfix(infix);

    cout << "\nInfix Expression: " << infix;
    cout << "\nPostfix Expression: " << postfix;

    // Evaluate Postfix
    double result = evaluatePostfix(postfix);

    cout << "\nResult: " << result << endl;

    return 0;
}
