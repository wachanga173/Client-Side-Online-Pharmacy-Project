# Director Profile Pages - Build Guide

## Overview
Each of the 10 directors now has their own personal HTML page and CSS file to customize. You have complete freedom to design and script your own profile page!

## Your Files

### 1. **I.N.N.O.C.E.N.T** (Dev-Felix001)
- HTML: `pages/directors/innocent.html`
- CSS: `css/directors/innocent.css`
- Role: Director of Authentication & User Management

### 2. **Isabell Wanjiku** (Isabel53)
- HTML: `pages/directors/isabell.html`
- CSS: `css/directors/isabell.css`
- Role: Director of Product Catalog & Display

### 3. **OBUYA ODUOR HEZEKIAH** (OBUYA123)
- HTML: `pages/directors/obuya.html`
- CSS: `css/directors/obuya.css`
- Role: Director of Shopping Cart Systems

### 4. **Samuel** (Samuel0096)
- HTML: `pages/directors/samuel.html`
- CSS: `css/directors/samuel.css`
- Role: Director of Checkout & Payment Integration

### 5. **AdongoSharine Mulindi** (shar979)
- HTML: `pages/directors/sharine.html`
- CSS: `css/directors/sharine.css`
- Role: Director of Admin Panel & Dashboard

### 6. **Techwizbiz**
- HTML: `pages/directors/techwizbiz.html`
- CSS: `css/directors/techwizbiz.css`
- Role: Director of UI Components & Reusable Modules

### 7. **Titus** (titus06ondeu)
- HTML: `pages/directors/titus.html`
- CSS: `css/directors/titus.css`
- Role: Director of Design & Supabase Integration

### 8. **Vikitar**
- HTML: `pages/directors/vikitar.html`
- CSS: `css/directors/vikitar.css`
- Role: Director of Product Details & Search

### 9. **Washington Dave** (washington-dave-dc)
- HTML: `pages/directors/washington.html`
- CSS: `css/directors/washington.css`
- Role: Director of Static Pages & Utilities

### 10. **Wachanga** (wachanga173)
- HTML: `pages/directors/wachanga.html`
- CSS: `css/directors/wachanga.css`
- Role: Chief Executive Officer & Project Coordinator

## What's Included

Each blank template page comes with:
- ✅ Header and Footer (automatically loaded)
- ✅ Basic HTML structure
- ✅ Link to your personal CSS file
- ✅ Supabase client loaded
- ✅ Toast notification system
- ✅ Your name and title
- ✅ A `.director-content` div ready for your custom content

## How to Build Your Page

### Step 1: Edit Your HTML
Open your HTML file (`pages/directors/[yourname].html`) and add content inside the `.director-content` div:

```html
<div class="director-content">
    <!-- Add your content here -->
    <section class="about-me">
        <h2>About Me</h2>
        <p>Your bio here...</p>
    </section>
    
    <section class="skills">
        <h2>Skills</h2>
        <ul>
            <li>JavaScript</li>
            <li>Supabase</li>
        </ul>
    </section>
    
    <section class="projects">
        <h2>My Work</h2>
        <!-- Your projects -->
    </section>
</div>
```

### Step 2: Style Your Page
Open your CSS file (`css/directors/[yourname].css`) and add custom styles:

```css
/* Your custom styles */
.about-me {
    background: var(--light-bg);
    padding: 2rem;
    border-radius: 8px;
    margin-bottom: 2rem;
}

.skills ul {
    display: flex;
    gap: 1rem;
    list-style: none;
}

.skills li {
    background: var(--primary-color);
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 20px;
}
```

### Step 3: Add JavaScript (Optional)
You can add custom JavaScript in your HTML file:

```javascript
<script type="module">
    import { initHeader } from '../js/components/header.js';
    import { initFooter } from '../js/components/footer.js';
    
    document.addEventListener('DOMContentLoaded', () => {
        initHeader();
        initFooter();
        
        // Your custom JavaScript here
        console.log('My profile loaded!');
    });
</script>
```

## Design Ideas

### Option 1: Professional Portfolio
- Hero section with large profile photo
- Skills section with badges
- Projects carousel
- Contact form
- Social media links

### Option 2: Creative Showcase
- Animated background
- Interactive elements
- Timeline of achievements
- Photo gallery
- Custom animations

### Option 3: Minimalist Design
- Clean typography
- Simple color scheme
- Focus on content
- Smooth scrolling sections

### Option 4: Developer Dashboard
- GitHub stats integration
- Code snippets showcase
- Blog posts
- Tech stack icons

## Available Resources

### CSS Variables (from style.css)
```css
--primary-color: #3498db;
--secondary-color: #2ecc71;
--danger-color: #e74c3c;
--warning-color: #f39c12;
--dark-color: #2c3e50;
--light-bg: #ecf0f1;
```

### Utility Classes
- `.container` - max-width content wrapper
- `.btn`, `.btn-primary`, `.btn-secondary` - button styles
- `.card` - card container
- `.grid` - CSS grid layouts

### Components Available
- Header (auto-loaded)
- Footer (auto-loaded)
- Toast notifications: `import { showToast } from '../js/components/toast.js';`
- Modal: `import { showModal } from '../js/components/modal.js';`

## Examples to Include

Consider adding:
- 📷 Profile photo
- 📝 Personal bio
- 💼 Your role and responsibilities
- 🎓 Education & certifications
- 🏆 Achievements
- 💻 Technical skills
- 🔗 Social links (GitHub, LinkedIn, Twitter)
- 📧 Contact information
- 📊 Project contributions
- ⭐ Testimonials

## Testing Your Page

1. Open your HTML file in a browser
2. Check responsiveness (resize window)
3. Test on mobile devices
4. Verify header/footer load correctly
5. Check console for errors

## Access Your Page

Your profile is linked from the Directors page:
- Navigate to: `pages/directors.html`
- Click "View Profile" on your director card
- It will open your custom page!

## Need Help?

- Review existing pages for inspiration
- Check `css/style.css` for global styles
- Ask team members for help
- Refer to project documentation

---

**Have fun building your profile! Show off your creativity and skills! 🚀**
