#include <iostream>
#include <cstdlib>
#include <cstring>
using namespace std;

struct node {
    char label[10];
    int ch_count;
    struct node *child[10];
} *root;

class GT {
public:
    void create_tree();
    void display(node *r1);
    int find_height(node *r1);

    GT() {
        root = NULL;
    }
};

void GT::create_tree() {
    int tchapters, i, j;
    root = new node;
    cout << "Enter name of book: ";
    cin >> root->label;
    cout << "Enter no. of chapters in book: ";
    cin >> tchapters;
    root->ch_count = tchapters;
    for (i = 0; i < tchapters; i++) {
        root->child[i] = new node;
        cout << "Enter Chapter name: ";
        cin >> root->child[i]->label;
        cout << "Enter no. of sections in Chapter " << root->child[i]->label << ": ";
        cin >> root->child[i]->ch_count;
        for (j = 0; j < root->child[i]->ch_count; j++) {
            root->child[i]->child[j] = new node;
            cout << "Enter Section " << j + 1 << " name: ";
            cin >> root->child[i]->child[j]->label;
            root->child[i]->child[j]->ch_count = 0; // No further subsections for simplicity
        }
    }
}

void GT::display(node *r1) {
    int i, j, tchapters;
    if (r1 != NULL) {
        cout << "\n-----Book Hierarchy-----";
        cout << "\nBook title: " << r1->label;
        tchapters = r1->ch_count;
        for (i = 0; i < tchapters; i++) {
            cout << "\n Chapter " << i + 1 << ": " << r1->child[i]->label;
            cout << "\n  Sections:";
            for (j = 0; j < r1->child[i]->ch_count; j++) {
                cout << "\n   " << r1->child[i]->child[j]->label;
            }
        }
        cout << endl;
    }
}

int GT::find_height(node *r1) {
    if (r1 == NULL)
        return 0;

    int max_height = 0;
    for (int i = 0; i < r1->ch_count; i++) {
        int child_height = find_height(r1->child[i]);
        if (child_height > max_height)
            max_height = child_height;
    }

    return max_height + 1;
}

int main() {
    int choice;
    GT gt;

    while (1) {
        cout << "-----------------" << endl;
        cout << "Book Tree Creation" << endl;
        cout << "-----------------" << endl;
        cout << "1. Create" << endl;
        cout << "2. Display" << endl;
        cout << "3. Find Height of Tree" << endl;
        cout << "4. Quit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
        case 1:
            gt.create_tree();
            break;
        case 2:
            gt.display(root);
            break;
        case 3:
            cout << "Height of the tree: " << gt.find_height(root) << endl;
            break;
        case 4:
            exit(1);
        default:
            cout << "Wrong choice" << endl;
        }
    }
}
