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
