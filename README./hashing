# Bank Account Management System using Hashing

# Account Class
class Account:
    def __init__(self, acc_no, name, balance):
        self.acc_no = acc_no
        self.name = name
        self.balance = balance

    def __str__(self):
        return f"{self.acc_no} | {self.name} | Rs.{self.balance}"


# Chaining Hashing
class ChainingHash:
    def __init__(self, size=7):
        self.size = size
        self.table = [[] for _ in range(size)]

    def h(self, key):
        return key % self.size

    def search(self, key):
        for a in self.table[self.h(key)]:
            if a.acc_no == key:
                return a
        return None

    def insert(self, acc):
        if self.search(acc.acc_no):
            print("Duplicate account number!")
            return

        self.table[self.h(acc.acc_no)].append(acc)
        print("Account inserted successfully.")

    def delete(self, key):
        a = self.search(key)

        if a:
            self.table[self.h(key)].remove(a)
            return True

        return False

    def display(self):
        for i, chain in enumerate(self.table):
            print(
                i, "->",
                " -> ".join(str(a) for a in chain) or "empty"
            )


# Open Addressing Hashing
class OpenAddressHash:
    DELETED = object()

    def __init__(self, size=7, mode="linear"):
        self.size = size
        self.mode = mode
        self.table = [None] * size

    def probe(self, key, i):
        step = i if self.mode == "linear" else i * i
        return (key % self.size + step) % self.size

    def search(self, key):
        for i in range(self.size):
            idx = self.probe(key, i)
            slot = self.table[idx]

            if slot is None:
                return None

            if slot is not self.DELETED and slot.acc_no == key:
                return slot

        return None

    def insert(self, acc):
        if self.search(acc.acc_no):
            print("Duplicate account number!")
            return

        for i in range(self.size):
            idx = self.probe(acc.acc_no, i)

            if self.table[idx] is None or self.table[idx] is self.DELETED:
                self.table[idx] = acc
                print("Account inserted successfully.")
                return

        print("Hash table is full / no free slot found!")

    def delete(self, key):
        for i in range(self.size):
            idx = self.probe(key, i)
            slot = self.table[idx]

            if slot is None:
                return False

            if slot is not self.DELETED and slot.acc_no == key:
                self.table[idx] = self.DELETED
                return True

        return False

    def display(self):
        for i, s in enumerate(self.table):
            if s is None:
                print(i, "-> empty")

            elif s is self.DELETED:
                print(i, "-> deleted")

            else:
                print(i, "->", s)


# Main Function
def main():

    print("\n1. Chaining")
    print("2. Linear Probing")
    print("3. Quadratic Probing")

    c = input("Choose method: ")

    if c == "1":
        ht = ChainingHash(7)

    elif c == "2":
        ht = OpenAddressHash(7, "linear")

    elif c == "3":
        ht = OpenAddressHash(7, "quadratic")

    else:
        print("Invalid choice!")
        return

    while True:

        print("\n1. Insert")
        print("2. Search")
        print("3. Delete")
        print("4. Display")
        print("5. Exit")

        ch = input("Enter choice: ")

        if ch == "1":
            acc_no = int(input("Account No: "))
            name = input("Name: ")
            balance = float(input("Balance: "))

            ht.insert(Account(acc_no, name, balance))

        elif ch == "2":
            key = int(input("Account No: "))
            r = ht.search(key)

            print(r if r else "Record not found")

        elif ch == "3":
            key = int(input("Account No: "))

            if ht.delete(key):
                print("Deleted successfully.")
            else:
                print("Record not found")

        elif ch == "4":
            ht.display()

        elif ch == "5":
            print("Program Terminated.")
            break

        else:
            print("Invalid choice!")


# Program Execution
main()
