# Quick Start Guide

## 🚀 5-Minute Setup

### Step 1: Start a Local Server

Choose one of these options:

**Option A: Python (Built-in)**
```bash
cd c:\website
python -m http.server 8000
```

**Option B: Node.js HTTP Server**
```bash
cd c:\website
npm install http-server
npx http-server .
```

**Option C: VS Code Live Server**
- Install "Live Server" extension in VS Code
- Right-click `index.html` → "Open with Live Server"

### Step 2: Open in Browser
- Navigate to `http://localhost:8000`
- You should see the TechStore homepage

### Step 3: Test Features

1. **Browse Products:**
   - Click "Products" or "Shop Now"
   - Try search and filters
   - Add products to cart

2. **Test Cart:**
   - Click cart icon or "Cart" in menu
   - Update quantities
   - Remove items
   - View order summary

3. **Test Checkout:**
   - Click "Proceed to Checkout"
   - Fill in billing information
   - Enter payment details (any number works in demo)
   - Submit order

4. **Test Authentication:**
   - Click "Login" in menu
   - Try Login or Register
   - See your profile
   - Logout

---

## 📁 Project Files Explained

### HTML Pages
| File | Purpose |
|------|---------|
| `index.html` | Homepage with hero section and featured products |
| `products.html` | Product catalog with search and filters |
| `cart.html` | Shopping cart page |
| `checkout.html` | Checkout with payment form |
| `auth.html` | Login and registration |

### JavaScript Files
| File | Purpose |
|------|---------|
| `js/api.js` | API service, mock data, and backend communication |
| `js/cart.js` | Shopping cart management and localStorage |
| `js/script.js` | Homepage functionality |
| `js/products.js` | Product page filtering and search |
| `js/cart-page.js` | Cart page display and management |
| `js/auth.js` | Login, registration, and user profiles |
| `js/checkout.js` | Checkout form and order processing |

### Styling
| File | Purpose |
|------|---------|
| `css/styles.css` | All website styling and responsive design |

### Configuration
| File | Purpose |
|------|---------|
| `package.json` | Project metadata and dependencies |
| `README.md` | Full documentation |
| `QUICKSTART.md` | This file |

---

## 🔧 Configuration

### Change Store Name
Edit in all HTML files:
```html
<h1>TechStore</h1>  <!-- Change to your store name -->
```

### Change Colors
Edit `css/styles.css`:
```css
:root {
    --primary-color: #007bff;      /* Change blue to your color */
    --secondary-color: #6c757d;
    --success-color: #28a745;
    --danger-color: #dc3545;
}
```

### Change API Endpoint
Edit `js/api.js`:
```javascript
const API_BASE_URL = 'http://localhost:3000/api'; // Your API URL
```

### Add Products
Edit `js/api.js`, update `MOCK_PRODUCTS` array:
```javascript
const MOCK_PRODUCTS = [
    {
        id: 1,
        name: 'Your Product',
        price: 99.99,
        // ... more fields
    }
];
```

---

## 💾 Data Storage

Currently, the website uses **localStorage** for:
- Shopping cart
- User sessions
- Application state

This means data persists in the browser but is lost if cleared.

### To Use a Real Database:
1. Build a backend API (see `api/server.js`)
2. Uncomment the fetch() calls in `js/api.js`
3. Replace mock data with API responses

---

## 🔐 Authentication Testing

### Test Login
1. Go to Auth page
2. Register a new account (any email/password works)
3. Auto-logged in after registration
4. Visit different pages, stay logged in
5. Click logout

### Test Registration
1. Email can be anything (no validation)
2. Password must match confirm password
3. User data saved in localStorage

---

## 🛒 Shopping Flow

1. **Browse:** Go to Products page
2. **Search:** Use search box or filters
3. **Add:** Click "Add to Cart"
4. **Review:** Click Cart in menu
5. **Modify:** Change quantities or remove items
6. **Checkout:** Click "Proceed to Checkout"
7. **Complete:** Fill forms and submit

---

## 🐛 Troubleshooting

### Issue: "Page not found"
- Make sure server is running
- Check URL is correct (http://localhost:8000)
- Refresh browser (Ctrl+R)

### Issue: Cart data lost
- Check if localStorage is enabled
- Clear browser cache doesn't always clear localStorage
- Use browser DevTools (F12) → Application → Local Storage

### Issue: Links not working
- Make sure you're using http://localhost, not file://
- Server must be running

### Issue: Styling looks wrong
- Hard refresh (Ctrl+Shift+R)
- Check console for CSS errors (F12)

---

## 📱 Mobile Testing

To test on mobile:

**Option 1: Local Network**
1. Find your computer's IP: `ipconfig` (Windows) or `ifconfig` (Mac/Linux)
2. Access from phone: `http://YOUR_IP:8000`

**Option 2: Browser DevTools**
1. Open DevTools (F12)
2. Click device icon (top-left)
3. Select mobile device

**Option 3: Browser Resize**
- Just resize your desktop browser to test responsiveness

---

## 🚀 Next Steps

### To Add Backend:
1. Create Node.js/Express API (see `api/server.js`)
2. Connect database (MySQL/MongoDB)
3. Update `API_BASE_URL` in `js/api.js`
4. Replace mock functions with API calls
5. Deploy backend and frontend

### To Deploy:
- **Netlify:** Drag and drop folder
- **GitHub Pages:** Push to main branch
- **Vercel:** Connect GitHub repo
- **Your Server:** FTP or Git deploy

### To Enhance:
- Add product images
- Implement email notifications
- Add admin dashboard
- Build order tracking
- Integrate payment processors
- Add customer reviews
- Implement wishlists

---

## 📞 Support

- Check the full README.md for detailed documentation
- Review inline code comments
- Check browser console (F12) for errors
- See JavaScript files for implementation details

---

## 🎓 Learning Resources

**Frontend:**
- MDN Web Docs
- W3Schools
- FreeCodeCamp

**Backend:**
- Node.js Guide
- Express.js Docs
- SQL Tutorials

**Deployment:**
- Netlify Docs
- Vercel Docs
- GitHub Pages Guide

---

**Happy selling! 🎉**
