def heapify(prices, n, i, is_max_heap):
    extreme = i
    left = 2 * i + 1
    right = 2 * i + 2

    # Check left child
    if left < n:
        if ((is_max_heap and prices[left] > prices[extreme]) or
            (not is_max_heap and prices[left] < prices[extreme])):
            extreme = left

    # Check right child
    if right < n:
        if ((is_max_heap and prices[right] > prices[extreme]) or
            (not is_max_heap and prices[right] < prices[extreme])):
            extreme = right

    # Swap and continue heapifying
    if extreme != i:
        prices[i], prices[extreme] = prices[extreme], prices[i]
        heapify(prices, n, extreme, is_max_heap)


def heap_sort(prices, ascending=True):
    n = len(prices)

    # Build heap
    for i in range(n // 2 - 1, -1, -1):
        heapify(prices, n, i, ascending)

    # Extract elements
    for i in range(n - 1, 0, -1):
        prices[0], prices[i] = prices[i], prices[0]
        heapify(prices, i, 0, ascending)

    return prices


# Main Program
prices = []

while True:
    print("\n===== PRODUCT PRICE HEAP SORT =====")
    print("1. Enter Product Prices")
    print("2. Display Prices in Ascending Order")
    print("3. Display Prices in Descending Order")
    print("4. Exit")

    choice = input("Enter your choice (1-4): ")

    if choice == "1":
        prices = list(map(float, input(
            "Enter product prices separated by spaces: "
        ).split()))

        print("Product prices entered successfully!")

    elif choice == "2":
        if prices:
            result = heap_sort(prices.copy(), True)
            print("Product prices in ascending order:", result)
        else:
            print("Please enter product prices first!")

    elif choice == "3":
        if prices:
            result = heap_sort(prices.copy(), False)
            print("Product prices in descending order:", result)
        else:
            print("Please enter product prices first!")

    elif choice == "4":
        print("Exiting program. Thank you!")
        break

    else:
        print("Invalid choice! Please enter a number from 1 to 4.")
