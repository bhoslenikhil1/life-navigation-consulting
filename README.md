# Speak & Settle — Multi-Page Website Setup

This is a complete restructure of your website into separate pages for Masterclass (Rs.99) and Personal Call (Rs.399) with integrated Razorpay payment processing.

## 📁 Files Included

1. **index.html** — Home page with navigation to both services
2. **masterclass.html** — Live Masterclass booking page (Rs.99)
3. **call.html** — Personal Voice Call booking page (Rs.399)
4. **README.md** — This file

## 🚀 Quick Start

### Step 1: Upload Files to GitHub
1. Go to your GitHub repository
2. Create a folder named `src` or `web` (optional)
3. Upload all three HTML files
4. Enable **GitHub Pages** in repository settings (Settings > Pages > Source: Main branch)

Your site will be live at: `https://yourusername.github.io/repositoryname/`

### Step 2: Update Razorpay Credentials
In both **masterclass.html** and **call.html**, find this line and replace with your actual key:

```javascript
"key": "rzp_test_T1PHUBUH5uxwjT", // ← Replace this
```

**To get your Razorpay key:**
1. Go to [Razorpay Dashboard](https://dashboard.razorpay.com/)
2. Login with your account
3. Go to **Settings > API Keys**
4. Copy your **Key ID** (Test mode for testing, Live for production)

### Step 3: Update Logo URL (Optional)
In both payment pages, update:
```javascript
"image": "https://via.placeholder.com/100", // Replace with your logo URL
```

### Step 4: Test Payments
Use Razorpay test credentials:
- Card: `4111 1111 1111 1111`
- Expiry: Any future date
- CVV: `123`

## 📱 Page Structure

### index.html (Home)
- Navigation with links to both services
- Two service cards with pricing
- Free WhatsApp chat option
- Responsive design

### masterclass.html (Masterclass)
- Service details and benefits
- Feature highlights
- Razorpay payment integration (Rs.99)
- WhatsApp Q&A button
- Back button to home

### call.html (Personal Call)
- Service details and how it works
- Available time slots
- Feature list
- Razorpay payment integration (Rs.399)
- WhatsApp booking button
- Back button to home

## 🔐 Razorpay Integration Details

### Masterclass (Rs.99)
- **Amount**: 9,900 paise (Rs.99)
- **Description**: Live Masterclass - Overcoming Rejection in Love
- **Redirect**: WhatsApp confirmation after payment

### Personal Call (Rs.399)
- **Amount**: 39,900 paise (Rs.399)
- **Description**: 20-Min Personalized Voice Call - Counselling
- **Redirect**: WhatsApp with payment ID for slot confirmation

### Payment Flow
1. User clicks "Pay Now" button
2. Razorpay modal opens
3. User enters payment details
4. On success → User is redirected to WhatsApp with payment confirmation
5. On cancel → Error message shown

## 📋 Customization Guide

### Change WhatsApp Number
Find this in all files:
```
918591201967
```
Replace with your WhatsApp number (without +91)

### Change Prices
- **Masterclass**: Find `9900` (line with amount)
- **Personal Call**: Find `39900` (line with amount)

### Add Your Logo
1. Upload logo to any hosting (Imgur, Cloudinary, etc.)
2. Replace `image` URL in payment options

### Update Service Details
Edit the HTML content in each page's sections to match your services

## 🔗 Navigation Links
All pages are linked together:
- Home → Masterclass
- Home → Personal Call
- Masterclass → Home
- Personal Call → Home
- Free Chat → WhatsApp (all pages)

## ✅ Testing Checklist

- [ ] All three files uploaded to GitHub
- [ ] GitHub Pages enabled
- [ ] Can navigate between pages
- [ ] Payment buttons open Razorpay modal
- [ ] WhatsApp links work correctly
- [ ] Responsive on mobile
- [ ] Back buttons work

## 🛠️ Deployment to Production

### Step 1: Live Razorpay Keys
1. Login to [Razorpay Dashboard](https://dashboard.razorpay.com/)
2. Switch from **Test** to **Live** mode
3. Get your **Live Key ID**
4. Update both HTML files with Live key

### Step 2: Update Domain (if using custom domain)
- Go to GitHub repo Settings > Pages
- Add your custom domain
- Update DNS records with GitHub's IP addresses

### Step 3: HTTPS
- GitHub Pages automatically provides HTTPS
- Your domain will be `https://yourdomain.com`

## 🐛 Troubleshooting

### Payment Modal Not Opening
- Verify Razorpay script is loaded: `<script src="https://checkout.razorpay.com/v1/checkout.js"></script>`
- Check browser console for errors
- Ensure JavaScript is enabled

### WhatsApp Links Not Working
- Verify WhatsApp number format (10 digits without +91)
- Check if WhatsApp is installed on the device

### Pages Not Loading
- Check GitHub Pages settings
- Verify file names are exactly: `index.html`, `masterclass.html`, `call.html`
- Clear browser cache

## 📞 Support

For Razorpay issues: https://razorpay.com/support/
For GitHub Pages issues: https://docs.github.com/en/pages

## 💡 Next Steps

1. ✅ Upload files to GitHub
2. ✅ Enable GitHub Pages
3. ✅ Update Razorpay credentials
4. ✅ Test payment flow
5. ✅ Go live with production keys

---

**Created**: 2025
**Last Updated**: June 2025
**Status**: Ready for Production
