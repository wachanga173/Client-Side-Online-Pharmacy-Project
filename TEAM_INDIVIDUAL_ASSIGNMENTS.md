# Individual Team Assignments - Online Pharmacy Project
**Date:** February 10, 2026  
**Project:** Client-Side Online Pharmacy with Supabase Backend

---

## 📋 **Assignment Overview**

Each team member has **3 main responsibilities**:

1. 🔧 **Complete Your Module** - Implement your assigned functionality
2. 📖 **Read & Understand Existing Code** - Study what's already built
3. 🎨 **Build Your Profile Page** - Create your personal director profile page

**All roles are balanced with equal workload and importance!**

---

## 1️⃣ **I.N.N.O.C.E.N.T** (Dev-Felix001)
### 🎯 **Role: Director of Authentication & User Management**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**
Your authentication system is **COMPLETE**! Study these files to understand how it works:

**Files to Read:**
- `js/services/auth.js` - Full Supabase Auth integration (400+ lines)
- `js/pages/profile.js` - Profile management with tabs
- `pages/login.html` - Login page
- `pages/register.html` - Registration page
- `pages/profile.html` - User profile page
- `css/pages/auth.css` - Login/register styling
- `css/pages/profile.css` - Profile page styling

**Key Functions Implemented:**
```javascript
- register(userData) // Sign up new users
- login(email, password) // User login
- logout() // Sign out
- getCurrentUser() // Get logged-in user
- updateUserProfile(updates) // Update profile
- uploadProfilePhoto(file) // Upload avatar
- resetPassword(email) // Password reset
- onAuthStateChange(callback) // Auth state listener
```

### 🔨 **Your Tasks:**

#### **Task 1: Enhance Authentication Features**
**Files:** `js/services/auth.js`, `pages/profile.html`

Add these optional features:
- [ ] Email change functionality
- [ ] Two-factor authentication (2FA)
- [ ] Social login (Google/GitHub)
- [ ] Remember me checkbox
- [ ] Password strength indicator
- [ ] Session timeout warnings

#### **Task 2: User Profile Enhancements**
**Files:** `js/pages/profile.js`, `css/pages/profile.css`

Improve the profile page:
- [ ] Add profile completion percentage
- [ ] Add user preferences section (theme, notifications)
- [ ] Add account deletion with confirmation
- [ ] Add export user data feature
- [ ] Improve profile photo cropping/editing
- [ ] Add bio/about me section

#### **Task 3: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/innocent.html`
- `css/directors/innocent.css`

**Creative Freedom:** Design your personal profile page showcasing:
- Your photo and bio
- Your authentication expertise
- Technologies you mastered (Supabase Auth, JWT, RLS)
- Security best practices you implemented
- Links to your GitHub, LinkedIn, portfolio

**Inspiration Ideas:**
- Security-themed design with lock icons
- Animated login flow demonstration
- Interactive security tips
- Dark mode hacker aesthetic
- Professional resume-style layout

### 🗄️ **Your Supabase Tables:**
- **`users` table** - READ, UPDATE user profiles
- **Supabase Auth** - Full access to authentication APIs
- **`user-avatars` bucket** - Storage for profile photos

### 📚 **Resources:**
- Supabase Auth docs: https://supabase.com/docs/guides/auth
- Already implemented in: `js/services/auth.js`

---

## 2️⃣ **Isabell Wanjiku** (Isabel53)
### 🎯 **Role: Director of Product Catalog & Display**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**
Basic product display exists - study these files:

**Files to Read:**
- `js/pages/products.js` - Basic product listing
- `js/services/products.js` - Product service with Supabase
- `pages/products.html` - Products page structure
- `css/pages/products.css` - Products styling
- `js/components/productCard.js` - Product card component

**Current Features:**
- Basic product grid display
- Product cards with image, name, price
- Add to cart buttons
- Supabase integration for fetching products

### 🔨 **Your Tasks:**

#### **Task 1: Advanced Filtering System** 🎯 **PRIORITY**
**Files:** `js/pages/products.js`, `pages/products.html`, `css/pages/products.css`

Implement comprehensive filters:
- [ ] **Category Filter** - Dropdown or sidebar with all categories
- [ ] **Price Range Filter** - Dual-handle slider (min/max)
- [ ] **Brand Filter** - Checkboxes for different brands
- [ ] **Availability Filter** - In stock / Out of stock
- [ ] **Rating Filter** - 5 stars, 4+, 3+, etc.
- [ ] Show active filters as removable chips/tags
- [ ] "Clear All Filters" button

**Implementation Guide:**
```javascript
// In js/pages/products.js
async function loadProducts(filters = {}) {
    let query = supabase.from('products').select('*');
    
    if (filters.category) {
        query = query.eq('category', filters.category);
    }
    if (filters.minPrice) {
        query = query.gte('price', filters.minPrice);
    }
    if (filters.maxPrice) {
        query = query.lte('price', filters.maxPrice);
    }
    
    const { data, error } = await query;
    renderProducts(data);
}
```

#### **Task 2: Sorting & Search**
**Files:** `js/pages/products.js`, `pages/products.html`

Add sorting options:
- [ ] Sort by: Price (Low to High)
- [ ] Sort by: Price (High to Low)
- [ ] Sort by: Name (A-Z)
- [ ] Sort by: Newest First
- [ ] Sort by: Best Selling
- [ ] Sort by: Highest Rated
- [ ] Quick search within current results

#### **Task 3: Pagination & View Options**
**Files:** `js/pages/products.js`, `css/pages/products.css`

Add pagination and display options:
- [ ] Pagination (12, 24, 48 items per page)
- [ ] Grid view / List view toggle
- [ ] Show total product count
- [ ] "Load More" button option
- [ ] Remember user's view preference

#### **Task 4: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/isabell.html`
- `css/directors/isabell.css`

**Creative Freedom:** Showcase your product expertise:
- Your photo and introduction
- Product catalog designs you created
- Filter UI mockups or demos
- E-commerce inspiration board
- Links to portfolio/social media

**Design Ideas:**
- E-commerce themed with product cards
- Interactive filter demonstration
- Product showcase grid
- Shopping-inspired aesthetic
- Modern marketplace design

### 🗄️ **Your Supabase Tables:**
- **`products` table** - READ all product data
  - Columns: id, name, description, price, category, brand, stock, rating, image_url, created_at

### 📚 **Key Files You'll Modify:**
```
js/pages/products.js          (main work here)
pages/products.html           (add filter UI)
css/pages/products.css        (style filters)
js/services/products.js       (read only - understand API)
```

---

## 3️⃣ **OBUYA ODUOR HEZEKIAH** (OBUYA123)
### 🎯 **Role: Director of Shopping Cart Systems**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**
Cart structure exists but has a critical bug:

**Files to Read:**
- `js/services/cart.js` - Cart service (localStorage-based)
- `js/pages/cart.js` - Cart page logic
- `pages/cart.html` - Cart page structure
- `css/pages/cart.css` - Cart styling
- `js/components/header.js` - Cart count in header

**Current Issues:**
- 🔴 **CRITICAL BUG:** Products don't save to cart (localStorage issue)
- Cart uses localStorage instead of Supabase
- No real-time updates
- No guest cart sync when logging in

### 🔨 **Your Tasks:**

#### **Task 1: Fix Cart Bug** 🔴 **CRITICAL - DO THIS FIRST**
**Files:** `js/services/cart.js`, `js/pages/products.js`

**The Problem:** When users click "Add to Cart", the message shows but cart remains empty.

**Root Cause:** `js/services/cart.js` expects products in `localStorage.pharmacy_products` but this is empty.

**Solution Option A - Quick Fix:**
```javascript
// In js/pages/products.js or home.js
// Cache products to localStorage when loading
async function loadProducts() {
    const { data } = await supabase.from('products').select('*');
    localStorage.setItem('pharmacy_products', JSON.stringify(data));
    renderProducts(data);
}
```

