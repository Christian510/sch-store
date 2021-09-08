# Custom Checkout Experience Created for a PromoShop Client

In this project I was tasked with building serveral checkout experiences in the Cart.

## Cost Center Checkout
### Problem
The client wanted a seperate checkout experience where the user can add their cost center number to the checkout.  This number indicates that the user can checkout without paying sales tax.  The standard checkout requires the user to pay sales tax.
### Solution
After some research I discovered I could skip the standard checkout, by creating a draft order.  This would require building a custom app that would handle all of the backend logic for this.  There is a problem with this.  I didn't have time to build out a custom backend solution.  In my research I found an app called mechanic.  This app is designed for developers like me.  They handle much of the backend repetetive logic.  They have many custom webhooks all set up.  This allows me to focus on the most of the front end logic.  This is not a tool for amateurs.  This still requires indepth understanding of the Shopify API, webhooks, CRUD operations, etc. 
Here are the code snippets from the mechanic app: 

This is the liquid logic for the webhook
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
Custom JS that handles passing the data to the webhook for creating the draft order and if successful display the success modal then redirect the user to the home page.
```
const mechanicCartSubmit = document.querySelector('#mechanic_cart_submit');
if (mechanicCartSubmit) {
  mechanicCartSubmit.addEventListener('click', (event) => {
  event.preventDefault();

  const ccn = document.querySelector('#cost-center-number').value;
  const cartNotes = document.querySelector('#CartSpecialInstructions');
    fetch({{ options.mechanic_webhook_url__required | json }}, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        cart: JSON.parse(event.target.dataset.cart),
        customerId: JSON.parse(event.target.dataset.customerId),
        customerIdSignature: JSON.parse(event.target.dataset.customerIdSignature),
        costCenterNum: JSON.parse(ccn),
        cartNotes: cartNotes
      }),
    }).then(data => {
      let id = event.target.dataset.customerId;
      if (id) {
        // show success message modal.
        emptyCart();
        cost_center_num.removeEventListener('input', toggleCheckoutBtns);
        ccOverlay.classList.replace('hidden', 'visible');
        ccModal.classList.replace('hidden', 'visible');
        } else {
          throw "No customer id!";         
        }
    }).catch((error) => {
       console.error(`Error sending cart data to Mechanic:, ${error}`);
    });
  });
}
```