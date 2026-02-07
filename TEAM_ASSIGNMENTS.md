# Team Task Assignments - Client-Side Online Pharmacy Project
**Project Repository:** wachanga173/Client-Side-Online-Pharmacy-Project  
**Deployment:** GitHub Pages  
**Backend:** Supabase (serverless database & auth)

---

## 🎉 **IMPORTANT UPDATE - Database Ready!**

**Date:** February 7, 2026  
**Status:** ✅ **ALL DATABASE TABLES CREATED AND READY**

The Supabase database is now fully set up with all required tables:
- ✅ **products** - Product catalog (10 sample products loaded)
- ✅ **users** - User profiles with role-based access
- ✅ **orders** - Order management with auto-generated order numbers
- ✅ **cart** - Shopping cart functionality
- ✅ **reviews** - Product reviews and ratings

**All tables have:**
- Row Level Security (RLS) enabled with proper policies
- Indexes for optimal performance
- Auto-updating timestamps
- Foreign key relationships

**Supabase Credentials Available in:** `js/config.js`

**🚀 Team members can now start implementing their assigned features!**

---

## 📋 Team Database Access Matrix

| Team Member | Primary Tables | Operations | Additional Access |
|-------------|---------------|------------|-------------------|
| **I.N.N.O.C.E.N.T** | `users` | CREATE, READ, UPDATE | Supabase Auth |
| **Isabell Wanjiku** | `products` | READ | - |
| **OBUYA ODUOR HEZEKIAH** | `cart`, `products` | CREATE, READ, UPDATE, DELETE (cart) | Real-time subscriptions |
| **Samuel0096** | `orders`, `cart` | CREATE, READ (orders)<br>DELETE (cart after order) | - |
| **AdongoSharine Mulindi** | `products`, `users`, `orders`, `reviews` | Full CRUD on all tables | Admin role required |
| **Techwizbiz** | `cart` | READ (for cart count) | Real-time subscriptions |
| **Titus** | All tables | Testing & Support | Assist with all integrations |
| **vikitar** | `products`, `reviews` | READ (products)<br>CREATE, READ (reviews) | - |
| **washington-dave-dc** | - | Minimal database use | Focus on utilities |
| **wachanga173** | All tables | Full access & coordination | Database management |

### **Key Notes:**
- **Admin Operations**: Only users with `role = 'admin'` can manage products, view all orders, and moderate reviews
- **Customer Operations**: Regular users can only access their own cart, orders, and reviews
- **RLS Policies**: All tables have Row Level Security enabled - test with different user roles
- **Real-time Features**: Cart and orders support real-time updates via Supabase subscriptions

---

## 🚀 Project Setup & Infrastructure