**Solution Option B - Better Approach:** Modify `cart.js` to fetch from Supabase directly:
```javascript
// In js/services/cart.js - modify addToCart function
export async function addToCart(productId, quantity = 1) {
    // Fetch product from Supabase instead of localStorage
    const { data: product } = await window.supabase
        .from('products')
        .select('*')
        .eq('id', productId)
        .single();
    
    if (!product) return { success: false };
    
    // Rest of cart logic...
}
```

#### **Task 2: Migrate Cart to Supabase** 🎯 **HIGH PRIORITY**
**Files:** `js/services/cart.js`, entire file rewrite

Convert from localStorage to Supabase `cart` table:

**Features to implement:**
- [ ] Save cart items to Supabase for logged-in users
- [ ] Guest carts still use localStorage
- [ ] When guest logs in, sync localStorage cart to Supabase
- [ ] Real-time cart updates (if user adds from another device)
- [ ] Persist cart across devices
- [ ] Clear cart after checkout

**Implementation Guide:**
```javascript
// Add to cart for logged-in users
export async function addToCart(productId, quantity) {
    const user = await window.supabase.auth.getUser();
    
    if (user.data.user) {
        // Logged in - use Supabase
        const { data, error } = await window.supabase
            .from('cart')
            .insert({ 
                user_id: user.data.user.id, 
                product_id: productId, 
                quantity 
            });
    } else {
        // Guest - use localStorage
        const cart = getStorage(CONFIG.STORAGE_KEYS.CART) || [];
        // ... localStorage logic
    }
}

// Sync guest cart when logging in
export async function syncGuestCart() {
    const guestCart = getStorage(CONFIG.STORAGE_KEYS.CART) || [];
    const user = await window.supabase.auth.getUser();
    
    if (user.data.user && guestCart.length > 0) {
        // Upload guest items to Supabase
        for (const item of guestCart) {
            await window.supabase.from('cart').insert({
                user_id: user.data.user.id,
                product_id: item.productId,
                quantity: item.quantity
            });
        }
        // Clear localStorage cart
        removeStorage(CONFIG.STORAGE_KEYS.CART);
    }
}
```

#### **Task 3: Real-Time Cart Updates**
**Files:** `js/services/cart.js`, `js/components/header.js`

Implement real-time features:
- [ ] Subscribe to cart changes
- [ ] Update cart count in header automatically
- [ ] Show toast when cart updates
- [ ] Handle concurrent updates from multiple devices

```javascript
// Real-time subscription
const cartSubscription = supabase
    .channel('cart_changes')
    .on('postgres_changes', 
        { event: '*', schema: 'public', table: 'cart' }, 
        (payload) => {
            console.log('Cart changed!', payload);
            refreshCartUI();
        }
    )
    .subscribe();
```

#### **Task 4: Enhanced Cart Features**
**Files:** `js/pages/cart.js`, `pages/cart.html`, `css/pages/cart.css`

Add user-friendly features:
- [ ] Update quantity with +/- buttons
- [ ] Remove item with confirmation
- [ ] "Save for later" feature
- [ ] Apply promo codes
- [ ] Calculate shipping costs
- [ ] Show estimated delivery date
- [ ] "Continue Shopping" link
- [ ] Cart summary sidebar (sticky)

#### **Task 5: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/obuya.html`
- `css/directors/obuya.css`

**Creative Freedom:** Showcase your cart expertise:
- Your photo and bio
- Shopping cart system you built
- Supabase real-time demos
- Cart UI/UX improvements
- Technical challenges solved

**Design Ideas:**
- Shopping cart themed design
- Animated cart interactions
- E-commerce checkout flow
- Modern minimalist style
- Interactive cart demo

### 🗄️ **Your Supabase Tables:**
- **`cart` table** - CREATE, READ, UPDATE, DELETE
  - Columns: id, user_id, product_id, quantity, created_at
- **`products` table** - READ (to get product details)
- **Real-time subscriptions** - Monitor cart changes

### 📚 **Key Files You'll Modify:**
```
js/services/cart.js           (complete rewrite - main work)
js/pages/cart.js              (update to use new cart service)
js/components/header.js       (update cart count)
pages/cart.html               (enhance UI)
css/pages/cart.css            (improve styling)
```

---

## 4️⃣ **Samuel** (Samuel0096)
### 🎯 **Role: Director of Checkout & Payment Integration**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**

**Files to Read:**
- `pages/checkout.html` - Basic checkout page structure
- `css/pages/checkout.css` - Checkout styling
- `js/pages/checkout.js` - Checkout logic (may need creation)

**Current State:**
- Basic HTML form exists
- No form validation
- No order submission
- No payment integration

### 🔨 **Your Tasks:**

#### **Task 1: Multi-Step Checkout Form** 🎯 **PRIORITY**
**Files:** `js/pages/checkout.js`, `pages/checkout.html`, `css/pages/checkout.css`

Create a 3-step checkout process:

**Step 1: Shipping Information**
- [ ] Full name (required)
- [ ] Email (required, validation)
- [ ] Phone number (required, format validation)
- [ ] Address line 1 (required)
- [ ] Address line 2 (optional)
- [ ] City (required)
- [ ] State/Province (required)
- [ ] ZIP/Postal Code (required)
- [ ] Country (dropdown)
- [ ] Save address for future orders (checkbox)

**Step 2: Payment Method**
- [ ] Credit/Debit Card option
- [ ] Mobile Money (M-Pesa, etc.)
- [ ] Cash on Delivery
- [ ] Card details form (if card selected):
  - Card number (format: #### #### #### ####)
  - Expiry date (MM/YY)
  - CVV (3-4 digits)
  - Cardholder name
- [ ] Secure payment badge/icons

**Step 3: Order Review & Confirmation**
- [ ] Show shipping address
- [ ] Show payment method
- [ ] Show cart items with images
- [ ] Show subtotal, shipping, tax, total
- [ ] Terms & conditions checkbox
- [ ] Place Order button

**Implementation Guide:**
```javascript
// js/pages/checkout.js
let currentStep = 1;

function initCheckout() {
    loadCheckoutData();
    setupStepNavigation();
    setupFormValidation();
}

function nextStep() {
    if (validateCurrentStep()) {
        currentStep++;
        showStep(currentStep);
    }
}

function validateCurrentStep() {
    const step = document.querySelector(`#step-${currentStep}`);
    const inputs = step.querySelectorAll('input[required]');
    
    for (const input of inputs) {
        if (!input.value) {
            showToast('Please fill all required fields', 'error');
            return false;
        }
    }
    return true;
}
```

#### **Task 2: Order Submission to Supabase**
**Files:** `js/pages/checkout.js`

Submit order to database:
- [ ] Create order in `orders` table
- [ ] Generate unique order number (e.g., ORD-20260210-001)
- [ ] Save order items as JSON
- [ ] Save shipping information
- [ ] Calculate and save totals
- [ ] Set initial status to 'pending'
- [ ] Clear user's cart after successful order

```javascript
async function submitOrder(orderData) {
    const user = await window.supabase.auth.getUser();
    
    const order = {
        user_id: user.data.user?.id || null,
        order_number: generateOrderNumber(),
        items: JSON.stringify(orderData.items),
        total: orderData.total,
        shipping_info: JSON.stringify(orderData.shipping),
        payment_method: orderData.paymentMethod,
        status: 'pending'
    };
    
    const { data, error } = await window.supabase
        .from('orders')
        .insert(order)
        .select()
        .single();
    
    if (!error) {
        // Clear cart
        await window.supabase
            .from('cart')
            .delete()
            .eq('user_id', user.data.user.id);
        
        // Redirect to confirmation page
        window.location.href = `order-confirmation.html?id=${data.id}`;
    }
}

