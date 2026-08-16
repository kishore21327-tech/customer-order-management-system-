


# Customer Order Management using Queue (FIFO)

from collections import deque

class CustomerOrderQueue:
    def __init__(self):
        self.queue = deque()

    # Add new order
    def enqueue(self, order_id, customer_name, item):
        order = {
            "Order ID": order_id,
            "Customer Name": customer_name,
            "Item": item
        }
        self.queue.append(order)
        print("\n✅ Order added successfully!")

    # Process order
    def dequeue(self):
        if self.is_empty():
            print("\n⚠ No orders to process.")
        else:
            order = self.queue.popleft()
            print("\n✅ Processing Order:")
            print(f"Order ID: {order['Order ID']}")
            print(f"Customer Name: {order['Customer Name']}")
            print(f"Item: {order['Item']}")

    # Display all orders
    def display(self):
        if self.is_empty():
            print("\n⚠ No pending orders.")
        else:
            print("\n📋 Pending Orders:")
            for i, order in enumerate(self.queue, start=1):
                print(f"\nOrder {i}")
                print(f"Order ID: {order['Order ID']}")
                print(f"Customer Name: {order['Customer Name']}")
                print(f"Item: {order['Item']}")

    # Peek next order
    def peek(self):
        if self.is_empty():
            print("\n⚠ Queue is empty.")
        else:
            order = self.queue[0]
            print("\n🔎 Next Order to Process:")
            print(f"Order ID: {order['Order ID']}")
            print(f"Customer Name: {order['Customer Name']}")
            print(f"Item: {order['Item']}")

    # Check if empty
    def is_empty(self):
        return len(self.queue) == 0


# ---------------- Main Program ----------------

def main():
    system = CustomerOrderQueue()

    while True:
        print("\n===== CUSTOMER ORDER MANAGEMENT =====")
        print("1. Add Order")
        print("2. Process Order")
        print("3. Display Orders")
        print("4. Peek Next Order")
        print("5. Exit")

        try:
            choice = int(input("Enter your choice (1-5): "))
        except ValueError:
            print("❌ Please enter a valid number.")
            continue

        if choice == 1:
            order_id = input("Enter Order ID: ")
            customer_name = input("Enter Customer Name: ")
            item = input("Enter Item Name: ")
            system.enqueue(order_id, customer_name, item)

        elif choice == 2:
            system.dequeue()

        elif choice == 3:
            system.display()

        elif choice == 4:
            system.peek()

        elif choice == 5:
            print("\nThank you! Exiting program...")
            break

        else:
            print("❌ Invalid choice. Please select between 1 and 5.")


if __name__ == "__main__":
    main()



# customer-order-management-system-
to make easier order and shipping 
