# store-
store's clothing accounting system
class ClothingItem:
    def __init__(self, name):
        self.name = name
        self.delivered = 0
        self.sold = 0
        self.defects = 0
        self.period_stay = 0

    def deliver(self, quantity):
        self.delivered += quantity

    def sell(self, quantity):
        if self.delivered >= quantity:
            self.sold += quantity
            self.delivered -= quantity
        else:
            print(f"Insufficient quantity of {self.name} available.")

    def add_defect(self, quantity):
        self.defects += quantity

    def update_period_stay(self, days):
        self.period_stay += days

    def calculate_stock(self):
        return self.delivered - self.sold - self.defects


# Example usage:
clothing_items = []

# Create clothing items
item1 = ClothingItem("T-Shirt")
item2 = ClothingItem("Jeans")
item3 = ClothingItem("Jacket")

# Add clothing items to the list
clothing_items.append(item1)
clothing_items.append(item2)
clothing_items.append(item3)

# Simulate transactions
item1.deliver(100)
item1.sell(50)
item1.add_defect(5)
item1.update_period_stay(10)

item2.deliver(80)
item2.sell(70)
item2.add_defect(2)
item2.update_period_stay(15)

item3.deliver(50)
item3.sell(30)
item3.add_defect(1)
item3.update_period_stay(20)

# Calculate and display stock
print("Current Stock:")
for item in clothing_items:
    stock = item.calculate_stock()
    print(f"{item.name}: {stock}")

# Find the most and least sold items
most_sold = max(clothing_items, key=lambda item: item.sold)
least_sold = min(clothing_items, key=lambda item: item.sold)

print(f"\nMost Sold Item: {most_sold.name} (Sold: {most_sold.sold})")
print(f"Least Sold Item: {least_sold.name} (Sold: {least_sold.sold})")