function generateOrderNumber() {
    const date = new Date();
    const dateStr = date.toISOString().slice(0, 10).replace(/-/g, '');
    const random = Math.floor(Math.random() * 1000).toString().padStart(3, '0');
    return `ORD-${dateStr}-${random}`;
}
```

#### **Task 3: Order Confirmation Page**
**Files:** Create `pages/order-confirmation.html`, `css/pages/order-confirmation.css`, `js/pages/order-confirmation.js`

Build a beautiful order success page:
- [ ] Success message with checkmark animation
- [ ] Order number (large, bold)
- [ ] Estimated delivery date
- [ ] Order summary (items, total)
- [ ] Shipping address
- [ ] Payment method
- [ ] Track Order button
- [ ] Continue Shopping button
- [ ] Print Receipt button

#### **Task 4: Form Validation & User Experience**
**Files:** `js/pages/checkout.js`, `js/utils/validation.js`

Add robust validation:
- [ ] Real-time field validation (as user types)
- [ ] Email format validation
- [ ] Phone number format validation
- [ ] Credit card number validation (Luhn algorithm)
- [ ] ZIP code format validation
- [ ] Required field indicators (*)
- [ ] Error messages below fields
- [ ] Disable "Next" button until valid
- [ ] Show progress indicator (Step 1 of 3)

#### **Task 5: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/samuel.html`
- `css/directors/samuel.css`

**Creative Freedom:** Showcase your checkout expertise:
- Your photo and introduction
- Checkout flow you designed
- Payment integration skills
- UX improvements you made
- Order processing logic

**Design Ideas:**
- Payment/checkout themed design
- Credit card visual elements
- Progress indicator showcase
- Clean, trustworthy aesthetic
- E-commerce payment flow demo

### 🗄️ **Your Supabase Tables:**
- **`orders` table** - CREATE, READ orders
  - Columns: id, user_id, order_number, items (JSON), total, shipping_info (JSON), payment_method, status, created_at
- **`cart` table** - DELETE (clear after checkout)
- **`products` table** - READ (get product details for order)

### 📚 **Key Files You'll Modify:**
```
js/pages/checkout.js          (main work - create if doesn't exist)
pages/checkout.html           (enhance form)
css/pages/checkout.css        (style steps)
pages/order-confirmation.html (create new)
js/pages/order-confirmation.js (create new)
```

---

## 5️⃣ **AdongoSharine Mulindi** (shar979)
### 🎯 **Role: Director of Admin Panel & Dashboard**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**

**Files to Read:**
- `pages/admin.html` - Basic admin page structure
- `css/pages/admin.css` - Admin styling
- `js/pages/admin.js` - Admin logic (minimal)

**Current State:**
- Basic admin layout exists
- No CRUD operations implemented
- No role-based access control
- No analytics dashboard

### 🔨 **Your Tasks:**

#### **Task 1: Admin Access Control** 🔴 **DO THIS FIRST**
**Files:** `js/pages/admin.js`, `js/services/auth.js`

Implement role-based security:
- [ ] Check if user is logged in
- [ ] Check if user has `role = 'admin'` in users table
- [ ] Redirect non-admins to home page
- [ ] Show admin menu only to admins in header

```javascript
// js/pages/admin.js
async function initAdminPage() {
    const user = await window.supabase.auth.getUser();
    
    if (!user.data.user) {
        window.location.href = 'login.html';
        return;
    }
    
    // Check admin role
    const { data: profile } = await window.supabase
        .from('users')
        .select('role')
        .eq('id', user.data.user.id)
        .single();
    
    if (profile?.role !== 'admin') {
        showToast('Access denied. Admin only.', 'error');
        window.location.href = 'index.html';
        return;
    }
    
    loadAdminDashboard();
}
```

#### **Task 2: Product Management (CRUD)** 🎯 **PRIORITY**
**Files:** `js/pages/admin.js`, `pages/admin.html`, `css/pages/admin.css`

Build complete product management:

**Features:**
- [ ] View all products in table/grid
- [ ] Search/filter products
- [ ] Add new product (modal/form)
- [ ] Edit existing product (modal/form)
- [ ] Delete product (with confirmation)
- [ ] Upload product image to Supabase Storage
- [ ] Bulk delete products
- [ ] Export products to CSV

**Add Product Form Fields:**
- Product name
- Description (textarea)
- Category (dropdown)
- Brand
- Price
- Stock quantity
- Image upload
- Status (Active/Inactive)

**Implementation Example:**
```javascript
// Create Product
async function createProduct(productData) {
    // Upload image first
    let imageUrl = null;
    if (productData.imageFile) {
        const fileName = `${Date.now()}-${productData.imageFile.name}`;
        const { data, error } = await window.supabase.storage
            .from('product-images')
            .upload(fileName, productData.imageFile);
        
        if (!error) {
            imageUrl = `${window.supabase.storage.from('product-images').getPublicUrl(fileName).data.publicUrl}`;
        }
    }
    
    // Insert product
    const { data, error } = await window.supabase
        .from('products')
        .insert({
            name: productData.name,
            description: productData.description,
            price: productData.price,
            category: productData.category,
            brand: productData.brand,
            stock: productData.stock,
            image_url: imageUrl
        });
    
    if (!error) {
        showToast('Product added successfully!', 'success');
        loadProducts();
    }
}

// Update Product
async function updateProduct(id, updates) {
    const { error } = await window.supabase
        .from('products')
        .update(updates)
        .eq('id', id);
    
    if (!error) {
        showToast('Product updated!', 'success');
        loadProducts();
    }
}

// Delete Product
async function deleteProduct(id) {
    if (confirm('Are you sure you want to delete this product?')) {
        const { error } = await window.supabase
            .from('products')
            .delete()
            .eq('id', id);
        
        if (!error) {
            showToast('Product deleted!', 'success');
            loadProducts();
        }
    }
}
```

#### **Task 3: Order Management**
**Files:** `js/pages/admin.js`, `pages/admin.html`

Build order management system:
- [ ] View all orders in table
- [ ] Filter orders by status (pending, processing, shipped, delivered, cancelled)
- [ ] Search orders by order number or customer email
- [ ] View order details (items, customer, shipping)
- [ ] Update order status
- [ ] Mark as paid/unpaid
- [ ] Export orders to CSV
- [ ] Order statistics (total orders, revenue)

```javascript
async function loadOrders() {
    const { data: orders } = await window.supabase
        .from('orders')
        .select(`
            *,
            users (full_name, email)
        `)
        .order('created_at', { ascending: false });
    
    renderOrdersTable(orders);
}

async function updateOrderStatus(orderId, newStatus) {
    const { error } = await window.supabase
        .from('orders')
        .update({ status: newStatus })
        .eq('id', orderId);
    
    if (!error) {
        showToast('Order status updated!', 'success');
        loadOrders();
    }
}
```

#### **Task 4: User Management**
**Files:** `js/pages/admin.js`, `pages/admin.html`

Manage users:
- [ ] View all users in table
- [ ] Search users by name/email
- [ ] View user details and order history
- [ ] Change user role (admin/customer)
- [ ] Deactivate/activate user accounts
- [ ] User registration statistics

#### **Task 5: Analytics Dashboard** 🎯 **CREATIVE**
**Files:** `js/pages/admin.js`, `pages/admin.html`, `css/pages/admin.css`

Create an analytics overview (no charts library needed, use CSS):
- [ ] Total revenue (card with big number)
- [ ] Total orders (card)
- [ ] Total products (card)
- [ ] Total customers (card)
- [ ] Recent orders table (last 5)
- [ ] Low stock alerts (products with stock < 10)
- [ ] Best-selling products (top 5)
- [ ] Revenue by category (simple bar display)

**Dashboard Layout:**
```html
<div class="dashboard-stats">
    <div class="stat-card">
        <h3>Total Revenue</h3>
        <p class="stat-value">$12,450</p>
        <span class="stat-change">+12% from last month</span>
    </div>
    <!-- More stat cards -->
</div>
```

#### **Task 6: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/sharine.html`
- `css/directors/sharine.css`

**Creative Freedom:** Showcase your admin work:
- Your photo and bio
- Admin dashboard you built
- Data management skills
- UI/UX for admin tools
- Security measures implemented

**Design Ideas:**
- Dashboard/analytics themed
- Professional admin interface
- Data visualization elements
- Modern SaaS aesthetic
- Command center style

