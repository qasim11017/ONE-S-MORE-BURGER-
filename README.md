<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ONE'S MORE BURGER - Order Online</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <style>
    body { background-color: #fff8f0; }
    .hero { background: url('https://images.unsplash.com/photo-1550547660-d9450f859349?auto=format&fit=crop&w=1350&q=80') center/cover; color: white; padding: 80px 20px; text-align: center; }
    .menu-item { border: 1px solid #ddd; border-radius: 10px; padding: 15px; background: #fff; margin-bottom: 20px; }
    .menu-item img { width: 100%; height: 200px; object-fit: cover; border-radius: 10px; }
  </style>
</head>
<body>
  <header class="hero">
    <h1>ONE'S MORE BURGER 🍔</h1>
    <p>Flame-Grilled Perfection at Your Doorstep</p>
    <a href="#menu" class="btn btn-warning">Order Now</a>
  </header>

  <div class="container mt-5" id="menu">
    <h2 class="text-center mb-4">Our Menu</h2>
    <div class="row">
      <!-- Sample items from all categories -->
      <div class="col-md-4">
        <div class="menu-item">
          <img src="https://source.unsplash.com/featured/?chicken,tikka" alt="Chicken Tikka">
          <h4>Chicken Tikka</h4>
          <p>Rs 350</p>
          <button class="btn btn-success add-to-cart" data-name="Chicken Tikka" data-price="350">Add to Cart</button>
        </div>
      </div>
      <div class="col-md-4">
        <div class="menu-item">
          <img src="https://source.unsplash.com/featured/?burger,zinger" alt="Zinger Burger">
          <h4>Zinger Burger</h4>
          <p>Rs 250</p>
          <button class="btn btn-success add-to-cart" data-name="Zinger Burger" data-price="250">Add to Cart</button>
        </div>
      </div>
      <div class="col-md-4">
        <div class="menu-item">
          <img src="https://source.unsplash.com/featured/?fries" alt="Fries">
          <h4>Fries</h4>
          <p>Rs 100</p>
          <button class="btn btn-success add-to-cart" data-name="Fries" data-price="100">Add to Cart</button>
        </div>
      </div>
      <div class="col-md-4">
        <div class="menu-item">
          <img src="https://source.unsplash.com/featured/?bbq,roll" alt="OMB Special Roll">
          <h4>OMB Special Roll</h4>
          <p>Rs 200</p>
          <button class="btn btn-success add-to-cart" data-name="OMB Special Roll" data-price="200">Add to Cart</button>
        </div>
      </div>
      <div class="col-md-4">
        <div class="menu-item">
          <img src="https://source.unsplash.com/featured/?broast,chicken" alt="Jumbo Broast">
          <h4>Jumbo Broast (3 pcs)</h4>
          <p>Rs 580</p>
          <button class="btn btn-success add-to-cart" data-name="Jumbo Broast (3 pcs)" data-price="580">Add to Cart</button>
        </div>
      </div>
    </div>
  </div>

  <div class="container mt-5">
    <h3>Cart</h3>
    <ul id="cart-list" class="list-group mb-3"></ul>
    <p><strong>Total: Rs <span id="cart-total">0</span></strong></p>
    <label for="delivery-option">Choose:</label>
    <select id="delivery-option" class="form-select mb-3">
      <option value="Delivery">Delivery</option>
      <option value="Pickup">Pickup</option>
    </select>
    <a id="checkout-btn" class="btn btn-primary" href="#" target="_blank">Checkout via WhatsApp</a>
  </div>

  <script>
    const cart = [];
    document.querySelectorAll('.add-to-cart').forEach(button => {
      button.addEventListener('click', () => {
        const name = button.getAttribute('data-name');
        const price = parseInt(button.getAttribute('data-price'));
        cart.push({ name, price });
        updateCart();
      });
    });

    function updateCart() {
      const list = document.getElementById('cart-list');
      const total = document.getElementById('cart-total');
      list.innerHTML = '';
      let totalPrice = 0;
      cart.forEach(item => {
        const li = document.createElement('li');
        li.className = 'list-group-item';
        li.textContent = `${item.name} - Rs ${item.price}`;
        list.appendChild(li);
        totalPrice += item.price;
      });
      total.textContent = totalPrice;
      const deliveryOption = document.getElementById('delivery-option').value;
      const orderText = cart.map(item => `${item.name} (Rs ${item.price})`).join(', ');
      const message = `Hi, I want to order: ${orderText}. Total: Rs ${totalPrice}. Option: ${deliveryOption}`;
      const whatsappURL = `https://wa.me/923113070607?text=${encodeURIComponent(message)}`;
      document.getElementById('checkout-btn').href = whatsappURL;
    }
  </script>
</body>
</html>
