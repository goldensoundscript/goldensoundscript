# Sutha Electronics - E-commerce Website

A modern, fully-functional e-commerce website built with HTML, CSS, and JavaScript. Features a responsive design, shopping cart, checkout system, authentication, and API integration.

## Features

✨ **Core Features:**
- 📄 Responsive multi-page design (Home, Products, Cart, Checkout, Auth)
- 🛒 Shopping cart management with local storage
- 💳 Complete checkout process with order handling
- 🔐 User authentication (Login/Register)
- 🔍 Product filtering and search
- 📱 Mobile-first responsive design
- 💻 Modern UI with smooth animations
- 📊 Product catalog with ratings and reviews

## Project Structure

```
website/
├── index.html              # Homepage
├── products.html           # Products catalog page
├── cart.html              # Shopping cart page
├── checkout.html          # Checkout page
├── auth.html              # Login/Register page
├── package.json           # Project dependencies
├── css/
│   └── styles.css         # Main stylesheet
├── js/
│   ├── api.js             # API service & mock data
│   ├── cart.js            # Cart management
│   ├── script.js          # Homepage scripts
│   ├── products.js        # Products page scripts
│   ├── cart-page.js       # Cart page scripts
│   ├── auth.js            # Authentication scripts
│   └── checkout.js        # Checkout scripts
├── assets/
│   └── images/            # Product images
└── api/                   # Backend API folder (for future use)
```

## Getting Started

### Prerequisites
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Node.js (optional, for running a development server)

### Installation

1. **Clone or download the project:**
   ```bash
   git clone <repository-url>
   cd website
   ```

2. **Open in VS Code:**
   ```bash
   code .
   ```

3. **Start a local server:**
   
   **Option 1: Using Python (if installed):**
   ```bash
   python -m http.server 8000
   # or for Python 2:
   python -m SimpleHTTPServer 8000
   ```

   **Option 2: Using Node.js HTTP Server:**
   ```bash
   npx http-server .
   ```

   **Option 3: Using VS Code Live Server Extension:**
   - Install "Live Server" extension
   - Right-click `index.html` → "Open with Live Server"

4. **Access the website:**
   - Open `http://localhost:8000` (or the port shown by your server)

## Features Overview

### 1. Homepage
- Hero section with call-to-action
- Featured products showcase
- Benefits section
- Navigation to other pages

### 2. Products Page
- Complete product catalog
- Search functionality
- Filter by category
- Filter by price range
- Product cards with ratings

### 3. Shopping Cart
- View all cart items
- Update quantities
- Remove items
- Order summary with:
  - Subtotal
  - Shipping cost (free over $50)
  - Tax (10%)
  - Total

### 4. Checkout
- Billing information form
- Payment information form
- Order summary
- Form validation
- Card number formatting
- Expiry date formatting

### 5. Authentication
- Login form
- Registration form
- User profile display
- Logout functionality
- Session management with localStorage

## API Integration

The project uses a modular `APIService` class for backend communication. Currently uses mock data via localStorage.

### To Connect to a Real Backend:

1. **Update API endpoints in `js/api.js`:**
   ```javascript
   const API_BASE_URL = 'https://your-api-domain.com/api';
   ```

2. **Uncomment the real API calls** in each method and comment out the mock implementations

3. **Available API endpoints to implement:**
   - `POST /auth/login` - User login
   - `POST /auth/register` - User registration
   - `GET /products` - Get all products
   - `GET /products/:id` - Get single product
   - `POST /orders` - Create order
   - `GET /orders` - Get user orders
   - `POST /payments` - Process payment
   - `PUT /user/profile` - Update user profile

### Example Backend Implementation:

See the `api/` folder for example backend structure (Node.js/Express recommended)

## Authentication

The website includes a complete authentication system:

- **Login:** Email and password authentication
- **Register:** New user registration with validation
- **Session Management:** Uses localStorage for session persistence
- **Password Requirements:** Currently basic validation (can be enhanced)
- **User Data Storage:** Stored in browser localStorage (implement proper backend for production)

## Shopping Cart

Cart features include:

- **Add to Cart:** Add products with quantity
- **Update Quantity:** Change quantity directly in cart
- **Remove Items:** Remove specific products
- **Persistent Storage:** Cart saved in localStorage
- **Cart Count:** Badge shows total items in cart

## Checkout Process

Complete checkout flow:

1. Fill in billing information
2. Enter payment details
3. Review order summary
4. Submit order
5. Order confirmation (mock for now)

## Styling

The website uses a modern design system with:

- **Color Scheme:**
  - Primary: #007bff (Blue)
  - Secondary: #6c757d (Gray)
  - Success: #28a745 (Green)
  - Danger: #dc3545 (Red)

- **Typography:** Segoe UI, system fonts
- **Responsive Breakpoints:**
  - Desktop: 1200px+
  - Tablet: 768px - 1199px
  - Mobile: Below 768px

- **Animations:**
  - Smooth transitions
  - Hover effects
  - Slide-in notifications

## Database Integration

For production use, implement the following database schema:

### Users Table
```sql
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Products Table
```sql
CREATE TABLE products (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(255) NOT NULL,
  category VARCHAR(100),
  price DECIMAL(10, 2) NOT NULL,
  description TEXT,
  rating DECIMAL(3, 1),
  reviews INT DEFAULT 0,
  stock INT DEFAULT 0
);
```

### Orders Table
```sql
CREATE TABLE orders (
  id INT PRIMARY KEY AUTO_INCREMENT,
  user_id INT NOT NULL,
  order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  status VARCHAR(50) DEFAULT 'pending',
  total DECIMAL(10, 2) NOT NULL,
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### Order Items Table
```sql
CREATE TABLE order_items (
  id INT PRIMARY KEY AUTO_INCREMENT,
  order_id INT NOT NULL,
  product_id INT NOT NULL,
  quantity INT NOT NULL,
  price DECIMAL(10, 2) NOT NULL,
  FOREIGN KEY (order_id) REFERENCES orders(id),
  FOREIGN KEY (product_id) REFERENCES products(id)
);
```

## Payment Integration

Currently uses mock payment processing. To integrate real payments:

1. **Stripe:** Install stripe.js library
2. **PayPal:** Use PayPal SDK
3. **Razorpay:** Implement Razorpay API
4. **Square:** Use Square payment form

Update `APIService.processPayment()` method with your payment provider.

## Security Considerations

⚠️ **Important for Production:**

1. **Never store passwords in localStorage**
2. **Use HTTPS for all transactions**
3. **Implement proper backend authentication**
4. **Use secure payment processing (PCI-DSS compliant)**
5. **Validate all user inputs server-side**
6. **Use environment variables for API keys**
7. **Implement CSRF protection**
8. **Use secure cookies for session management**

## Browser Compatibility

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Performance Optimization

Suggestions for production:

1. Minify CSS and JavaScript
2. Compress images
3. Use lazy loading for product images
4. Implement service workers for offline support
5. Cache static assets
6. Use CDN for content delivery

## Troubleshooting

### Cart not persisting?
- Check browser localStorage is enabled
- Clear browser cache and try again

### Products not loading?
- Check browser console for errors
- Verify api.js is loaded correctly
- Check network requests

### Payment failing?
- Verify payment backend is running
- Check payment processor credentials
- Review payment error messages

## Contributing

To add new features:

1. Create feature branch
2. Make changes
3. Test thoroughly
4. Submit pull request

## Future Enhancements

- [ ] Product reviews and ratings system
- [ ] Wishlist functionality
- [ ] Email notifications
- [ ] Order tracking
- [ ] Admin dashboard
- [ ] Inventory management
- [ ] Multiple payment methods
- [ ] Customer service chat
- [ ] Product recommendations
- [ ] Analytics integration

## License

This project is licensed under the MIT License - see LICENSE file for details.

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Contact: support@techstore.com
- Documentation: See inline code comments

## Deployment

### Deploy to Netlify:
```bash
npm run build  # If using build tools
# Then drag and drop the website folder to Netlify
```

### Deploy to GitHub Pages:
```bash
git push origin main
# Enable GitHub Pages in repository settings
```

### Deploy to Vercel:
```bash
vercel
```

---

**Happy Coding! 🚀**

For more information, visit the project documentation or contact the development team.