### 🗄️ **Your Supabase Tables:**
- **`products` table** - Full CRUD access
- **`orders` table** - READ, UPDATE (status)
- **`users` table** - READ, UPDATE (role, status)
- **`reviews` table** - READ, DELETE (moderate)
- **`product-images` bucket** - UPLOAD, DELETE images

### 📚 **Key Files You'll Modify:**
```
js/pages/admin.js             (main work - 500+ lines)
pages/admin.html              (enhance with tabs/sections)
css/pages/admin.css           (professional styling)
```

---

## 6️⃣ **Techwizbiz**
### 🎯 **Role: Director of UI Components & Reusable Modules**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**

**Files to Read:**
- `js/components/header.js` - Header with navigation
- `js/components/footer.js` - Footer component
- `js/components/toast.js` - Toast notifications
- `js/components/modal.js` - Modal dialogs
- `js/components/productCard.js` - Product card component
- `css/components.css` - Component styling

**Current Features:**
- ✅ Header with logo and navigation
- ✅ Footer with links
- ✅ Toast notifications (success, error, info)
- ✅ Modal system
- ✅ Product cards

**Issues:**
- ❌ Mobile menu doesn't work
- ❌ Cart count not updating in real-time
- ❌ User dropdown menu missing

### 🔨 **Your Tasks:**

#### **Task 1: Fix Mobile Menu** 🔴 **PRIORITY**
**Files:** `js/components/header.js`, `css/components.css`, `css/responsive.css`

Make the hamburger menu work:

```javascript
// js/components/header.js
function initHeader() {
    renderHeader();
    setupMobileMenu();
    updateCartCount();
    updateUserMenu();
}

function setupMobileMenu() {
    const hamburger = document.querySelector('.hamburger-menu');
    const navMenu = document.querySelector('.nav-menu');
    const overlay = document.createElement('div');
    overlay.className = 'mobile-overlay';
    
    hamburger?.addEventListener('click', () => {
        navMenu?.classList.toggle('active');
        hamburger.classList.toggle('active');
        
        if (navMenu?.classList.contains('active')) {
            document.body.appendChild(overlay);
            overlay.classList.add('active');
            document.body.style.overflow = 'hidden';
        } else {
            overlay.remove();
            document.body.style.overflow = '';
        }
    });
    
    overlay.addEventListener('click', () => {
        navMenu?.classList.remove('active');
        hamburger?.classList.remove('active');
        overlay.remove();
        document.body.style.overflow = '';
    });
}
```

**CSS for mobile menu:**
```css
/* css/responsive.css */
@media (max-width: 768px) {
    .nav-menu {
        position: fixed;
        top: 0;
        right: -100%;
        width: 80%;
        max-width: 300px;
        height: 100vh;
        background: white;
        transition: right 0.3s ease;
        z-index: 1000;
        padding: 2rem 1rem;
        box-shadow: -2px 0 10px rgba(0,0,0,0.1);
    }
    
    .nav-menu.active {
        right: 0;
    }
    
    .mobile-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.5);
        z-index: 999;
    }
    
    .hamburger-menu {
        display: flex;
        flex-direction: column;
        gap: 5px;
        cursor: pointer;
    }
    
    .hamburger-menu span {
        width: 25px;
        height: 3px;
        background: var(--dark-color);
        transition: all 0.3s;
    }
    
    .hamburger-menu.active span:nth-child(1) {
        transform: rotate(45deg) translate(5px, 5px);
    }
    
    .hamburger-menu.active span:nth-child(2) {
        opacity: 0;
    }
    
    .hamburger-menu.active span:nth-child(3) {
        transform: rotate(-45deg) translate(7px, -6px);
    }
}
```

#### **Task 2: Real-Time Cart Count** 🎯 **IMPORTANT**
**Files:** `js/components/header.js`

Update cart count automatically:

```javascript
// Real-time cart count
let cartSubscription = null;

async function updateCartCount() {
    const user = await window.supabase.auth.getUser();
    
    if (user.data.user) {
        // Get cart count from Supabase
        const { count } = await window.supabase
            .from('cart')
            .select('*', { count: 'exact', head: true })
            .eq('user_id', user.data.user.id);
        
        const badge = document.querySelector('.cart-count');
        if (badge) {
            badge.textContent = count || 0;
            badge.style.display = count > 0 ? 'flex' : 'none';
        }
        
        // Subscribe to real-time updates
        if (!cartSubscription) {
            cartSubscription = window.supabase
                .channel('cart_count')
                .on('postgres_changes',
                    { event: '*', schema: 'public', table: 'cart', filter: `user_id=eq.${user.data.user.id}` },
                    () => {
                        updateCartCount(); // Refresh count
                    }
                )
                .subscribe();
        }
    } else {
        // Guest cart from localStorage
        const cart = JSON.parse(localStorage.getItem('pharmacy_cart') || '[]');
        const badge = document.querySelector('.cart-count');
        if (badge) {
            badge.textContent = cart.length;
            badge.style.display = cart.length > 0 ? 'flex' : 'none';
        }
    }
}

// Call this when component loads
initHeader();
```

#### **Task 3: User Dropdown Menu**
**Files:** `js/components/header.js`, `css/components.css`

Add a user menu dropdown:

**Features:**
- [ ] Show user's name and avatar
- [ ] Dropdown menu on click
- [ ] Links: Profile, Orders, Settings, Logout
- [ ] Admin link (if user is admin)
- [ ] Smooth dropdown animation

```javascript
function renderUserMenu(user) {
    if (user) {
        return `
            <div class="user-menu">
                <button class="user-button" id="userMenuBtn">
                    <img src="${user.avatar || '/assets/images/default-avatar.png'}" alt="User" class="user-avatar">
                    <span>${user.full_name || 'User'}</span>
                    <i class="icon-chevron-down"></i>
                </button>
                <div class="user-dropdown" id="userDropdown">
                    <a href="profile.html" class="dropdown-item">
                        <i class="icon-user"></i> My Profile
                    </a>
                    <a href="profile.html#orders" class="dropdown-item">
                        <i class="icon-package"></i> My Orders
                    </a>
                    ${user.role === 'admin' ? `
                        <a href="admin.html" class="dropdown-item">
                            <i class="icon-settings"></i> Admin Panel
                        </a>
                    ` : ''}
                    <hr>
                    <button onclick="logout()" class="dropdown-item logout">
                        <i class="icon-logout"></i> Logout
                    </button>
                </div>
            </div>
        `;
    } else {
        return `
            <a href="login.html" class="btn btn-primary">Login</a>
        `;
    }
}

function setupUserDropdown() {
    const userBtn = document.getElementById('userMenuBtn');
    const dropdown = document.getElementById('userDropdown');
    
    userBtn?.addEventListener('click', (e) => {
        e.stopPropagation();
        dropdown?.classList.toggle('active');
    });
    
    document.addEventListener('click', () => {
        dropdown?.classList.remove('active');
    });
}
```

#### **Task 4: Enhanced Components**
**Files:** `js/components/`, `css/components.css`

Improve existing components:

**Toast Enhancements:**
- [ ] Add progress bar showing timeout
- [ ] Add close button
- [ ] Stack multiple toasts
- [ ] Different toast positions (top, bottom, left, right)

**Modal Enhancements:**
- [ ] Add modal sizes (small, medium, large, fullscreen)
- [ ] Add modal animations (fade, slide, zoom)
- [ ] Add confirmation modals (with Yes/No buttons)
- [ ] Close on outside click (optional)

**New Components to Create:**
- [ ] Loading spinner component
- [ ] Breadcrumb navigation
- [ ] Pagination component
- [ ] Rating stars component
- [ ] Image lightbox/gallery

#### **Task 5: Accessibility & UX**
**Files:** All component files

Add accessibility features:
- [ ] Keyboard navigation (Tab, Enter, Escape)
- [ ] ARIA labels and roles
- [ ] Focus management for modals
- [ ] Screen reader support
- [ ] Skip to main content link
- [ ] High contrast mode support

#### **Task 6: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/techwizbiz.html`
- `css/directors/techwizbiz.css`

