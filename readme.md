# Custom Checkout Experience Created for a PromoShop Client

In this project I was tasked with building serveral checkout experiences in the Cart.

## Cost Center Checkout
### Problem
The client wanted a seperate checkout experience where the user can add their cost center number to the checkout.  This number indicates that the user can checkout without paying sales tax.  The standard checkout requires the user to pay sales tax.
### Solution
After some research I discovered I could skip the standard checkout, by creating a draft order.  This would require building a custom app that would handle all of the backend logic for this.  There is a problem with this.  I didn't have time to build out a custom backend solution.  In my research I found an app called mechanic.  This app is designed for developers like me.  They handle much of the backend repetetive logic.  They have many custom webhooks all set up.  This allows me to focus on the most of the front end logic and.  This is not a tool for amateurs.  This still requires indepth understanding of the Shopify API, webhooks, CRUD operations, etc. 
Here are the code snippets from the mechanic app: 

```
{% assign line_items = array %}
{% assign cost_center_num = event.data.costCenterNum %}
{% assign cart_notes = event.data.cartNotes%}

{% for item in event.data.cart.items %}
  {% assign line_item = hash %}
  {% assign line_item["variant_id"] = item.variant_id %}
  {% assign line_item["quantity"] = item.quantity %}
  {% assign line_items[line_items.size] = line_item %}
{% endfor %}

{% if event.data.customerId %}
  {% assign expected_signature = event.data.customerId | hmac_sha256: options.shared_secret__required %}
  {% if expected_signature == event.data.customerIdSignature %}
    {% assign customer_id = event.data.customerId %}
  {% endif %}
{% endif %}

{% action "shopify" %}
  [
    "create",
    "draft_order",
    {
      "customer": {
        "id": {{ customer_id | json }}
      },
      "line_items": {{ line_items | json }},
      "tags": {{ cost_center_num | json }},
      "note": {{ event.data.cart.note | json }}
    }
  ]
{% endaction %}
```