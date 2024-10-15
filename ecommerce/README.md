# E-Commerce Order Management and Tracking

In an e-commerce platform, AI can interact with inventory, payment, and shipping APIs to automate the complete order lifecycle.

## Prompt

`Prompt:` "Order a new iPhone 15, pay for it with my saved card, and let me know when it will arrive."

## Functions:

Simulates checking the inventory for an item like "iPhone 15". It returns the available quantity if the item is in stock, or indicates it's out of stock.

### Check Inventory

```python
# Mock implementation of the check_inventory function
def check_inventory(item: str):
    # Simulate checking inventory for the given item
    inventory = {
        "iPhone 15": 50,  # 50 units of iPhone 15 available
        "MacBook Pro": 20
    }
    available_quantity = inventory.get(item, 0)
    if available_quantity > 0:
        return f"{item} is in stock. Available quantity: {available_quantity}."
    else:
        return f"{item} is out of stock."
```

### Place Order

Places an order for the specified item and quantity, using the given payment method (e.g., "Credit Card"). It generates a mock order_id and confirms the order placement.

```python
# Mock implementation of the place_order function
def place_order(item: str, quantity: int, payment_method: str):
    # Simulate placing an order for the item
    if quantity <= 0:
        return "Invalid order. Quantity must be greater than 0."

    order_id = f"ORD-{item[:3].upper()}-{quantity}-{payment_method[:3].upper()}"
    return f"Order placed for {quantity} units of {item} using {payment_method}. Order ID: {order_id}"
```
    get_shipping_estimate(order_id: str): Retrieves an estimated delivery date.

### Get Shipping Estimate

 Retrieves the estimated delivery date for the provided order_id. It returns a mock shipping estimate based on the order ID.

```python
# Mock implementation of the get_shipping_estimate function
def get_shipping_estimate(order_id: str):
    # Simulate retrieving the shipping estimate for the given order ID
    shipping_estimates = {
        "ORD-IPH-1-CRE": "Expected delivery by October 18th.",
        "ORD-MAC-2-PAY": "Expected delivery by October 20th."
    }
    return shipping_estimates.get(order_id, "Shipping estimate not available for this order.")

# Example usage
item = "iPhone 15"
quantity = 1
payment_method = "Credit Card"

# Call the functions
inventory_status = check_inventory(item)
print(inventory_status)

if "in stock" in inventory_status:
    order_confirmation = place_order(item, quantity, payment_method)
    print(order_confirmation)

    # Assume the order ID from the order confirmation is parsed
    order_id = order_confirmation.split("Order ID: ")[1]
    shipping_estimate = get_shipping_estimate(order_id)
    print(shipping_estimate)
```
### Workflow:

1. AI calls `check_inventory("iPhone 15")` to ensure the product is available.
2. It uses `place_order("iPhone 15", 1, "saved_card")` to complete the purchase.
3. Finally, `get_shipping_estimate(order_id)` is used to inform the user of the expected delivery.

## Response:

`Response:` "Your order for the iPhone 15 has been placed and paid for. It will be delivered by October 18th."