**Creative Freedom:** Showcase your UI components:
- Your photo and bio
- Interactive component demos
- UI design philosophy
- Component library showcase
- JavaScript skills

**Design Ideas:**
- Component library style (Storybook-like)
- Interactive UI elements
- Animated components showcase
- Modern design system
- Tech/developer aesthetic

### 🗄️ **Your Supabase Tables:**
- **`cart` table** - READ (for cart count)
- **`users` table** - READ (for user menu)
- **Real-time subscriptions** - Cart updates

### 📚 **Key Files You'll Modify:**
```
js/components/header.js       (main work)
js/components/footer.js       (minor updates)
js/components/toast.js        (enhancements)
js/components/modal.js        (enhancements)
css/components.css            (styling)
css/responsive.css            (mobile fixes)
```

---

## 7️⃣ **Titus** (titus06ondeu)
### 🎯 **Role: Director of Design & Supabase Integration**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**

**Files to Read:**
- `css/style.css` - Global styles and variables
- `css/components.css` - Component styling
- `css/responsive.css` - Responsive breakpoints
- `css/pages/*.css` - All page-specific styles
- `js/config.js` - Supabase configuration

**Current State:**
- Basic CSS architecture exists
- CSS variables defined
- Basic responsive design
- Component styles

### 🔨 **Your Tasks:**

#### **Task 1: Design System Refinement** 🎨 **CREATIVE**
**Files:** `css/style.css`, `css/components.css`

Enhance the global design system:

**Color System:**
- [ ] Define primary, secondary, accent colors
- [ ] Create color variants (light, dark)
- [ ] Add semantic colors (success, warning, error, info)
- [ ] Dark mode color scheme
- [ ] Accessible color contrast ratios

```css
/* css/style.css */
:root {
    /* Primary Colors */
    --primary-50: #e3f2fd;
    --primary-100: #bbdefb;
    --primary-500: #2196f3;
    --primary-700: #1976d2;
    --primary-900: #0d47a1;
    
    /* Semantic Colors */
    --success: #4caf50;
    --warning: #ff9800;
    --error: #f44336;
    --info: #2196f3;
    
    /* Neutrals */
    --gray-50: #fafafa;
    --gray-100: #f5f5f5;
    --gray-500: #9e9e9e;
    --gray-900: #212121;
    
    /* Spacing Scale */
    --space-1: 0.25rem;
    --space-2: 0.5rem;
    --space-3: 0.75rem;
    --space-4: 1rem;
    --space-6: 1.5rem;
    --space-8: 2rem;
    
    /* Typography */
    --font-size-xs: 0.75rem;
    --font-size-sm: 0.875rem;
    --font-size-base: 1rem;
    --font-size-lg: 1.125rem;
    --font-size-xl: 1.25rem;
    --font-size-2xl: 1.5rem;
    --font-size-3xl: 1.875rem;
    
    /* Border Radius */
    --radius-sm: 0.25rem;
    --radius-md: 0.5rem;
    --radius-lg: 1rem;
    --radius-full: 9999px;
    
    /* Shadows */
    --shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
    --shadow-md: 0 4px 6px rgba(0,0,0,0.1);
    --shadow-lg: 0 10px 15px rgba(0,0,0,0.1);
    --shadow-xl: 0 20px 25px rgba(0,0,0,0.15);
}

/* Dark Mode */
[data-theme="dark"] {
    --background: #1a1a1a;
    --text-color: #ffffff;
    --primary-500: #64b5f6;
}
```

**Typography System:**
- [ ] Font pairings (headings + body)
- [ ] Font sizes scale
- [ ] Line heights
- [ ] Letter spacing
- [ ] Font weights

**Spacing System:**
- [ ] Consistent spacing scale
- [ ] Margin/padding utilities
- [ ] Gap utilities for flex/grid

#### **Task 2: Responsive Design Overhaul**
**Files:** `css/responsive.css`, all page CSS files

Make everything mobile-first:

**Breakpoints:**
```css
/* Mobile First Approach */
/* Default: Mobile (< 640px) */

/* Tablet */
@media (min-width: 640px) { }

/* Desktop */
@media (min-width: 1024px) { }

/* Large Desktop */
@media (min-width: 1280px) { }
```

**Areas to improve:**
- [ ] Navigation menu (mobile/desktop)
- [ ] Product grid (1 col mobile → 4 col desktop)
- [ ] Forms (stack on mobile, side-by-side on desktop)
- [ ] Tables (horizontal scroll on mobile)
- [ ] Buttons (full width on mobile)
- [ ] Hero sections (text size adjustments)
- [ ] Footer (stack on mobile)

#### **Task 3: Animation & Interactions**
**Files:** `css/style.css`, `css/components.css`

Add smooth animations:

```css
/* Transitions */
.card {
    transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
    transform: translateY(-4px);
    box-shadow: var(--shadow-lg);
}

/* Animations */
@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

@keyframes slideUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.fade-in {
    animation: fadeIn 0.3s ease-in;
}

.slide-up {
    animation: slideUp 0.4s ease-out;
}

/* Loading Spinner */
@keyframes spin {
    to { transform: rotate(360deg); }
}

.spinner {
    border: 3px solid rgba(0,0,0,0.1);
    border-top-color: var(--primary-500);
    border-radius: 50%;
    width: 40px;
    height: 40px;
    animation: spin 0.6s linear infinite;
}
```

**Add animations for:**
- [ ] Button hover effects
- [ ] Card hover effects
- [ ] Modal open/close
- [ ] Toast slide in/out
- [ ] Page transitions
- [ ] Loading states
- [ ] Skeleton screens

#### **Task 4: Supabase Integration Testing** 🎯 **TECHNICAL**
**Files:** `js/services/*.js`, `js/pages/*.js`

Help team members test their Supabase integration:

**Test Areas:**
- [ ] **Authentication:** Login, register, logout flows
- [ ] **Products:** Fetch, filter, search
- [ ] **Cart:** Add, update, delete, sync
- [ ] **Orders:** Create, read orders
- [ ] **Real-time:** Test subscriptions work
- [ ] **RLS Policies:** Test users can only access their data
- [ ] **Storage:** Test image uploads work

**Create test utilities:**
```javascript
// js/utils/testSupabase.js
export async function testSupabaseConnection() {
    try {
        const { data, error } = await window.supabase
            .from('products')
            .select('count')
            .limit(1);
        
        if (error) throw error;
        console.log('✅ Supabase connected successfully');
        return true;
    } catch (error) {
        console.error('❌ Supabase connection failed:', error);
        return false;
    }
}

export async function testRLSPolicies() {
    // Test that users can't access other users' data
    // Test admin-only operations
    // Log results
}
```

#### **Task 5: Performance Optimization**
**Files:** All CSS files

Optimize for performance:
- [ ] Minify CSS (create `style.min.css`)
- [ ] Remove unused CSS
- [ ] Optimize images (compress, use WebP)
- [ ] Lazy load images
- [ ] Defer non-critical CSS
- [ ] Use CSS containment
- [ ] Optimize animations (use transform/opacity)

#### **Task 6: Dark Mode Implementation** 🌙
**Files:** `css/style.css`, `js/utils/theme.js`

Add dark mode toggle:

```javascript
// js/utils/theme.js
export function initTheme() {
    const saved = localStorage.getItem('theme') || 'light';
    setTheme(saved);
}

export function setTheme(theme) {
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('theme', theme);
}

export function toggleTheme() {
    const current = document.documentElement.getAttribute('data-theme') || 'light';
    const next = current === 'light' ? 'dark' : 'light';
    setTheme(next);
}
```

#### **Task 7: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/titus.html`
- `css/directors/titus.css`

**Creative Freedom:** Showcase your design skills:
- Your photo and bio
- Design system you created
- Color palettes and typography
- Animation examples
- Supabase integration work
- UI/UX improvements

**Design Ideas:**
- Designer portfolio style
- Animated/interactive showcase
- Color and typography demo
- Dark mode toggle on your page
- Modern, experimental design
- Glassmorphism or neumorphism effects

