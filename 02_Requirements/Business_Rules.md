- Calculation Rule ID: B-ORD-01
Rule Name: Calculate total order value
Description: The total order value is calculated based on product price, quantity, tax, and shipping fee.
Trigger: When adding/editing/deleting products in the shopping cart, or when changing the delivery address. Formula: Total amount = Σ (Unit price × Quantity) + Shipping fee - Discount VAT = (Total amount - Discount) × 10% Final payment = Total amount + VAT Business Constraint - Shipping fee = 30,000 if the address is within the city, 50,000 if outside the city - Maximum discount is no more than 50% of the total amount

- Permission Rule ID: B-AUTH-02
Rule Name: Product deletion permission
Description: Only users with the appropriate role are allowed to delete products from the system.
Trigger: When a user performs the action of deleting a product.
Condition: The user's role must Admin or Warehouse Manager
Action: Allows deleting a product (or changing it to "Discontinued" status instead of physically deleting it)
Exception: If the role is Salesperson: hide the delete button or display the message "You do not have permission to perform this action"