### **Supabase Configuration**
- **Service:** Supabase (https://supabase.com) - provides PostgreSQL database, authentication, real-time subscriptions, and storage
- **Client Library:** CDN via `<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>`
- **Configuration:** `js/config.js` - Supabase URL and anon key (safe to expose publicly)
- **Security:** Row Level Security (RLS) policies protect data, NOT the API key
- **CORS:** Supabase allows `https://wachanga173.github.io` origin

### **Database Schema Tables**
- `products` - Product catalog (id, name, description, price, image_url, category, stock, created_at)
- `users` - User profiles (id, email, full_name, role, created_at) - synced with Supabase Auth
- `orders` - Order records (id, user_id, total, status, items, shipping_info, created_at)
- `cart` - Shopping cart items (id, user_id, product_id, quantity, created_at)
- `reviews` - Product reviews (id, product_id, user_id, rating, comment, created_at)

### **Authentication**
- Supabase Auth handles user signup, login, password reset
- JWT tokens stored in localStorage automatically by Supabase client
- Protected routes check `supabase.auth.getUser()`
- Role-based access: `admin` and `customer` roles

### **Storage Buckets**
- `product-images` - Product photos (publicly accessible)
- `user-avatars` - Profile pictures (authenticated access)

### **Deployment Process**
1. Push to `main` branch
2. GitHub Pages automatically deploys from root or `gh-pages` branch
3. Site available at `https://wachanga173.github.io/Client-Side-Online-Pharmacy-Project/`
4. No build step needed (vanilla JS project)

---

## 👥 Team Member Assignments

### 1. **I.N.N.O.C.E.N.T** (Dev-Felix001)
**Primary Focus: Authentication & User Management**

**Pages & Styling:**
- `pages/login.html` - Login page HTML
- `pages/register.html` - Registration page HTML  
- `pages/profile.html` - User profile page HTML
- `css/pages/auth.css` - Login/register styling
- `css/pages/profile.css` - Profile page styling

**JavaScript:**
- `js/services/auth.js` - Supabase Auth integration
  - `signUp(email, password, userData)` - Register new users
  - `signIn(email, password)` - Login users
  - `signOut()` - Logout users
  - `resetPassword(email)` - Password reset
  - `getCurrentUser()` - Get logged-in user
  - `updateProfile(userId, updates)` - Update user profile
- `js/pages/profile.js` - Profile page logic

**Supabase Integration:**
```javascript
// Example: Sign up with Supabase
const { data, error } = await supabase.auth.signUp({
  email: email,
  password: password,
  options: {
    data: { full_name: fullName }
  }
});
```

**Deliverables:**
- Working registration with email verification
- Secure login/logout functionality
- Profile management (view/edit user details)
- Password reset flow
- Session persistence across page reloads
- Protected route middleware

---

### 2. **Isabell Wanjiku** (Isabel53)
**Primary Focus: Product Catalog & Display**

**Pages & Styling:**
- `pages/products.html` - Product listing page
- `css/pages/products.css` - Products page styling

**JavaScript:**
- `js/pages/products.js` - Product listing logic
- `js/components/productCard.js` - Reusable product card component

**Supabase Integration:**
```javascript
// Fetch all products with filters
const { data, error } = await supabase
  .from('products')
  .select('*')
  .eq('category', selectedCategory)
  .gte('price', minPrice)
  .lte('price', maxPrice)
  .order('created_at', { ascending: false });
```

**Deliverables:**
- Product grid/list display
- Category filtering (dropdown/sidebar)
- Price range filtering
- Search functionality (by name/description)
- Sort options (price, name, date)
- Pagination or infinite scroll
- Product card component with image, name, price, "Add to Cart" button
- Loading states and error handling
- Image lazy loading from Supabase Storage

---

### 3. **OBUYA ODUOR HEZEKIAH** (OBUYA123)
**Primary Focus: Shopping Cart System**

**Pages & Styling:**
- `pages/cart.html` - Shopping cart page
- `css/pages/cart.css` - Cart page styling

**JavaScript:**
- `js/services/cart.js` - Cart service layer
- `js/pages/cart.js` - Cart page logic

**Supabase Integration:**
```javascript
// Add item to cart (for logged-in users)
const { data, error } = await supabase
  .from('cart')
  .insert({ user_id: userId, product_id: productId, quantity: qty });

// Use localStorage for guest users, sync on login
```

**Deliverables:**
- Add to cart functionality
- Update quantity (increment/decrement)
- Remove from cart
- Cart item counter in header (real-time)
- Subtotal, tax, and total calculations
- Guest cart (localStorage) with sync to Supabase on login
- Real-time cart updates using Supabase subscriptions
- Empty cart state with "Continue Shopping" CTA
- Cart persistence across sessions

---

### 4. **Samuel0096**
**Primary Focus: Checkout & Payment Interface**

**Pages & Styling:**
- `pages/checkout.html` - Checkout page
- `css/pages/checkout.css` - Checkout styling

**JavaScript:**
- `js/pages/checkout.js` - Checkout logic

**Supabase Integration:**
```javascript
// Create order
const { data, error } = await supabase
  .from('orders')
  .insert({
    user_id: userId,
    items: cartItems,
    total: totalAmount,
    shipping_info: shippingData,
    status: 'pending'
  });

// Clear cart after successful order
await supabase.from('cart').delete().eq('user_id', userId);
```

**Deliverables:**
- Multi-step checkout form (shipping, payment, review)
- Form validation for all fields
- Order summary with itemized list
- Shipping address form
- Payment information form (mock payment gateway)
- Order confirmation page
- Order email/notification (using Supabase Edge Functions if needed)
- Order submission to Supabase `orders` table
- Redirect to confirmation with order ID
- Print receipt functionality

---

### 5. **AdongoSharine Mulindi** (shar979)
**Primary Focus: Admin Panel & Dashboard**

**Pages & Styling:**
- `pages/admin.html` - Admin dashboard
- `css/pages/admin.css` - Admin panel styling

**JavaScript:**
- `js/pages/admin.js` - Admin dashboard logic

**Supabase Integration:**
```javascript
// Admin role check
const { data: { user } } = await supabase.auth.getUser();
const { data } = await supabase
  .from('users')
  .select('role')
  .eq('id', user.id)
  .single();

if (data.role !== 'admin') redirect('/');

// CRUD operations on products
// Create
await supabase.from('products').insert(newProduct);
// Read
await supabase.from('products').select('*');
// Update
await supabase.from('products').update(updates).eq('id', productId);
// Delete
await supabase.from('products').delete().eq('id', productId);
```

**Deliverables:**
- Admin authentication and role-based access control
- Product management dashboard (CRUD operations)
- Product form (add/edit with image upload to Supabase Storage)
- Order management (view all orders, update status)
- User management (view users, change roles)
- Analytics dashboard (total sales, order count, popular products)
- Data tables with search and sorting
- Responsive admin UI

---

### 6. **Techwizbiz**
**Primary Focus: UI Components & Reusable Modules**

**JavaScript:**
- `js/components/header.js` - Site header/navigation
- `js/components/footer.js` - Site footer
- `js/components/modal.js` - Modal dialog system
- `js/components/toast.js` - Toast notifications

**Supabase Integration:**
```javascript
// Header: Show user info and cart count
supabase.auth.onAuthStateChange((event, session) => {
  if (session) {
    // Show logged-in state
    updateHeaderUI(session.user);
  } else {
    // Show logged-out state
    updateHeaderUI(null);
  }
});

// Real-time cart count
supabase
  .channel('cart-changes')
  .on('postgres_changes', 
    { event: '*', schema: 'public', table: 'cart' },
    updateCartCount
  )
  .subscribe();
```

**Deliverables:**
- Dynamic navigation header with logo, links, cart icon, user menu
- User menu dropdown (Profile, Orders, Logout)
- Cart count badge (real-time updates)
- Responsive mobile menu (hamburger)
- Footer with links, social media, copyright
- Reusable modal component (confirm dialogs, image previews)
- Toast notification system (success, error, info, warning)
- Loading spinner component
- Breadcrumb navigation
- All components should work across all pages

---

### 7. **Titus** (titus06ondeu)
**Primary Focus: Core Styling, Responsive Design & Supabase Integration Support**

**CSS:**
- `css/style.css` - Global styles, typography, CSS variables
- `css/components.css` - Component styles (buttons, cards, forms, badges)
- `css/responsive.css` - Media queries for all breakpoints

**Supabase Support:**
- Help implement Supabase client initialization in `js/config.js`
- Assist with real-time subscription setup across modules
- Debug Supabase queries and error handling
- Test Supabase RLS policies with different user roles
- Support image upload to Supabase Storage buckets

**Deliverables:**
- CSS variables for colors, spacing, fonts, shadows
- Consistent design system (primary, secondary, success, danger colors)
- Button styles (primary, secondary, outline, icon buttons)
- Form input styles (text, select, checkbox, radio)
- Card component styling
- Responsive grid system
- Mobile-first responsive layouts (mobile, tablet, desktop)
- Smooth transitions and hover effects
- Loading animations and skeletons
- Print styles for receipts/invoices
- Cross-browser compatibility
- **Work closely with wachanga173 on all Supabase integrations**

---

### 8. **vikitar**
**Primary Focus: Product Details & Search Functionality**

**Pages & Styling:**
- `pages/product-detail.html` - Individual product page
- `css/pages/product-detail.css` - Product detail styling

**Supabase Integration:**
```javascript
// Get product with reviews
const { data: product } = await supabase
  .from('products')
  .select(`
    *,
    reviews (
      id,
      rating,
      comment,
      created_at,
      users (full_name)
    )
  `)
  .eq('id', productId)
  .single();

// Add review
await supabase.from('reviews').insert({
  product_id: productId,
  user_id: userId,
  rating: rating,
  comment: comment
});

// Search products
const { data } = await supabase
  .from('products')
  .select('*')
  .or(`name.ilike.%${query}%,description.ilike.%${query}%`);
```

**Deliverables:**
- Product detail page with large images
- Image gallery with thumbnails and zoom
- Product information (name, price, description, specs)
- Stock availability indicator
- Add to cart button with quantity selector
- Related products section (same category)
- Product reviews and ratings display
- Review submission form (authenticated users only)
- Average rating calculation and stars display
- Global search functionality (search bar in header)
- Search results page with highlighting

---

### 9. **washington-dave-dc**
**Primary Focus: Static Pages & Utility Functions**

**Pages & Styling:**
- `pages/about.html` - About us page
- `css/pages/about.css` - About page styling
- `pages/directors.html` - Directors/team page
- `css/pages/directors.css` - Directors page styling
- `pages/contact.html` - Contact us page
- `css/pages/contact.css` - Contact page styling

**JavaScript:**
- `js/utils/helpers.js` - Helper functions
- `js/utils/validation.js` - Form validation
- `js/utils/storage.js` - LocalStorage utilities

**Utilities to Implement:**
```javascript
// helpers.js
- formatCurrency(amount) - "$1,234.56"
- formatDate(date) - "Feb 7, 2026"
- generateOrderId() - "ORD-2026-001"
- debounce(fn, delay) - Debounce search
- truncateText(text, length)
- calculateDiscount(price, percentage)

// validation.js
- validateEmail(email)
- validatePassword(password) - min 8 chars, number, special char
- validatePhone(phone)
- validateCreditCard(number)
- validateForm(formData, rules)

// storage.js
- saveToLocalStorage(key, value)
- getFromLocalStorage(key)
- removeFromLocalStorage(key)
- clearLocalStorage()
```

**Deliverables:**
- About page (company mission, history, values)
- Directors/team page (profiles, photos, bios)
- Contact us page (contact form, location, business hours)
- Contact form submission handling
- Comprehensive utility functions
- Form validation library
- LocalStorage wrapper with error handling
- Guest cart management in localStorage
- Data sanitization functions
- Error logging utilities

---

### 10. **wachanga173** (YOU - Overall Coordinator)
**Primary Focus: Supabase Setup, Integration & Project Coordination**

**Supabase Database Setup:**

1. **Create Tables:**
```sql
-- Products table
CREATE TABLE products (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  name TEXT NOT NULL,
  description TEXT,
  price DECIMAL(10,2) NOT NULL,
  image_url TEXT,
  category TEXT,
  stock INTEGER DEFAULT 0,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Users table (extends auth.users)
CREATE TABLE users (
  id UUID PRIMARY KEY REFERENCES auth.users,
  email TEXT UNIQUE NOT NULL,
  full_name TEXT,
  role TEXT DEFAULT 'customer',
  created_at TIMESTAMP DEFAULT NOW()
);

-- Orders table
CREATE TABLE orders (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id),
  items JSONB NOT NULL,
  total DECIMAL(10,2) NOT NULL,
  status TEXT DEFAULT 'pending',
  shipping_info JSONB,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Cart table
CREATE TABLE cart (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES users(id),
  product_id UUID REFERENCES products(id),
  quantity INTEGER DEFAULT 1,
  created_at TIMESTAMP DEFAULT NOW(),
  UNIQUE(user_id, product_id)
);

-- Reviews table
CREATE TABLE reviews (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  product_id UUID REFERENCES products(id),
  user_id UUID REFERENCES users(id),
  rating INTEGER CHECK (rating >= 1 AND rating <= 5),
  comment TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);
```

2. **Row Level Security (RLS) Policies:**
```sql
-- Enable RLS
ALTER TABLE products ENABLE ROW LEVEL SECURITY;
ALTER TABLE users ENABLE ROW LEVEL SECURITY;
ALTER TABLE orders ENABLE ROW LEVEL SECURITY;
ALTER TABLE cart ENABLE ROW LEVEL SECURITY;
ALTER TABLE reviews ENABLE ROW LEVEL SECURITY;

-- Products: Public read, admin write
CREATE POLICY "Anyone can view products" ON products FOR SELECT USING (true);
CREATE POLICY "Admins can manage products" ON products FOR ALL 
  USING (auth.jwt() ->> 'role' = 'admin');

-- Cart: Users manage their own cart
CREATE POLICY "Users can view own cart" ON cart FOR SELECT 
  USING (auth.uid() = user_id);
CREATE POLICY "Users can manage own cart" ON cart FOR ALL 
  USING (auth.uid() = user_id);

-- Orders: Users see their own orders, admins see all
CREATE POLICY "Users can view own orders" ON orders FOR SELECT 
  USING (auth.uid() = user_id);
CREATE POLICY "Admins can view all orders" ON orders FOR SELECT 
  USING (auth.jwt() ->> 'role' = 'admin');

-- Reviews: Anyone can read, authenticated users can write
CREATE POLICY "Anyone can view reviews" ON reviews FOR SELECT USING (true);
CREATE POLICY "Authenticated users can add reviews" ON reviews FOR INSERT 
  WITH CHECK (auth.role() = 'authenticated');
```

3. **Storage Buckets:**
- Create `product-images` bucket (public)
- Create `user-avatars` bucket (authenticated)

4. **Configuration File** `js/config.js`:
```javascript
// Supabase Configuration
const SUPABASE_URL = 'https://xyzcompany.supabase.co'; // Replace with actual
const SUPABASE_ANON_KEY = 'your-anon-key-here'; // Replace with actual

// Initialize Supabase client
const supabase = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

// App Configuration
const APP_CONFIG = {
  appName: 'Pharmacare',
  currency: 'USD',
  taxRate: 0.08, // 8%
  freeShippingThreshold: 50,
  itemsPerPage: 12
};

export { supabase, APP_CONFIG };
```

5. **Data Migration:**
- Migrate products from `data/products.json` to Supabase
- Upload product images to Supabase Storage
- Update image URLs in database

**Additional Responsibilities:**
- Set up GitHub Pages deployment
- Code review all pull requests
- Ensure consistent coding standards
- Integration testing across modules
- Performance optimization
- Error monitoring and debugging
- Documentation and team support
- Deployment and production monitoring

---

## 🔄 Development Workflow

### **Git Workflow:**
1. Clone repository: `git clone https://github.com/wachanga173/Client-Side-Online-Pharmacy-Project.git`
2. Create feature branch: `git checkout -b feature/your-feature-name`
3. Make changes and commit: `git commit -m "Description"`
4. Push to GitHub: `git push origin feature/your-feature-name`
5. Create Pull Request for review
6. After approval, merge to `main`
7. GitHub Pages auto-deploys from `main`

### **Branch Naming Convention:**
- `feature/cart-functionality`
- `feature/product-search`
- `bugfix/login-error`
- `style/responsive-navbar`

### **Commit Message Format:**
```
[Component] Brief description

- Detailed point 1
- Detailed point 2
```

Example:
```
[Auth] Implement user registration with Supabase

- Add signup form validation
- Integrate Supabase Auth
- Handle error states
```

### **Code Standards:**
- Use ES6+ JavaScript features
- Camelcase for variables/functions: `getUserData()`
- PascalCase for classes/components: `ProductCard`
- Consistent indentation (2 or 4 spaces)
- Comments for complex logic
- Error handling with try/catch
- Async/await for Supabase calls

### **Testing Checklist:**
- [ ] Test on Chrome, Firefox, Safari, Edge
- [ ] Test on mobile devices (iOS, Android)
- [ ] Test with different user roles (guest, customer, admin)
- [ ] Test error scenarios (no internet, invalid data)
- [ ] Test Supabase RLS policies
- [ ] Check console for errors
- [ ] Validate forms with incorrect data
- [ ] Test real-time features (cart updates, etc.)

---

## 📋 Integration Dependencies

**Critical Path:**
1. **wachanga173** + **Titus**: Supabase setup → Everyone else can start
2. **Techwizbiz**: Header/Footer → All pages can use
3. **I.N.N.O.C.E.N.T**: Auth service → Admin, Profile, Cart, Checkout depend on this
4. **Isabell**: Products service → Product details, Cart, Checkout need this
5. **OBUYA**: Cart service → Checkout depends on this

**Communication Channels:**
- GitHub Issues for bugs and feature requests
- Pull Request comments for code review
- Discord/Slack for daily standups (if available)
- Document decisions in repository Wiki

**Weekly Milestones:**
- **Week 1**: Supabase setup, basic structure, header/footer
- **Week 2**: Auth, products listing, cart functionality
- **Week 3**: Checkout, admin panel, product details
- **Week 4**: Styling, responsive design, utilities, static pages
- **Week 5**: Testing, bug fixes, deployment, documentation

---

## ✅ Collaborative Responsibilities

**Everyone should:**
- ✅ Pull latest changes from `main` before starting work
- ✅ Test Supabase integration in their modules
- ✅ Review at least 2 pull requests per week
- ✅ Update `README.md` with features they implement
- ✅ Help debug issues across all modules
- ✅ Ask questions when blocked (don't waste time stuck)
- ✅ Write clean, documented code
- ✅ Test on mobile and desktop
- ✅ Handle loading states and errors gracefully
- ✅ Follow security best practices (validate inputs, sanitize data)

**Nobody works in isolation** - this is a collaborative team project!

---

## 🔧 Quick Start Guide

### **For Team Members:**

1. **Clone the repository:**
```bash
git clone https://github.com/wachanga173/Client-Side-Online-Pharmacy-Project.git
cd Client-Side-Online-Pharmacy-Project
```

2. **✅ Supabase is Ready!** Credentials are already in `js/config.js`

3. **Verify you can access Supabase:**
   - Open browser console (F12)
   - Navigate to the homepage or products page
   - Check console logs for "Supabase client initialized successfully"
   - You should see products loading from the database

4. **Create your feature branch:**
```bash
git checkout -b feature/your-task-name
```

5. **Start coding!** Open `index.html` in a browser or use Live Server

6. **Test your changes** thoroughly

7. **Commit and push:**
```bash
git add .
git commit -m "[YourComponent] What you did"
git push origin feature/your-task-name
```

8. **Create Pull Request** on GitHub

---

## � Database Schema Reference

### **Available Tables & Fields**

#### **products**
```javascript
{
  id: UUID,
  name: TEXT,
  description: TEXT,
  price: DECIMAL(10,2),
  image_url: TEXT,
  category: TEXT,
  stock: INTEGER,
  created_at: TIMESTAMP
}
```

#### **users**
```javascript
{
  id: UUID (references auth.users),
  email: TEXT,
  full_name: TEXT,
  role: TEXT ('customer' | 'admin'),
  phone: TEXT,
  address: JSONB,
  created_at: TIMESTAMP,
  updated_at: TIMESTAMP
}
```

#### **orders**
```javascript
{
  id: UUID,
  user_id: UUID,
  items: JSONB,
  subtotal: DECIMAL(10,2),
  tax: DECIMAL(10,2),
  shipping_cost: DECIMAL(10,2),
  total: DECIMAL(10,2),
  status: TEXT ('pending' | 'processing' | 'shipped' | 'delivered' | 'cancelled'),
  shipping_info: JSONB,
  payment_method: TEXT,
  order_number: TEXT (auto-generated: ORD-YYYYMMDD-000001),
  created_at: TIMESTAMP,
  updated_at: TIMESTAMP
}
```

#### **cart**
```javascript
{
  id: UUID,
  user_id: UUID,
  product_id: UUID,
  quantity: INTEGER,
  created_at: TIMESTAMP,
  updated_at: TIMESTAMP
}
```

#### **reviews**
```javascript
{
  id: UUID,
  product_id: UUID,
  user_id: UUID,
  rating: INTEGER (1-5),
  comment: TEXT,
  verified_purchase: BOOLEAN,
  helpful_count: INTEGER,
  created_at: TIMESTAMP,
  updated_at: TIMESTAMP
}
```

### **Example Supabase Queries**

```javascript
// Get all products
const { data, error } = await supabase
  .from('products')
  .select('*');

// Get user's cart with product details
const { data, error } = await supabase
  .from('cart')
  .select(`
    *,
    products (
      name,
      price,
      image_url,
      stock
    )
  `)
  .eq('user_id', userId);

// Get product with reviews
const { data, error } = await supabase
  .from('products')
  .select(`
    *,
    reviews (
      rating,
      comment,
      created_at,
      users (full_name)
    )
  `)
  .eq('id', productId)
  .single();

// Create order
const { data, error } = await supabase
  .from('orders')
  .insert({
    user_id: userId,
    items: cartItems,
    subtotal: subtotal,
    tax: tax,
    shipping_cost: shipping,
    total: total,
    shipping_info: shippingData,
    payment_method: 'credit_card'
  })
  .select()
  .single();
```

---

## �📚 Resources

- **Supabase Docs:** https://supabase.com/docs
- **JavaScript ES6+:** https://developer.mozilla.org/en-US/docs/Web/JavaScript
- **Git Guide:** https://www.atlassian.com/git
- **GitHub Pages:** https://docs.github.com/en/pages

---

**Last Updated:** February 7, 2026  
**Project Coordinator:** wachanga173  
**Team Size:** 10 developers