### 🗄️ **Your Supabase Tables:**
- **All tables** - Testing access for team
- **Storage buckets** - Testing uploads
- **Real-time** - Testing subscriptions

### 📚 **Key Files You'll Modify:**
```
css/style.css                 (main design system)
css/components.css            (component styling)
css/responsive.css            (mobile responsive)
css/pages/*.css               (all page styles)
js/utils/theme.js             (dark mode - create new)
```

---

## 8️⃣ **Vikitar**
### 🎯 **Role: Director of Product Details & Search**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**

**Files to Read:**
- `pages/product-detail.html` - Product detail page structure
- `css/pages/product-detail.css` - Product detail styling
- `js/services/products.js` - Product service
- `js/components/productCard.js` - Product card component

**Current State:**
- Basic product detail page exists
- No image gallery
- No reviews system
- No search functionality

### 🔨 **Your Tasks:**

#### **Task 1: Product Detail Page** 🎯 **PRIORITY**
**Files:** `js/pages/product-detail.js` (create), `pages/product-detail.html`, `css/pages/product-detail.css`

Build a complete product detail page:

**Layout Sections:**
1. **Product Gallery (Left Side)**
   - [ ] Main large image display
   - [ ] Thumbnail gallery (4-5 images)
   - [ ] Image zoom on hover
   - [ ] Lightbox on click (fullscreen view)
   - [ ] Image navigation arrows

2. **Product Info (Right Side)**
   - [ ] Product name (H1)
   - [ ] Price (large, bold)
   - [ ] Star rating with count (4.5 ★ 234 reviews)
   - [ ] Short description
   - [ ] Availability status (In Stock / Out of Stock)
   - [ ] SKU/Product ID
   - [ ] Category and brand tags
   - [ ] Quantity selector (+/- buttons)
   - [ ] Add to Cart button
   - [ ] Add to Wishlist button (heart icon)
   - [ ] Share buttons (social media)

3. **Product Tabs**
   - [ ] Description (full details)
   - [ ] Reviews (all customer reviews)
   - [ ] Specifications (table of specs)
   - [ ] Shipping Info

**Implementation Example:**
```javascript
// js/pages/product-detail.js
async function initProductDetail() {
    const productId = getQueryParam('id');
    if (!productId) {
        window.location.href = 'products.html';
        return;
    }
    
    await loadProduct(productId);
    await loadReviews(productId);
    await loadRelatedProducts(productId);
    setupImageGallery();
    setupTabs();
}

async function loadProduct(id) {
    const { data: product, error } = await window.supabase
        .from('products')
        .select('*')
        .eq('id', id)
        .single();
    
    if (error || !product) {
        showToast('Product not found', 'error');
        return;
    }
    
    renderProductDetails(product);
}

function renderProductDetails(product) {
    document.getElementById('productName').textContent = product.name;
    document.getElementById('productPrice').textContent = `$${product.price}`;
    document.getElementById('productImage').src = product.image_url;
    document.getElementById('productDescription').textContent = product.description;
    // ... more rendering
}

function setupImageGallery() {
    const mainImage = document.getElementById('mainImage');
    const thumbnails = document.querySelectorAll('.thumbnail');
    
    thumbnails.forEach(thumb => {
        thumb.addEventListener('click', (e) => {
            mainImage.src = e.target.dataset.full;
            thumbnails.forEach(t => t.classList.remove('active'));
            e.target.classList.add('active');
        });
    });
    
    // Zoom on hover
    mainImage.addEventListener('mousemove', (e) => {
        const rect = mainImage.getBoundingClientRect();
        const x = ((e.clientX - rect.left) / rect.width) * 100;
        const y = ((e.clientY - rect.top) / rect.height) * 100;
        mainImage.style.transformOrigin = `${x}% ${y}%`;
        mainImage.style.transform = 'scale(2)';
    });
    
    mainImage.addEventListener('mouseleave', () => {
        mainImage.style.transform = 'scale(1)';
    });
}
```

#### **Task 2: Reviews System** ⭐ **IMPORTANT**
**Files:** `js/pages/product-detail.js`, `pages/product-detail.html`

Build complete reviews functionality:

**Features:**
- [ ] Display all reviews for product
- [ ] Show reviewer name, date, rating
- [ ] Show review text
- [ ] Helpful votes (👍 Was this helpful?)
- [ ] Sort reviews (Most recent, Highest rated, Lowest rated)
- [ ] Filter by star rating (Show only 5★, 4★, etc.)
- [ ] Review statistics (% of 5★, 4★, 3★, 2★, 1★)
- [ ] Average rating calculation
- [ ] Write a review form (logged-in users only)
- [ ] Review submission with rating

**Implementation:**
```javascript
async function loadReviews(productId) {
    const { data: reviews } = await window.supabase
        .from('reviews')
        .select(`
            *,
            users (full_name)
        `)
        .eq('product_id', productId)
        .order('created_at', { ascending: false });
    
    calculateAverageRating(reviews);
    renderReviews(reviews);
}

function calculateAverageRating(reviews) {
    if (reviews.length === 0) return 0;
    
    const total = reviews.reduce((sum, r) => sum + r.rating, 0);
    const average = total / reviews.length;
    
    const breakdown = {
        5: reviews.filter(r => r.rating === 5).length,
        4: reviews.filter(r => r.rating === 4).length,
        3: reviews.filter(r => r.rating === 3).length,
        2: reviews.filter(r => r.rating === 2).length,
        1: reviews.filter(r => r.rating === 1).length
    };
    
    renderRatingStats(average, breakdown, reviews.length);
}

async function submitReview(productId, rating, comment) {
    const user = await window.supabase.auth.getUser();
    
    if (!user.data.user) {
        showToast('Please login to write a review', 'error');
        return;
    }
    
    const { error } = await window.supabase
        .from('reviews')
        .insert({
            product_id: productId,
            user_id: user.data.user.id,
            rating: rating,
            comment: comment
        });
    
    if (!error) {
        showToast('Review submitted!', 'success');
        loadReviews(productId); // Refresh
    }
}

function renderReviews(reviews) {
    const container = document.getElementById('reviewsList');
    
    if (reviews.length === 0) {
        container.innerHTML = '<p>No reviews yet. Be the first to review!</p>';
        return;
    }
    
    container.innerHTML = reviews.map(review => `
        <div class="review-card">
            <div class="review-header">
                <div class="review-author">
                    <strong>${review.users.full_name}</strong>
                    <div class="review-rating">
                        ${'★'.repeat(review.rating)}${'☆'.repeat(5 - review.rating)}
                    </div>
                </div>
                <span class="review-date">${formatDate(review.created_at)}</span>
            </div>
            <p class="review-comment">${review.comment}</p>
            <div class="review-actions">
                <button class="helpful-btn">👍 Helpful</button>
            </div>
        </div>
    `).join('');
}
```

#### **Task 3: Global Search Functionality** 🔍
**Files:** Create `js/pages/search.js`, `pages/search.html`, `css/pages/search.css`

Build a search page:

**Features:**
- [ ] Search box in header (already exists)
- [ ] Search results page
- [ ] Search by product name
- [ ] Search by description
- [ ] Search by category
- [ ] Highlight search terms in results
- [ ] Show number of results
- [ ] Sort search results
- [ ] Filter search results (by category, price)
- [ ] "Did you mean...?" suggestions

**Implementation:**
```javascript
// js/pages/search.js
async function performSearch(query) {
    if (!query || query.length < 2) return;
    
    const { data: products } = await window.supabase
        .from('products')
        .select('*')
        .or(`name.ilike.%${query}%,description.ilike.%${query}%,category.ilike.%${query}%`);
    
    renderSearchResults(products, query);
}

function renderSearchResults(products, query) {
    const container = document.getElementById('searchResults');
    const count = document.getElementById('resultCount');
    
    count.textContent = `${products.length} results for "${query}"`;
    
    if (products.length === 0) {
        container.innerHTML = `
            <div class="no-results">
                <h3>No products found for "${query}"</h3>
                <p>Try different keywords or browse our categories</p>
            </div>
        `;
        return;
    }
    
    container.innerHTML = products.map(product => `
        <div class="search-result-card">
            <img src="${product.image_url}" alt="${product.name}">
            <div class="result-info">
                <h3>${highlightText(product.name, query)}</h3>
                <p>${highlightText(product.description, query)}</p>
                <span class="price">$${product.price}</span>
                <a href="product-detail.html?id=${product.id}" class="btn">View Product</a>
            </div>
        </div>
    `).join('');
}

function highlightText(text, query) {
    const regex = new RegExp(`(${query})`, 'gi');
    return text.replace(regex, '<mark>$1</mark>');
}
```

