- As a customer, I want to cancel my order within a limited time so that I can change my decision if needed.

Acceptance Criteria 1: Canceling an order within the allowed time
Given the customer is logged in
And the order status is "Pending confirmation"
And the order was created less than 2 minutes ago
When the customer clicks the "Cancel order" button
Then the system displays a confirmation popup "Are you sure you want to cancel this order?"

And the customer confirms
Then the system updates the order status to "Cancelled"
And the system returns the product quantity to the warehouse
And the system sends an email confirming the order cancellation

Acceptance Criteria 2: Canceling an order after the time limit has passed
Given the customer is logged in
And the order status is "Shipping"
When the customer clicks the "Cancel order" button
Then the system displays the message "The order is being shipped and cannot be canceled. Please contact customer service."
And the system does not change the order status.

- As a customer, I want to buy goods immediately.

Acceptance Criteria 1: Buy immediately when goods are available.
Given the customer is logged in.
And the product has the status "In stock".
And the urgent order has the status "Empty".
When the customer clicks the "Buy" button,
Then the system displays a confirmation popup: "Do you confirm purchase immediately without adding to cart?"
And Customer confirms
Then the system updates the urgent order status to “awaiting payment”
And the system displays a payment popup
And Customer confirms
Then the system deducts the remaining product quantity from the inventory
And the system displays the message "Purchase successful"
And the system sends a purchase confirmation email

Acceptance Criteria 2: Purchase when inventory is depleted
Given Customer is logged in
And the product status is "Out of stock"
When Customer clicks the "Buy" button
Then the system displays the message "This product is currently out of stock and will be updated in the future. Please contact Customer Service for more details."

And the system does not change the product status

- As a customer, I want to add goods to the order list
Acceptance Criteria 1:add a good when its available.
And the product has the status "In stock".
When the customer clicks the "Add to cart" button.
Then the system displays a confirmation popup: "Add to cart?"
And Customer confirms
Then the system displays the message "Add successful"
