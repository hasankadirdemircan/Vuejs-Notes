<h1>Card Shopiing </h1>

### Screenshot
![vuejs02](https://user-images.githubusercontent.com/34090058/74372582-f9b0fa80-4deb-11ea-82a5-83b4ce32a77c.gif)


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
