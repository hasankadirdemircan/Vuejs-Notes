<h1>Card Shopiing </h1>

### Screenshot

<p align="center">
  <a href="https://user-images.githubusercontent.com/34090058/74091381-e8a07a80-4ac7-11ea-9830-ba5c8098ef7a.png">
    <img alt="Techs" title="Techs" src="https://user-images.githubusercontent.com/34090058/74091381-e8a07a80-4ac7-11ea-9830-ba5c8098ef7a.png"width="400">
  </a>
</p>
Save for latter
<p align="center">
  <a href="https://user-images.githubusercontent.com/34090058/74091393-fc4be100-4ac7-11ea-83cb-01e90a293323.png">
    <img alt="Techs" title="Techs" src="https://user-images.githubusercontent.com/34090058/74091393-fc4be100-4ac7-11ea-83cb-01e90a293323.png"width="400">
  </a>
</p>
# Code Example
index.html
 ```js
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>VueJS Demo</title>
  <link rel="stylesheet" type="text/css" href="app.css" />
  <script src="https://cdnjs.cloudflare.com/ajax/libs/vue/2.0.3/vue.js"></script>
  <script type="text/javascript" src="app.js"></script>
</head>
<body>
  <div id="app">
    <p v-if="isLoading">Loading</p>
    <h2>Shopping Cart</h2>
    <p v-if="!cart.length">No item in cart.</p>
    <div class="cart">
      <div class="item" v-for="(item, index) in cart">
        <div class="image">
          <a v-bind:href="item.url">
            <img v-bind:src="item.image" />
          </a>
        </div>
        <div class="info">
          <h4>{{item.name}}</h4>
          <p class="seller">by {{item.seller}}</p>
          <p class="status available" v-if="item.isAvailable">In Stock</p>
          <p class="shipping" v-if="item.isEligible">Eligible for FREE Shipping & FREE Returns</p>
          <a href="#" v-on:click="removeFromCart(index)">Delete</a>
          <a href="#" class="secondary" v-on:click="saveForLater(index)">Save for later</a>
        </div>
      </div>
    </div>

    <h2 class="saved-header">Saved for later ({{saved.length}} item)</h2>
    <div class="cart">
      <div class="item" v-for="(item, index) in saved">
        <div class="image">
          <a v-bind:href="item.url">
            <img v-bind:src="item.image" />
          </a>
        </div>
        <div class="info">
          <h4>{{item.name}}</h4>
          <p class="seller">by {{item.seller}}</p>
          <p class="status available" v-if="item.isAvailable">In Stock</p>
          <p class="shipping" v-if="item.isEligible">Eligible for FREE Shipping & FREE Returns</p>
          <a href="#" v-on:click="removeFromSavedList(index)">Delete</a>
          <a href="#" class="secondary" v-on:click="moveToCart(index)">Move to cart</a>
        </div>
      </div>
    </div>
  </div>
</body>
</html>
 ```
 app.js
  ```js
window.addEventListener('load', () => {

    window.vue = new Vue({
      el: '#app',
      name: 'Cart',
      data: {
        isLoading: true,
        cart: [],
        saved: []
      },
      methods: {
        removeFromCart(index) {
          this.cart.splice(index, 1);
        },
        saveForLater(index) {
          const item = this.cart.splice(index, 1);
          this.saved.push(item[0]);
        },
        removeFromSavedList(index) {
          this.saved.splice(index);
        },
        moveToCart(index) {
          const item = this.saved.splice(index, 1);
          this.cart.push(item[0]);
        }
      },
      created() {
        fetch('./data.json')
          .then((res) => { return res.json() })
          .then((res) => {
            this.isLoading = false;
            this.cart = res.cart;
            this.saved = res.saved;
          })
      }
    })
  
  });
   ```
   
   ## How to Run to Server
 ```
 python -m SimpleHTTPServer 8000
 ```