#### **Task 4: Related Products**
**Files:** `js/pages/product-detail.js`

Show related products:
- [ ] "You May Also Like" section
- [ ] Show 4-6 related products from same category
- [ ] Product cards with images
- [ ] Quick add to cart buttons

```javascript
async function loadRelatedProducts(productId) {
    // Get current product's category
    const { data: currentProduct } = await window.supabase
        .from('products')
        .select('category')
        .eq('id', productId)
        .single();
    
    // Get other products in same category
    const { data: related } = await window.supabase
        .from('products')
        .select('*')
        .eq('category', currentProduct.category)
        .neq('id', productId)
        .limit(6);
    
    renderRelatedProducts(related);
}
```

#### **Task 5: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/vikitar.html`
- `css/directors/vikitar.css`

**Creative Freedom:** Showcase your search expertise:
- Your photo and bio
- Product detail pages you designed
- Search functionality
- Review system
- UI/UX work

**Design Ideas:**
- Product-focused design
- Search engine themed
- E-commerce catalog style
- Grid of product images
- Modern shopping experience

### 🗄️ **Your Supabase Tables:**
- **`products` table** - READ product details
- **`reviews` table** - CREATE, READ reviews
  - Columns: id, product_id, user_id, rating, comment, created_at

### 📚 **Key Files You'll Modify:**
```
js/pages/product-detail.js    (create - main work)
pages/product-detail.html     (enhance)
css/pages/product-detail.css  (styling)
js/pages/search.js            (create - search page)
pages/search.html             (create - search page)
css/pages/search.css          (create - search styling)
```

---

## 9️⃣ **Washington Dave** (washington-dave-dc)
### 🎯 **Role: Director of Static Pages & Utilities**

### ✅ **What's Already Implemented (READ & UNDERSTAND)**

**Files to Read:**
- `js/utils/helpers.js` - Helper functions COMPLETE ✅
- `js/utils/validation.js` - Validation utilities COMPLETE ✅
- `js/utils/storage.js` - localStorage wrapper COMPLETE ✅
- `pages/about.html` - About page (basic)
- `pages/contact.html` - Contact page (basic)
- `pages/directors.html` - Directors page COMPLETE ✅

**Current Features:**
- ✅ Helper functions (formatPrice, formatDate, etc.)
- ✅ Validation utilities (email, phone, required fields)
- ✅ Storage wrapper functions
- ⚠️ About and Contact pages need content

### 🔨 **Your Tasks:**

#### **Task 1: Complete About Page** 📄
**Files:** `pages/about.html`, `css/pages/about.css`

Build a comprehensive About Us page:

**Sections to add:**
- [ ] **Hero Section**
  - Pharmacy name and tagline
  - High-quality hero image
  - "Learn More" CTA button

- [ ] **Our Story**
  - Company history
  - Mission statement
  - Vision statement
  - Core values (4-6 values with icons)

- [ ] **Why Choose Us**
  - 4-6 benefits/features
  - Icons or images
  - Brief descriptions
  - Examples: Fast Delivery, Quality Products, Licensed Pharmacists, 24/7 Support

- [ ] **Statistics Section**
  - Happy customers count
  - Products available
  - Years in business
  - Delivery success rate
  - (Animated counters optional)

- [ ] **Team Section** (Link to directors page)
  - Brief intro to the team
  - "Meet Our Team" button → directors.html

- [ ] **Certifications & Partners**
  - Pharmacy licenses
  - Partner logos
  - Certifications/badges

**Content Example:**
```html
<section class="about-hero">
    <div class="container">
        <h1>About PharmaCare</h1>
        <p class="hero-text">Your trusted online pharmacy delivering quality healthcare products to your doorstep since 2020.</p>
    </div>
</section>

<section class="our-story">
    <div class="container">
        <div class="story-content">
            <h2>Our Story</h2>
            <p>Founded in 2020, PharmaCare began with a simple mission: make healthcare accessible to everyone...</p>
            
            <h3>Our Mission</h3>
            <p>To provide safe, affordable, and convenient access to pharmaceutical products...</p>
            
            <h3>Our Values</h3>
            <div class="values-grid">
                <div class="value-card">
                    <i class="icon-shield"></i>
                    <h4>Trust</h4>
                    <p>We prioritize quality and safety</p>
                </div>
                <!-- More values -->
            </div>
        </div>
    </div>
</section>
```

#### **Task 2: Complete Contact Page** 📧 **PRIORITY**
**Files:** `pages/contact.html`, `css/pages/contact.css`, `js/pages/contact.js` (create)

Build a functional contact page:

**Sections:**
- [ ] **Contact Form**
  - Name (required)
  - Email (required, validated)
  - Phone (optional)
  - Subject (dropdown: General, Order, Support, Complaint)
  - Message (textarea, required)
  - Submit button
  - Form validation

- [ ] **Contact Information**
  - Address
  - Phone numbers
  - Email addresses
  - Business hours
  - Map (Google Maps embed or static image)

- [ ] **FAQ Section** (Optional)
  - 5-10 common questions
  - Accordion/collapsible answers

**Form Implementation:**
```javascript
// js/pages/contact.js
import { showToast } from '../components/toast.js';
import { validateEmail, validateRequired } from '../utils/validation.js';

function initContactPage() {
    setupContactForm();
}

function setupContactForm() {
    const form = document.getElementById('contactForm');
    
    form?.addEventListener('submit', async (e) => {
        e.preventDefault();
        
        const formData = {
            name: form.name.value,
            email: form.email.value,
            phone: form.phone.value,
            subject: form.subject.value,
            message: form.message.value
        };
        
        if (!validateContactForm(formData)) return;
        
        await submitContactForm(formData);
    });
}

function validateContactForm(data) {
    if (!validateRequired(data.name, 'Name')) return false;
    if (!validateEmail(data.email)) return false;
    if (!validateRequired(data.message, 'Message')) return false;
    return true;
}

async function submitContactForm(data) {
    try {
        // Option 1: Save to Supabase (create 'contacts' table)
        const { error } = await window.supabase
            .from('contacts')
            .insert({
                name: data.name,
                email: data.email,
                phone: data.phone,
                subject: data.subject,
                message: data.message,
                status: 'new'
            });
        
        if (error) throw error;
        
        showToast('Message sent successfully! We\'ll respond within 24 hours.', 'success');
        document.getElementById('contactForm').reset();
        
    } catch (error) {
        console.error('Error:', error);
        showToast('Failed to send message. Please try again.', 'error');
    }
}

document.addEventListener('DOMContentLoaded', initContactPage);
```

**Create Supabase table for contacts:**
```sql
create table contacts (
  id uuid default gen_random_uuid() primary key,
  name text not null,
  email text not null,
  phone text,
  subject text not null,
  message text not null,
  status text default 'new',
  created_at timestamp with time zone default timezone('utc'::text, now()) not null
);
```

#### **Task 3: Enhanced Utility Functions**
**Files:** `js/utils/helpers.js`

Add more useful helper functions:

