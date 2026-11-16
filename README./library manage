#include <iostream>
#include <string>
using namespace std;

struct Book {
    int bookID;
    string title;
    string author;
    string status;
};

// Function to Display Books
void displayBooks(Book books[], int n) {
    cout << "\n------------------------------------------------------\n";
    cout << "Book ID\tTitle\t\tAuthor\t\tStatus\n";
    cout << "------------------------------------------------------\n";

    for (int i = 0; i < n; i++) {
        cout << books[i].bookID << "\t";
        cout << books[i].title << "\t\t";
        cout << books[i].author << "\t\t";
        cout << books[i].status << endl;
    }
}

// Linear Search
void linearSearch(Book books[], int n, int key) {
    bool found = false;

    for (int i = 0; i < n; i++) {
        if (books[i].bookID == key) {
            cout << "\nBook Found (Linear Search)\n";
            cout << "Book ID: " << books[i].bookID << endl;
            cout << "Title: " << books[i].title << endl;
            cout << "Author: " << books[i].author << endl;
            cout << "Status: " << books[i].status << endl;

            found = true;
            break;
        }
    }

    if (!found)
        cout << "\nBook Not Found.\n";
}

// Bubble Sort (Ascending Book ID)
void bubbleSort(Book books[], int n) {
    Book temp;

    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - 1; j++) {
            if (books[j].bookID > books[j + 1].bookID) {
                temp = books[j];
                books[j] = books[j + 1];
                books[j + 1] = temp;
            }
        }
    }
}

// Binary Search
void binarySearch(Book books[], int n, int key) {
    int low = 0, high = n - 1;

    while (low <= high) {
        int mid = (low + high) / 2;

        if (books[mid].bookID == key) {
            cout << "\nBook Found (Binary Search)\n";
            cout << "Book ID: " << books[mid].bookID << endl;
            cout << "Title: " << books[mid].title << endl;
            cout << "Author: " << books[mid].author << endl;
            cout << "Status: " << books[mid].status << endl;
            return;
        }
        else if (key < books[mid].bookID) {
            high = mid - 1;
        }
        else {
            low = mid + 1;
        }
    }

    cout << "\nBook Not Found.\n";
}

// Insertion Sort (Book Title)
void insertionSort(Book books[], int n) {
    Book key;

    for (int i = 1; i < n; i++) {
        key = books[i];
        int j = i - 1;

        while (j >= 0 && books[j].title > key.title) {
            books[j + 1] = books[j];
            j--;
        }

        books[j + 1] = key;
    }
}

// Main Function
int main() {
    int n, key;

    cout << "Enter number of books: ";
    cin >> n;

    Book books[n];

    for (int i = 0; i < n; i++) {
        cout << "\nEnter details of Book " << i + 1 << endl;

        cout << "Book ID: ";
        cin >> books[i].bookID;

        cin.ignore();

        cout << "Book Title: ";
        getline(cin, books[i].title);

        cout << "Author Name: ";
        getline(cin, books[i].author);

        cout << "Availability Status: ";
        getline(cin, books[i].status);
    }

    cout << "\nOriginal Book Records";
    displayBooks(books, n);

    // Linear Search
    cout << "\nEnter Book ID to Search (Linear Search): ";
    cin >> key;

    linearSearch(books, n, key);

    // Bubble Sort
    bubbleSort(books, n);

    cout << "\nBooks Sorted by Book ID (Bubble Sort):";
    displayBooks(books, n);

    // Binary Search
    cout << "\nEnter Book ID to Search (Binary Search): ";
    cin >> key;

    binarySearch(books, n, key);

    // Insertion Sort
    insertionSort(books, n);

    cout << "\nBooks Sorted by Book Title (Insertion Sort):";
    displayBooks(books, n);

    return 0;
}
