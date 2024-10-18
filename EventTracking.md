---

### **4. EventTracking.md**

```markdown
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
