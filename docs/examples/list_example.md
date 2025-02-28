# Medium Articles Code Extract

## App using Data Structures Inventory

~~~python
inventory = []

def add_item(item_id, name, quantity, price):
    item = {'id': item_id, 'name': name, 'quantity': quantity, 'price': price}
    inventory.append(item)

def remove_item(item_id):
    global inventory
    for item in inventory:
        if item['id'] == item_id:
            inventory.remove(item)
            break

def view_inventory():
    for item in inventory:
        print(
            f"ID: {item['id']}, Name: {item['name']}, Quantity: {item['quantity']}, Price: {item['price']}"
        )

while True:
    print("1. Add Item")
    print("2. Remove Item")
    print("3. Update Quantity")
    print("4. View Inventory")
    print("5. Exit")
    choice = input("Enter choice:")
    # handle choices...
    if choice == '5':
        break
    else:
        print("Invalid choice. Please try again.")

~~~

