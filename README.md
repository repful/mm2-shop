# mm2-shop
A mm2 shop
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MM2 Shop</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      background: #09090d;
      color: white;
    }

    header {
      padding: 22px 7%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #222;
      background: #0d0d13;
    }

    .logo {
      font-size: 24px;
      font-weight: bold;
    }

    nav a {
      color: #aaa;
      text-decoration: none;
      margin-left: 25px;
    }

    nav a:hover {
      color: white;
    }

    .hero {
      text-align: center;
      padding: 80px 20px;
    }

    .hero h1 {
      font-size: 48px;
      margin-bottom: 15px;
    }

    .hero p {
      color: #aaa;
      font-size: 18px;
      margin-bottom: 30px;
    }

    .discord-btn {
      display: inline-block;
      background: #5865f2;
      color: white;
      padding: 13px 24px;
      border-radius: 8px;
      text-decoration: none;
      font-weight: bold;
    }

    .shop {
      width: 86%;
      max-width: 1200px;
      margin: auto;
      padding-bottom: 80px;
    }

    .controls {
      display: flex;
      gap: 12px;
      margin-bottom: 30px;
      flex-wrap: wrap;
    }

    input, select {
      background: #14141b;
      color: white;
      border: 1px solid #292933;
      padding: 13px;
      border-radius: 8px;
      outline: none;
    }

    input {
      flex: 1;
      min-width: 220px;
    }

    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
    }

    .card {
      background: #111118;
      border: 1px solid #24242e;
      border-radius: 12px;
      padding: 18px;
      transition: 0.2s;
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: #555;
    }

    .item-image {
      height: 150px;
      background: #181820;
      border-radius: 9px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #666;
      margin-bottom: 15px;
    }

    .card h3 {
      margin-bottom: 8px;
    }

    .category {
      color: #888;
      font-size: 14px;
      margin-bottom: 12px;
    }

    .price {
      font-size: 20px;
      font-weight: bold;
      margin-bottom: 8px;
    }

    .stock {
      color: #62d98b;
      font-size: 14px;
    }

    footer {
      text-align: center;
      padding: 30px;
      border-top: 1px solid #222;
      color: #666;
    }
  </style>
</head>

<body>

<header>
  <div class="logo">MM2 SHOP</div>

  <nav>
    <a href="#home">Home</a>
    <a href="#shop">Shop</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<section class="hero" id="home">
  <h1>Your MM2 Shop</h1>
  <p>Browse our inventory and check what's available.</p>

  <a class="discord-btn" href="https://discord.com/" target="_blank">
    Join Discord
  </a>
</section>

<section class="shop" id="shop">

  <div class="controls">
    <input
      type="text"
      id="search"
      placeholder="Search items..."
      onkeyup="filterItems()"
    >

    <select id="category" onchange="filterItems()">
      <option value="all">All Items</option>
      <option value="godly">Godlies</option>
      <option value="ancient">Ancients</option>
      <option value="set">Sets</option>
      <option value="other">Other</option>
    </select>
  </div>

  <div class="products">

    <div class="card" data-name="Example Godly" data-category="godly">
      <div class="item-image">
        IMAGE
      </div>

      <h3>Example Godly</h3>
      <div class="category">Godly</div>
      <div class="price">$10.00</div>
      <div class="stock">● In Stock</div>
    </div>

    <div class="card" data-name="Example Ancient" data-category="ancient">
      <div class="item-image">
        IMAGE
      </div>

      <h3>Example Ancient</h3>
      <div class="category">Ancient</div>
      <div class="price">$15.00</div>
      <div class="stock">● In Stock</div>
    </div>

    <div class="card" data-name="Example Set" data-category="set">
      <div class="item-image">
        IMAGE
      </div>

      <h3>Example Set</h3>
      <div class="category">Set</div>
      <div class="price">$20.00</div>
      <div class="stock">● In Stock</div>
    </div>

    <div class="card" data-name="Example Item" data-category="other">
      <div class="item-image">
        IMAGE
      </div>

      <h3>Example Item</h3>
      <div class="category">Other</div>
      <div class="price">$5.00</div>
      <div class="stock">● In Stock</div>
    </div>

  </div>
</section>

<footer id="contact">
  <p>© 2026 Your MM2 Shop</p>
</footer>

<script>
  function filterItems() {
    const search = document
      .getElementById("search")
      .value
      .toLowerCase();

    const category = document
      .getElementById("category")
      .value;

    const cards = document.querySelectorAll(".card");

    cards.forEach(card => {
      const name = card.dataset.name.toLowerCase();
      const cardCategory = card.dataset.category;

      const matchesSearch = name.includes(search);
      const matchesCategory =
        category === "all" || cardCategory === category;

      card.style.display =
        matchesSearch && matchesCategory
          ? "block"
          : "none";
    });
  }
</script>

</body>
</html>