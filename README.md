# E-commerce-Website
A simple and responsive e-commerce web app showcasing core features like product listing, cart, and checkout. Built with HTML, CSS, and JS.  With user Authentication Functions (Create Account)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WebCraft | E-Commerce Store</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* External CSS */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #4a6de5;
            --secondary: #f8f9fa;
            --accent: #ff6b6b;
            --dark: #343a40;
            --light: #f8f9fa;
            --success: #28a745;
            --border: #dee2e6;
            --text: #212529;
        }

        body {
            background-color: #f5f7ff;
            color: var(--text);
            line-height: 1.6;
        }

        /* Header Styles */
        header {
            background: linear-gradient(135deg, var(--primary), #2a4ac0);
            color: white;
            padding: 1rem 2rem;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            display: flex;
            align-items: center;
        }

        .logo i {
            margin-right: 10px;
            color: var(--accent);
        }

        nav ul {
            display: flex;
            list-style: none;
        }

        nav ul li {
            margin-left: 1.5rem;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            padding: 0.5rem;
            border-radius: 4px;
        }

        nav ul li a:hover {
            color: var(--accent);
            background: rgba(255, 255, 255, 0.1);
        }

        .cart-icon {
            position: relative;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -10px;
            right: -10px;
            background-color: var(--accent);
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }

        /* Main Content */
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .hero {
            background: linear-gradient(rgba(74, 109, 229, 0.9), rgba(74, 109, 229, 0.8)), url('https://images.unsplash.com/photo-1607082350899-7e105aa886ae?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2072&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            padding: 4rem 2rem;
            text-align: center;
            border-radius: 12px;
            margin-bottom: 2rem;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 2rem;
        }

        .btn {
            display: inline-block;
            background: var(--accent);
            color: white;
            padding: 0.8rem 1.5rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .btn:hover {
            background: #ff5252;
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        /* Products Section */
        .section-title {
            text-align: center;
            margin-bottom: 2rem;
            color: var(--dark);
            position: relative;
            padding-bottom: 0.5rem;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: var(--accent);
            border-radius: 2px;
        }

        .products {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .product {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .product:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }

        .product-img {
            height: 200px;
            width: 100%;
            object-fit: cover;
            border-bottom: 1px solid var(--border);
        }

        .product-content {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: var(--dark);
        }

        .product-price {
            font-size: 1.3rem;
            color: var(--primary);
            font-weight: 700;
            margin-bottom: 1rem;
        }

        .product-description {
            color: #6c757d;
            margin-bottom: 1.5rem;
        }

        .product-actions {
            display: flex;
            justify-content: space-between;
        }

        /* Table Styles */
        .order-summary {
            background: white;
            border-radius: 12px;
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .order-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }

        .order-table th, .order-table td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid var(--border);
        }

        .order-table th {
            background-color: #f8f9fa;
            font-weight: 600;
        }

        .order-table tr:last-child td {
            border-bottom: none;
        }

        /* Form Styles */
        .form-container {
            background: white;
            border-radius: 12px;
            padding: 2rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            background: linear-gradient(to bottom right, #f8f9fa, #e9ecef);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 0.8rem 1rem;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s, box-shadow 0.3s;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(74, 109, 229, 0.2);
        }

        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            padding: 3rem 2rem;
            margin-top: 3rem;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .footer-section h3 {
            font-size: 1.3rem;
            margin-bottom: 1.5rem;
            position: relative;
            padding-bottom: 0.5rem;
        }

        .footer-section h3::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 50px;
            height: 3px;
            background: var(--accent);
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 0.8rem;
        }

        .footer-links a {
            color: #ced4da;
            text-decoration: none;
            transition: color 0.3s;
        }

        .footer-links a:hover {
            color: white;
        }

        .social-icons {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-icons a {
            color: white;
            font-size: 1.5rem;
            transition: color 0.3s;
        }

        .social-icons a:hover {
            color: var(--accent);
        }

        .copyright {
            text-align: center;
            margin-top: 3rem;
            padding-top: 1.5rem;
            border-top: 1px solid #495057;
            color: #adb5bd;
        }

        /* Digital Clock */
        .clock-container {
            background: var(--dark);
            color: white;
            padding: 1rem;
            border-radius: 8px;
            text-align: center;
            margin: 1rem 0;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        #digital-clock {
            font-size: 2rem;
            font-weight: 700;
            letter-spacing: 2px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                text-align: center;
            }

            nav ul {
                margin-top: 1rem;
                flex-wrap: wrap;
                justify-content: center;
            }

            nav ul li {
                margin: 0.5rem;
            }

            .hero h1 {
                font-size: 2.2rem;
            }

            .hero p {
                font-size: 1rem;
            }
        }

        /* Internal CSS for specific elements */
        .featured-products {
            border: 2px solid var(--primary);
            border-radius: 12px;
            padding: 2rem;
            margin: 2rem 0;
            background: linear-gradient(to bottom, #ffffff, #f0f4ff);
            box-shadow: 0 8px 20px rgba(74, 109, 229, 0.15);
        }

        .special-offer {
            text-align: center;
            padding: 2rem;
            margin: 2rem 0;
            background: linear-gradient(135deg, #ff6b6b, #ff8e8e);
            color: white;
            border-radius: 12px;
            box-shadow: 0 6px 15px rgba(255, 107, 107, 0.3);
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="header-container">
            <div class="logo">
                <i class="fas fa-laptop-code"></i>
                <span>WebCraft</span>
            </div>
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Products</a></li>
                    <li><a href="#">About</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
            <div class="cart-icon">
                <i class="fas fa-shopping-cart"></i>
                <span class="cart-count">3</span>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <div class="container">
        <!-- Hero Section -->
        <section class="hero">
            <h1>Web Development Essentials</h1>
            <p>Discover the best tools, resources, and gadgets for web developers and designers. Everything you need to craft amazing web experiences.</p>
            <a href="#products" class="btn">Shop Now</a>
        </section>

        <!-- Digital Clock -->
        <div class="clock-container">
            <div id="digital-clock">00:00:00</div>
        </div>

        <!-- Products Section -->
        <section id="products">
            <h2 class="section-title">Featured Products</h2>
            <div class="products">
                <div class="product">
                    <img src="https://images.unsplash.com/photo-1593642632823-8f785ba67e45?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="Web Development Book" class="product-img">
                    <div class="product-content">
                        <h3 class="product-title">Advanced Web Development</h3>
                        <div class="product-price">$49.99</div>
                        <p class="product-description">Master modern web development techniques with this comprehensive guide.</p>
                        <div class="product-actions">
                            <button class="btn">Add to Cart</button>
                            <button class="btn" style="background: var(--dark);">Details</button>
                        </div>
                    </div>
                </div>

                <div class="product">
                    <img src="https://images.unsplash.com/photo-1611186871348-b1ce696e52c9?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="MacBook Pro" class="product-img">
                    <div class="product-content">
                        <h3 class="product-title">MacBook Pro 16"</h3>
                        <div class="product-price">$2399.99</div>
                        <p class="product-description">Powerful laptop for developers and designers with M2 Pro chip.</p>
                        <div class="product-actions">
                            <button class="btn">Add to Cart</button>
                            <button class="btn" style="background: var(--dark);">Details</button>
                        </div>
                    </div>
                </div>

                <div class="product">
                    <img src="https://images.unsplash.com/photo-1550745165-9bc0b252726f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80" alt="Gaming Headphones" class="product-img">
                    <div class="product-content">
                        <h3 class="product-title">Professional Headphones</h3>
                        <div class="product-price">$199.99</div>
                        <p class="product-description">High-quality sound for immersive coding sessions and entertainment.</p>
                        <div class="product-actions">
                            <button class="btn">Add to Cart</button>
                            <button class="btn" style="background: var(--dark);">Details</button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Order Summary Table -->
        <section class="order-summary">
            <h2 class="section-title">Order Summary</h2>
            <table class="order-table">
                <thead>
                    <tr>
                        <th>Product</th>
                        <th>Price</th>
                        <th>Quantity</th>
                        <th>Total</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Advanced Web Development Book</td>
                        <td>$49.99</td>
                        <td>1</td>
                        <td>$49.99</td>
                    </tr>
                    <tr>
                        <td>MacBook Pro 16"</td>
                        <td>$2399.99</td>
                        <td>1</td>
                        <td>$2399.99</td>
                    </tr>
                    <tr>
                        <td>Professional Headphones</td>
                        <td>$199.99</td>
                        <td>2</td>
                        <td>$399.98</td>
                    </tr>
                </tbody>
                <tfoot>
                    <tr>
                        <th colspan="3">Total</th>
                        <th>$2849.96</th>
                    </tr>
                </tfoot>
            </table>
        </section>

        <!-- Registration Form -->
        <section class="form-container">
            <h2 class="section-title">Create Account</h2>
            <form id="registration-form">
                <div class="form-group">
                    <label for="name">Full Name</label>
                    <input type="text" id="name" class="form-control" placeholder="Enter your full name" required>
                </div>
                <div class="form-group">
                    <label for="email">Email Address</label>
                    <input type="email" id="email" class="form-control" placeholder="Enter your email" required>
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" class="form-control" placeholder="Create a password" required>
                </div>
                <div class="form-group">
                    <label for="birthdate">Birthdate</label>
                    <input type="date" id="birthdate" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="experience">Web Development Experience (years)</label>
                    <input type="range" id="experience" min="0" max="20" value="2" class="form-control">
                    <output for="experience" id="experience-output">2 years</output>
                </div>
                <button type="submit" class="btn" style="width: 100%;">Register Now</button>
            </form>
        </section>

        <!-- Special Offer -->
        <div class="special-offer">
            <h2>Limited Time Offer!</h2>
            <p>Get 20% off on all products when you sign up today. Use promo code: WEBCRAFT20</p>
            <a href="#" class="btn" style="background: white; color: #ff6b6b;">Claim Offer Now</a>
        </div>

        <!-- Multimedia Section -->
        <section>
            <h2 class="section-title">Web Development Resources</h2>
            <div style="display: flex; gap: 2rem; flex-wrap: wrap;">
                <div style="flex: 1; min-width: 300px;">
                    <h3>HTML5 Tutorial Audio</h3>
                    <audio controls style="width: 100%; margin-top: 1rem;">
                        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
                        Your browser does not support the audio element.
                    </audio>
                </div>
                <div style="flex: 1; min-width: 300px;">
                    <h3>CSS3 Tutorial Video</h3>
                    <video controls style="width: 100%; height: auto; margin-top: 1rem;">
                        <source src="https://www.w3schools.com/html/mov_bbb.mp4" type="video/mp4">
                        Your browser does not support the video element.
                    </video>
                </div>
            </div>
        </section>
    </div>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-section">
                <h3>About WebCraft</h3>   
                <p>We provide the best tools and resources for web developers and designers to create amazing digital experiences.</p>
                <div class="social-icons">
                    <a href="#"><i class="fab fa-facebook"></i></a>
                    <a href="#"><i class="fab fa-twitter"></i></a>
                    <a href="#"><i class="fab fa-instagram"></i></a>
                    <a href="#"><i class="fab fa-linkedin"></i></a>
                </div>
            </div>
            <div class="footer-section">
                <h3>Quick Links</h3>
                <ul class="footer-links">
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Products</a></li>
                    <li><a href="#">About Us</a></li>
                    <li><a href="#">Contact</a></li>
                    <li><a href="#">Privacy Policy</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Contact Info</h3>
                <p><i class="fas fa-map-marker-alt"></i> 123 Web Street, Dev City</p>
                <p><i class="fas fa-phone"></i> +1 (555) 123-4567</p>
                <p><i class="fas fa-envelope"></i> info@webcraft.com</p>
            </div>
        </div>
        <div class="copyright">
            <p>&copy; 2025 WebCraft. All rights reserved.</p>
        </div>
    </footer>

    <!-- JavaScript -->
    <script>
        // Digital Clock
        function updateClock() {
            const now = new Date();
            const hours = now.getHours().toString().padStart(2, '0');
            const minutes = now.getMinutes().toString().padStart(2, '0');
            const seconds = now.getSeconds().toString().padStart(2, '0');
            
            document.getElementById('digital-clock').textContent = `${hours}:${minutes}:${seconds}`;
        }
        
        setInterval(updateClock, 1000);
        updateClock();
        
        // Experience Range Output
        const experienceSlider = document.getElementById('experience');
        const experienceOutput = document.getElementById('experience-output');
        
        experienceSlider.addEventListener('input', function() {
            experienceOutput.textContent = `${this.value} years`;
        });
        
        // Form Validation
        document.getElementById('registration-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;
            
            try {
                // Simple validation
                if (name.length < 3) {
                    throw new Error('Name must be at least 3 characters long');
                }
                
                if (!email.includes('@')) {
                    throw new Error('Please enter a valid email address');
                }
                
                if (password.length < 6) {
                    throw new Error('Password must be at least 6 characters long');
                }
                
                alert('Registration successful!');
                this.reset();
                
            } catch (error) {
                alert(error.message);
            }
        });
        
        // Change H1 Color
        const heroTitle = document.querySelector('.hero h1');
        let colorIndex = 0;
        const colors = ['#fff', '#f8f9fa', '#e9ecef', '#dee2e6'];
        
        setInterval(() => {
            heroTitle.style.color = colors[colorIndex % colors.length];
            colorIndex++;
        }, 1000);
        
        // Math Operations Example
        const calculateTotal = () => {
            const productPrices = [49.99, 2399.99, 199.99];
            const quantities = [1, 1, 2];
            
            let subtotal = 0;
            for (let i = 0; i < productPrices.length; i++) {
                subtotal += productPrices[i] * quantities[i];
            }
            
            const tax = subtotal * 0.08;
            const total = subtotal + tax;
            
            console.log(`Subtotal: $${subtotal.toFixed(2)}`);
            console.log(`Tax (8%): $${tax.toFixed(2)}`);
            console.log(`Total: $${total.toFixed(2)}`);
        };
        
        calculateTotal();
    </script>
</body>
</html>
