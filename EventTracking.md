---

### **4. EventTracking.md**

# Event Tracking Setup

## Standard Events

Implement the following standard events using the `facebook_app_events` plugin.

### 1. Search

- **When:** User searches for restaurants or food items.
- **Implementation:**

  ```dart
  FacebookAppEvents().logEvent(
    name: 'fb_mobile_search',
    parameters: {
      'fb_search_string': searchQuery,
      'content_type': contentType, // 'restaurant' or 'food_item'
    },
  );
  ```

### 2. View Content

- **When:** User views a restaurant or menu item.
- **Implementation:**

  ```dart
  FacebookAppEvents().logEvent(
  name: 'fb_mobile_content_view',
  parameters: {
    'content_id': contentId,
    'content_type': contentType, // 'restaurant' or 'menu_item'
  },
  );
   ```
  ### 3. Add to Cart

- **When:** User adds a food item to the cart.
- **Implementation:**

  ```dart
  FacebookAppEvents().logEvent(
  name: 'fb_mobile_add_to_cart',
  parameters: {
    'content_id': itemId,
    'content_type': 'menu_item',
    'value': price,
    'currency': 'USD', // or appropriate currency code
  },
  );
   ```
  ### 4. Initiate Checkout

- **When:** User begins the checkout process.
- **Implementation:**

  ```dart
  FacebookAppEvents().logEvent(
  name: 'fb_mobile_initiated_checkout',
  parameters: {
    'num_items': numItems,
    'payment_info_available': paymentInfoAvailable ? '1' : '0',
    'currency': 'USD',
  },
  );
   ```
  ### 5. Purchase

- **When:** User completes an order.
- **Implementation:**

  ```dart
  FacebookAppEvents().logPurchase(
  amount: totalAmount,
  currency: 'USD',
  parameters: {
    'content_type': 'order',
    'content_id': orderId,
  },
  );
   ```

  ## Custom Events
  
    ### Table Reservation

- **When:** User reserves a table.
- **Implementation:**

  ```dart
  FacebookAppEvents().logEvent(
  name: 'ReserveTable',
  parameters: {
    'restaurant_id': restaurantId,
    'number_of_guests': numberOfGuests,
    'reservation_time': reservationTime.toIso8601String(),
  },
  );
   ```

  ## Event Implementation Examples

  **Logging a Purchase Event**

    ```dart
  FacebookAppEvents().logPurchase(
  amount: purchaseAmount,
  currency: 'USD',
  parameters: {
    'content_type': 'order',
    'content_id': orderId,
  },
  );
  ```
    
  **Logging User Consent Status**
   ```dart
   bool userConsent = await getUserConsentStatus();
   FacebookAppEvents.setAdvertiserTracking(enabled: userConsent);
    ```
   

  
