#include <iostream>
#include <stack>
#include <string>
#include <cctype>

using namespace std;

struct Node {
    char data;
    Node* left;
    Node* right;
    
    Node(char value) {
        data = value;
        left = right = nullptr;
    }
};

bool isOperator(char ch) {
    return (ch == '+' || ch == '-' || ch == '*' || ch == '/');
}

Node* constructTree(const string& prefix) {
    stack<Node*> s;
    for (int i = prefix.length() - 1; i >= 0; i--) {
        char ch = prefix[i];
        if (isalnum(ch)) {
            s.push(new Node(ch));
        } else if (isOperator(ch)) {
            Node* left = s.top(); s.pop();
            Node* right = s.top(); s.pop();
            Node* node = new Node(ch);
            node->left = left;
            node->right = right;
            s.push(node);
        }
    }
    return s.top();
}

void postorderTraversal(Node* root) {
    if (!root) return;
    stack<Node*> s1, s2;
    s1.push(root);
    while (!s1.empty()) {
        Node* node = s1.top(); s1.pop();
        s2.push(node);
        if (node->left) s1.push(node->left);
        if (node->right) s1.push(node->right);
    }
    while (!s2.empty()) {
        cout << s2.top()->data << " ";
        s2.pop();
    }
    cout << endl;
}

void inorderTraversal(Node* root) {
    if (root) {
        if (isOperator(root->data)) cout << "(";
        inorderTraversal(root->left);
        cout << root->data << " ";
        inorderTraversal(root->right);
        if (isOperator(root->data)) cout << ")";
    }
}

void preorderTraversal(Node* root) {
    if (!root) return;
    stack<Node*> s;
    s.push(root);
    while (!s.empty()) {
        Node* node = s.top(); s.pop();
        cout << node->data << " ";
        if (node->right) s.push(node->right);
        if (node->left) s.push(node->left);
    }
    cout << endl;
}

void deleteTree(Node* root) {
    if (!root) return;
    deleteTree(root->left);
    deleteTree(root->right);
    delete root;
}

int main() {
    Node* root = nullptr;
    string prefix;
    int choice;
    
    do {
        cout << "\nMenu:\n";
        cout << "1. Enter Prefix Expression & Construct Tree\n";
        cout << "2. Postorder Traversal\n";
        cout << "3. Inorder (Infix) Traversal\n";
        cout << "4. Preorder Traversal\n";
        cout << "5. Delete Tree\n";
        cout << "6. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;
        
        switch (choice) {
            case 1:
                cout << "Enter a prefix expression: ";
                cin >> prefix;
                if (root) deleteTree(root);
                root = constructTree(prefix);
                break;
            case 2:
                cout << "Postorder traversal: ";
                postorderTraversal(root);
                break;
            case 3:
                cout << "Inorder (Infix) traversal: ";
                inorderTraversal(root);
                cout << endl;
                break;
            case 4:
                cout << "Preorder traversal: ";
                preorderTraversal(root);
                break;
            case 5:
                cout << "Deleting tree...\n";
                deleteTree(root);
                root = nullptr;
                break;
            case 6:
                cout << "Exiting...\n";
                break;
            default:
                cout << "Invalid choice! Please try again.\n";
        }
    } while (choice != 6);
    
    deleteTree(root);
    return 0;
}
