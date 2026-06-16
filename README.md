```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>THREAD & CO. | Modern Apparel</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/lucide-icons/0.321.0/umd/lucide.min.js"></script>
    <style>
        :root {
            --bg-color: #ffffff;
            --text-color: #111111;
            --accent-color: #2563eb;
            --gray-light: #f3f4f6;
            --gray-md: #e5e7eb;
            --gray-text: #6b7280;
        }

        [data-theme="dark"] {
            --bg-color: #111827;
            --text-color: #f9fafb;
            --accent-color: #3b82f6;
            --gray-light: #1f2937;
            --gray-md: #374151;
            --gray-text: #9ca3af;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            transition: background-color 0.3s, border-color 0.3s;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            overflow-x: hidden;
        }

        /* Navbar */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 5%;
            border-bottom: 1px solid var(--gray-md);
            position: sticky;
            top: 0;
            background-color: var(--bg-color);
            z-index: 100;
        }

        .logo {
            font-weight: 800;
            font-size: 1.5rem;
            letter-spacing: 1px;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;
        }

        .nav-actions {
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .icon-btn {
            background: none;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            position: relative;
        }

        .cart-badge {
            position: absolute;
            top: -8px;
            right: -8px;
            background-color: var(--accent-color);
            color: white;
            font-size: 0.75rem;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.1), rgba(0,0,0,0.3)), url('https://images.unsplash.com/photo-1441986300917-64674bd600d8?auto=format&fit=crop&w=1600&q=80');
            background-size: cover;
            background-position: center;
            height: 60vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: flex-start;
            padding: 0 10%;
            color: white;
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            font-weight: 800;
        }

        .hero p {
            font-size: 1.25rem;
            margin-bottom: 2rem;
            max-width: 500px;
        }

        .shop-btn {
            background-color: white;
            color: black;
            border: none;
            padding: 0.8rem 2rem;
            font-weight: 600;
            cursor: pointer;
            text-decoration: none;
            border-radius: 4px;
            transition: transform 0.2s;
        }

        .shop-btn:hover {
            transform: scale(1.05);
        }

        /* Product Section */
        .main-container {
            padding: 4rem 5%;
        }

        .section-title {
            font-size: 2rem;
            margin-bottom: 2rem;
            text-align: center;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background-color: var(--gray-light);
            border-radius: 8px;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            position: relative;
        }

        .product-img {
            width: 100%;
            height: 350px;
            object-fit: cover;
        }

        .product-info {
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .product-name {
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }

        .product-price {
            font-weight: 700;
            color: var(--accent-color);
            margin-bottom: 1rem;
            margin-top: auto;
        }

        .add-to-cart {
            background-color: var(--text-color);
            color: var(--bg-color);
            border: none;
            padding: 0.75rem;
            border-radius: 4px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 0.5rem;
        }

        .add-to-cart:hover {
            opacity: 0.9;
        }

        /* Cart Slide-out Drawer */
        .cart-drawer {
            position: fixed;
            top: 0;
            right: -400px;
            width: 400px;
            height: 100%;
            background-color: var(--bg-color);
            box-shadow: -5px 0 15px rgba(0,0,0,0.1);
            z-index: 200;
            transition: right 0.3s ease;
            display: flex;
            flex-direction: column;
            border-left: 1px solid var(--gray-md);
        }

        .cart-drawer.open {
            right: 0;
        }

        .cart-header {
            padding: 1.5rem;
            border-bottom: 1px solid var(--gray-md);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .cart-items {
            flex-grow: 1;
            overflow-y: auto;
            padding: 1.5rem;
        }

        .cart-item {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
            align-items: center;
        }

        .cart-item-img {
            width: 70px;
            height: 90px;
            object-fit: cover;
            border-radius: 4px;
        }

        .cart-item-details {
            flex-grow: 1;
        }

        .cart-item-title {
            font-weight: 600;
            font-size: 0.95rem;
        }

        .cart-item-price {
            color: var(--gray-text);
            margin-top: 0.25rem;
        }

        .remove-item {
            background: none;
            border: none;
            color: #ef4444;
            cursor: pointer;
        }

        .cart-footer {
            padding: 1.5rem;
            border-top: 1px solid var(--gray-md);
        }

        .cart-total {
            display: flex;
            justify-content: space-between;
            font-size: 1.2rem;
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .checkout-btn {
            width: 100%;
            background-color: var(--accent-color);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 4px;
            font-weight: 600;
            cursor: pointer;
        }

        .cart-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: rgba(0,0,0,0.4);
            z-index: 150;
            display: none;
        }

        .cart-overlay.open {
            display: block;
        }

        /* Footer */
        footer {
            background-color: var(--gray-light);
            padding: 3rem 5%;
            text-align: center;
            color: var(--gray-text);
            border-top: 1px solid var(--gray-md);
        }

        @media (max-width: 600px) {
            .cart-drawer {
                width: 100%;
                right: -100%;
            }
            .hero h1 {
                font-size: 2.5rem;
            }
            .nav-links {
                display: none;
            }
        }
    </style>
</head>
<body>

    <nav>
        <div class="logo">THREAD & CO.</div>
        <ul class="nav-links">
            <li><a href="#shop">Shop All</a></li>
            <li><a href="#shop">New Arrivals</a></li>
            <li><a href="#shop">Essentials</a></li>
        </ul>
        <div class="nav-actions">
            <button class="icon-btn" id="theme-toggle" aria-label="Toggle Theme">
                <i data-lucide="moon"></i>
            </button>
            <button class="icon-btn" id="cart-icon" aria-label="Open Cart">
                <i data-lucide="shopping-bag"></i>
                <span class="cart-badge" id="cart-count">0</span>
            </button>
        </div>
    </nav>

    <header class="hero">
        <h1>Effortless Style</h1>
        <p>Explore curated essentials designed for comfort, utility, and modern everyday wear.</p>
        <a href="#shop" class="shop-btn">Shop Collection</a>
    </header>

    <main class="main-container" id="shop">
        <h2 class="section-title">Featured Pieces</h2>
        <div class="product-grid" id="product-list"></div>
    </main>

    <div class="cart-overlay" id="cart-overlay"></div>
    <div class="cart-drawer" id="cart-drawer">
        <div class="cart-header">
            <h3>Your Bag</h3>
            <button class="icon-btn" id="close-cart"><i data-lucide="x"></i></button>
        </div>
        <div class="cart-items" id="cart-items-container">
            </div>
        <div class="cart-footer">
            <div class="cart-total">
                <span>Total:</span>
                <span id="cart-total-price">$0.00</span>
            </div>
            <button class="checkout-btn" onclick="alert('Checkout process initiated!')">Proceed to Checkout</button>
        </div>
    </div>

    <footer>
        <p>&copy; 2026 THREAD & CO. Built beautifully.</p>
    </footer>

    <script>
        // Initialize Lucide Icons
        lucide.createIcons();

        // Sample Clothing Data
        const products = [
            { id: 1, name: "Classic Heavyweight Tee", price: 35.00, image: "https://images.unsplash.com/photo-1521572267360-ee0c2909d518?auto=format&fit=crop&w=500&q=80" },
            { id: 2, name: "Oversized Linen Shirt", price: 58.00, image: "https://images.unsplash.com/photo-1596755094514-f87e34085b2c?auto=format&fit=crop&w=500&q=80" },
            { id: 3, name: "Everyday Canvas Jacket", price: 110.00, image: "https://images.unsplash.com/photo-1551028719-00167b16eac5?auto=format&fit=crop&w=500&q=80" },
            { id: 4, name: "Relaxed Fit Chinos", price: 65.00, image: "https://images.unsplash.com/photo-1624378439575-d8705ad7ae80?auto=format&fit=crop&w=500&q=80" },
            { id: 5, name: "Knit Cotton Sweater", price: 85.00, image: "https://images.unsplash.com/photo-1614975058789-41316d0e2e9c?auto=format&fit=crop&w=500&q=80" },
            { id: 6, name: "Minimalist Weekender Cap", price: 28.00, image: "https://images.unsplash.com/photo-1534215754734-18e55d13ce35?auto=format&fit=crop&w=500&q=80" }
        ];

        let cart = [];

        // Elements
        const productGrid = document.getElementById('product-list');
        const cartDrawer = document.getElementById('cart-drawer');
        const cartOverlay = document.getElementById('cart-overlay');
        const cartIcon = document.getElementById('cart-icon');
        const closeCart = document.getElementById('close-cart');
        const cartItemsContainer = document.getElementById('cart-items-container');
        const cartCount = document.getElementById('cart-count');
        const cartTotalPrice = document.getElementById('cart-total-price');
        const themeToggle = document.getElementById('theme-toggle');

        // Render Products
        function renderProducts() {
            productGrid.innerHTML = products.map(product => `
                <div class="product-card">
                    <img src="${product.image}" alt="${product.name}" class="product-img">
                    <div class="product-info">
                        <div class="product-name">${product.name}</div>
                        <div class="product-price">$${product.price.toFixed(2)}</div>
                        <button class="add-to-cart" onclick="addToCart(${product.id})">
                            <i data-lucide="plus" size="16"></i> Add to Bag
                        </button>
                    </div>
                </div>
            `).join('');
            lucide.createIcons();
        }

        // Cart Actions
        function toggleCart() {
            cartDrawer.classList.toggle('open');
            cartOverlay.classList.toggle('open');
        }

        function addToCart(id) {
            const product = products.find(p => p.id === id);
            const existingItem = cart.find(item => item.id === id);

            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({ ...product, quantity: 1 });
            }
            updateCart();
            // Automatically open cart when adding item
            cartDrawer.classList.add('open');
            cartOverlay.classList.add('open');
        }

        function removeFromCart(id) {
            cart = cart.filter(item => item.id !== id);
            updateCart();
        }

        function updateCart() {
            // Count total items
            const totalItems = cart.reduce((acc, item) => acc + item.quantity, 0);
            cartCount.textContent = totalItems;

            // Calculate Price
            const totalSum = cart.reduce((acc, item) => acc + (item.price * item.quantity), 0);
            cartTotalPrice.textContent = `$${totalSum.toFixed(2)}`;

            // Render Cart List
            if (cart.length === 0) {
                cartItemsContainer.innerHTML = `<p style="color: var(--gray-text); text-align: center; margin-top: 2rem;">Your bag is empty.</p>`;
            } else {
                cartItemsContainer.innerHTML = cart.map(item => `
                    <div class="cart-item">
                        <img src="${item.image}" alt="${item.name}" class="cart-item-img">
                        <div class="cart-item-details">
                            <div class="cart-item-title">${item.name}</div>
                            <div class="cart-item-price">${item.quantity} &times; $${item.price.toFixed(2)}</div>
                        </div>
                        <button class="remove-item" onclick="removeFromCart(${item.id})">
                            <i data-lucide="trash-2" size="18"></i>
                        </button>
                    </div>
                `).join('');
            }
            lucide.createIcons();
        }

        // Theme Toggle
        themeToggle.addEventListener('click', () => {
            const currentTheme = document.documentElement.getAttribute('data-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            document.documentElement.setAttribute('data-theme', newTheme);
            
            // Update icon dynamically
            const icon = themeToggle.querySelector('i');
            if (newTheme === 'dark') {
                icon.setAttribute('data-lucide', 'sun');
            } else {
                icon.setAttribute('data-lucide', 'moon');
            }
            lucide.createIcons();
        });

        // Event Listeners
        cartIcon.addEventListener('click', toggleCart);
        closeCart.addEventListener('click', toggleCart);
        cartOverlay.addEventListener('click', toggleCart);

        // Initial Load
        renderProducts();
        updateCart();
    </script>
</body>
</html>

```