```javascript
// Add to helpers.js

/**
 * Debounce function for search inputs
 */
export function debounce(func, wait) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, args), wait);
    };
}

/**
 * Throttle function for scroll events
 */
export function throttle(func, limit) {
    let inThrottle;
    return function(...args) {
        if (!inThrottle) {
            func.apply(this, args);
            inThrottle = true;
            setTimeout(() => inThrottle = false, limit);
        }
    };
}

/**
 * Copy text to clipboard
 */
export async function copyToClipboard(text) {
    try {
        await navigator.clipboard.writeText(text);
        return true;
    } catch (err) {
        return false;
    }
}

/**
 * Generate random ID
 */
export function generateId(length = 8) {
    return Math.random().toString(36).substring(2, length + 2);
}

/**
 * Truncate text with ellipsis
 */
export function truncateText(text, maxLength) {
    if (text.length <= maxLength) return text;
    return text.substring(0, maxLength) + '...';
}

/**
 * Calculate discount percentage
 */
export function calculateDiscount(originalPrice, salePrice) {
    const discount = ((originalPrice - salePrice) / originalPrice) * 100;
    return Math.round(discount);
}

/**
 * Format phone number
 */
export function formatPhoneNumber(phone) {
    const cleaned = phone.replace(/\D/g, '');
    const match = cleaned.match(/^(\d{3})(\d{3})(\d{4})$/);
    if (match) {
        return '(' + match[1] + ') ' + match[2] + '-' + match[3];
    }
    return phone;
}
```

#### **Task 4: Guest Cart Management**
**Files:** `js/utils/storage.js`, create `js/utils/guestCart.js`

Create utilities for guest cart synchronization:

```javascript
// js/utils/guestCart.js
import { getStorage, setStorage, removeStorage } from './storage.js';
import { CONFIG } from '../config.js';

/**
 * Get guest cart from localStorage
 */
export function getGuestCart() {
    return getStorage(CONFIG.STORAGE_KEYS.CART) || [];
}

/**
 * Add item to guest cart
 */
export function addToGuestCart(productId, quantity = 1) {
    const cart = getGuestCart();
    const existing = cart.find(item => item.productId === productId);
    
    if (existing) {
        existing.quantity += quantity;
    } else {
        cart.push({ productId, quantity, addedAt: Date.now() });
    }
    
    setStorage(CONFIG.STORAGE_KEYS.CART, cart);
    return cart;
}

/**
 * Sync guest cart to user account after login
 */
export async function syncGuestCartToUser(userId) {
    const guestCart = getGuestCart();
    
    if (guestCart.length === 0) return;
    
    try {
        // Upload each item to Supabase cart
        for (const item of guestCart) {
            await window.supabase.from('cart').insert({
                user_id: userId,
                product_id: item.productId,
                quantity: item.quantity
            });
        }
        
        // Clear guest cart
        removeStorage(CONFIG.STORAGE_KEYS.CART);
        console.log('Guest cart synced successfully');
        
    } catch (error) {
        console.error('Error syncing guest cart:', error);
    }
}

/**
 * Clear guest cart
 */
export function clearGuestCart() {
    removeStorage(CONFIG.STORAGE_KEYS.CART);
}
```

#### **Task 5: Additional Static Pages** (Optional)
**Files:** Create new pages as needed

Consider creating:
- [ ] **FAQ Page** (`pages/faq.html`)
  - Frequently asked questions
  - Searchable/filterable
  - Accordion UI

- [ ] **Terms & Conditions** (`pages/terms.html`)
  - Legal terms
  - Privacy policy
  - Return/refund policy

- [ ] **Shipping Info** (`pages/shipping.html`)
  - Delivery areas
  - Shipping rates
  - Estimated delivery times

#### **Task 6: Creative Profile Page** 🎨
**Your Files:** 
- `pages/directors/washington.html`
- `css/directors/washington.css`

**Creative Freedom:** Showcase your utility work:
- Your photo and bio
- Static pages you created
- Utility functions you built
- Content writing skills
- Technical documentation

**Design Ideas:**
- Clean, professional layout
- Document/page themed design
- Utility showcase
- Code snippet examples
- Developer tools aesthetic

### 🗄️ **Your Supabase Tables:**
- **`contacts` table** - CREATE (for contact form submissions)
  - You may need to create this table
- Minimal database interaction (focus on front-end utilities)

### 📚 **Key Files You'll Modify:**
```
pages/about.html              (add content)
pages/contact.html            (add content)
css/pages/about.css           (styling)
css/pages/contact.css         (styling)
js/pages/contact.js           (create - form handling)
js/utils/helpers.js           (add more functions)
js/utils/guestCart.js         (create new)
pages/faq.html                (create - optional)
pages/terms.html              (create - optional)
```

---

## 🎨 **Creative Profile Pages - All Members**

**Every team member must create their personal profile page!**

### **Your Individual Files:**
- `pages/directors/[your-name].html`
- `css/directors/[your-name].css`

### **What to Include:**
1. ✅ **Personal Photo** - Professional or creative
2. ✅ **Name & Title** - Your role in the project
3. ✅ **Bio/About Me** - Who you are, your background
4. ✅ **Skills & Technologies** - What you know (JavaScript, Supabase, CSS, etc.)
5. ✅ **Your Contributions** - What you built for this project
6. ✅ **Social Links** - GitHub, LinkedIn, Twitter, Portfolio
7. ✅ **Contact Info** - Email (optional)
8. ✅ **Achievements/Certifications** - Awards, courses, degrees
9. ✅ **Hobbies/Interests** - Make it personal!

### **Design Freedom:**
- ✨ Choose any design style you like
- ✨ Use animations and interactions
- ✨ Experiment with layouts
- ✨ Add your personality
- ✨ Make it uniquely YOURS!

### **Inspiration Styles:**
- Minimalist & Clean
- Bold & Colorful
- Dark & Mysterious
- Professional Resume
- Creative Portfolio
- Interactive Game
- Animated Showcase

### **Access Your Page:**
Visit `pages/directors.html` and click "View Profile" on your card!

---

## 📚 **General Guidelines for All Team Members**

### **Code Quality:**
- ✅ Write clean, readable code
- ✅ Add comments to explain complex logic
- ✅ Use consistent naming conventions
- ✅ Follow the existing code structure
- ✅ Test your features thoroughly

### **Git Workflow:**
1. Pull latest changes: `git pull origin main`
2. Create your feature branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Test everything works
5. Commit: `git add .` and `git commit -m "Description"`
6. Push: `git push origin feature/your-feature-name`
7. Create Pull Request on GitHub
8. Wait for review from Wachanga

### **Testing Checklist:**
- [ ] Desktop browser (Chrome, Firefox)
- [ ] Mobile responsive (resize window)
- [ ] All buttons work
- [ ] Forms validate correctly
- [ ] Supabase data loads
- [ ] No console errors
- [ ] Images load properly
- [ ] Links work correctly

### **Communication:**
- 📢 Ask questions in the team group
- 📢 Share progress updates
- 📢 Help team members if they're stuck
- 📢 Review each other's code
- 📢 Celebrate wins together!

### **Resources:**
- **Supabase Docs:** https://supabase.com/docs
- **JavaScript MDN:** https://developer.mozilla.org/en-US/docs/Web/JavaScript
- **CSS Tricks:** https://css-tricks.com
- **Project README:** `README.md`
- **Team Assignments:** `TEAM_ASSIGNMENTS.md`

---

## 🏆 **Success Criteria**

### **Individual Success:**
- ✅ Complete all assigned tasks
- ✅ Code is clean and well-documented
- ✅ Features work on mobile and desktop
- ✅ No critical bugs
- ✅ Personal profile page completed
- ✅ Helped team members

### **Team Success:**
- ✅ All features implemented
- ✅ Website is fully functional
- ✅ Professional design throughout
- ✅ Fast performance
- ✅ Deployed to GitHub Pages
- ✅ Ready for real users!

---

## 🎯 **Your Next Steps**

1. **Read this entire document carefully**
2. **Study the "Already Implemented" section for your role**
3. **Open the files mentioned in "Key Files You'll Modify"**
4. **Start with Priority tasks first**
5. **Test frequently as you build**
6. **Create your personal profile page**
7. **Ask for help when needed**
8. **Have fun and be creative!**

---

**Remember:** You're not just building features, you're building your skills and portfolio. Make it something you're proud to show!

**Let's build something amazing together! 🚀**

--- 

*Questions? Contact Wachanga (Project Coordinator) or ask in the team group.*
