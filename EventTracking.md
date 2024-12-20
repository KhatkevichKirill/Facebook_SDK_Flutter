---

### **4. EventTracking.md**

# Event Tracking Setup

## Standard Events

Implement the following standard events using the `facebook_app_events` plugin.

### 1. Search

- **When:** User searches for restaurants or food items.
- **Implementation:**

  ```dart
  FacebookAppEvents facebookAppEvents = FacebookAppEvents();
  
  facebookAppEvents.logEvent(
  name: 'fb_mobile_search',
  parameters: {
    'fb_search_string': 'pizza',
    'fb_content_type': 'food_item',
    // Если необходимо, можно добавить fb_content для уточнения результатов:
    // 'fb_content': '[{"id":"pizza-category"}]'
  },
  );
  ```

### 2. View Content

- **When:** User views a restaurant or menu item.
- **Implementation:**

  ```dart
  FacebookAppEvents facebookAppEvents = FacebookAppEvents();
  
  facebookAppEvents.logEvent(
  name: 'fb_mobile_content_view',
  parameters: {
    'fb_content': '[{"id":"1234"}]',
    'fb_content_type': 'product',
    'fb_content_id': '1234',
    '_valueToSum': totalAmount,
    'fb_currency': 'USD'
  },
  );
   ```
### 3. Add to Cart

- **When:** User adds a food item to the cart.
- **Implementation:**

  ```dart
  facebookAppEvents.logEvent(
  name: 'fb_mobile_add_to_cart',
  parameters: {
    'fb_content': '[{"id":"1234","quantity":1}]',
    'fb_content_type': 'product',
    'fb_content_id': '1234',
    '_valueToSum': totalAmount, // Стоимость добавленного товара
    'fb_currency': 'USD'
  },
  );
   ```
  ### 4. Initiate Checkout

- **When:** User begins the checkout process.
- **Implementation:**

  ```dart
  FacebookAppEvents facebookAppEvents = FacebookAppEvents();

  facebookAppEvents.logEvent(
  name: 'fb_mobile_initiated_checkout',
  parameters: {
    'fb_content': '[{"id":"1234","quantity":2},{"id":"5678","quantity":1}]',
    'fb_content_type': 'product',
    'fb_num_items': 3, // пример: всего 3 предмета в корзине
    'fb_payment_info_available': paymentInfoAvailable ? '1' : '0',
    'fb_currency': 'USD'
  },
  );
   ```
  ### 5. Purchase

- **When:** User completes an order.
- **Implementation:**

  ```dart
  FacebookAppEvents facebookAppEvents = FacebookAppEvents();
  
  facebookAppEvents.logEvent(
  name: 'fb_mobile_purchase',
  parameters: {
    'fb_content': '[{"id":"1234","quantity":2},{"id":"5678","quantity":1}]',
    'fb_content_type': 'product',
    '_valueToSum': totalAmount, // Сумма покупки
    'fb_currency': 'USD'
  }
  );
   ```

  ## Custom Events
  
    ### Contact me

- **When:** User reserves a table.
- **Implementation:**

  ```dart
  FacebookAppEvents facebookAppEvents = FacebookAppEvents();
  
  facebookAppEvents.logEvent(
  name: 'ContactMe',
  parameters: {
    'fb_content': '[{"id":"restaurant_123"}]',
    'fb_content_type': 'restaurant',
    'fb_contact_method': 'phone' // или 'email', 'chat' в зависимости от способа связи
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
   

  
