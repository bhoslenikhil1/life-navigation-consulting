# Razorpay Integration Setup Guide

## ⚡ Quick Reference

Your Razorpay Test Credentials:
- **Key ID**: `rzp_test_T1PHUBUH5uxwjT`
- **Key Secret**: `T0wFuWPqL2W76IFIPtCaeMwZ` (NEVER share this publicly)

## 🎯 What's Already Integrated

### Masterclass Payment (Rs.99)
- Location: `masterclass.html`
- Amount: 9,900 paise
- Payment Link: Razorpay Checkout Modal
- Success Action: Redirect to WhatsApp

### Personal Call Payment (Rs.399)
- Location: `call.html`
- Amount: 39,900 paise
- Payment Link: Razorpay Checkout Modal
- Success Action: Redirect to WhatsApp with Payment ID

## 🔧 Implementation Details

### Current Implementation: Razorpay Checkout Modal
This is the simplest & recommended approach that requires NO BACKEND.

**How it works:**
1. User clicks "Pay Now"
2. Razorpay modal loads
3. User enters payment details
4. Razorpay processes payment
5. On success: Redirect to WhatsApp
6. On failure: Error message shown

### Code Location in Files

**In `masterclass.html` and `call.html`:**

```javascript
function initiatePayment() {
    var options = {
        "key": "rzp_test_T1PHUBUH5uxwjT",        // ← Your Key ID
        "amount": 9900,                          // Amount in paise
        "currency": "INR",
        "name": "Speak & Settle",
        "description": "Live Masterclass...",
        "handler": function(response) {
            // This runs when payment succeeds
            alert("Payment successful!");
            // Redirect to WhatsApp
        }
    };
    var rzp = new Razorpay(options);
    rzp.open();
}
```

## 📋 Step-by-Step Setup

### Step 1: Get Your Razorpay Account
1. Go to https://dashboard.razorpay.com
2. Sign up or login
3. Verify your email

### Step 2: Find Your Keys
1. Click **Settings** (bottom left)
2. Go to **API Keys**
3. You'll see:
   - **Key ID** (public, safe to share in code)
   - **Key Secret** (private, NEVER share!)

**Test Mode:**
- Used for testing
- No real money charged
- Payments marked as "test"

**Live Mode:**
- Real payments
- Money goes to your account
- Need to activate account fully

### Step 3: Testing with Test Credentials

#### Test Card Details:
```
Card Number: 4111 1111 1111 1111
Expiry: Any future date (e.g., 12/25)
CVV: 123
Name: Test
Email: test@example.com
Phone: 9999999999
```

#### How to Test:
1. Go to `masterclass.html` or `call.html`
2. Click "Book Now" button
3. Razorpay modal opens
4. Enter test card details
5. Click Pay
6. You'll see success message
7. Check Razorpay dashboard for transaction

### Step 4: Switch to Live Mode (Production)

**Prerequisites:**
- Complete your KYC (Know Your Customer) on Razorpay
- Add your bank account for payouts
- Enable live mode

**Steps:**
1. Go to Razorpay Dashboard
2. Click **Toggle Test/Live** (top right)
3. Switch to **LIVE**
4. Copy your **Live Key ID**
5. Update in both HTML files:

```javascript
"key": "rzp_live_XXXXXXXXXXXXX", // Your LIVE key
```

**Important:** NEVER put the Key Secret in your code!

## 🛡️ Security Best Practices

### ✅ Safe to Put in Code:
- Key ID (public)
- Amount
- Description
- Customer email/phone

### ❌ NEVER Put in Code:
- Key Secret
- Passwords
- Private tokens
- Account credentials

### Why This Is Safe:
- Razorpay handles all payment security
- Your site never touches credit card data
- PCI-DSS compliant
- HTTPS encrypted

## 📊 Payment Flow Diagram

```
User Clicks "Pay Now"
         ↓
JavaScript triggers payment() function
         ↓
Razorpay Checkout Modal Opens
         ↓
User Enters Card Details
         ↓
User Clicks "Pay" → Razorpay Processes
         ↓
     ↙─────────────┐
    ↙              ↘
SUCCESS            FAILURE
  ↓                 ↓
Redirect to      Show Error
WhatsApp         Message
```

## 🔍 Verify Integration in Code

### In `masterclass.html`:
Line ~200:
```javascript
var options = {
    "key": "rzp_test_T1PHUBUH5uxwjT",
    "amount": 9900,  // Rs.99
```

### In `call.html`:
Line ~200:
```javascript
var options = {
    "key": "rzp_test_T1PHUBUH5uxwjT",
    "amount": 39900,  // Rs.399
```

## 📈 After Payment Success

### What User Sees:
1. "Payment successful! Transaction ID: rpy_xxxxx" alert
2. Redirects to WhatsApp pre-filled with:
   - Your number: `918591201967`
   - Message includes payment ID
   - Pre-written confirmation text

### What You Receive:
1. WhatsApp message from customer with Payment ID
2. Razorpay dashboard shows the transaction
3. Money goes to your bank account

### How to Verify in Razorpay:
1. Go to Razorpay Dashboard
2. Click **Payments**
3. See all transactions with:
   - Payment ID
   - Amount
   - Status (Captured/Failed)
   - Customer details
   - Timestamp

## 💰 Payout Settings

### Setup Payouts:
1. Go to **Settings > Account Settings**
2. Add your **Bank Account**
3. Verify bank details (takes 2-3 days)
4. Set payout schedule (automatic or manual)

### Payout Schedule Options:
- **Daily**: Money every day
- **Weekly**: Money every Monday
- **Monthly**: Money on 1st of month
- **Manual**: You request payouts

## 🚨 Common Issues & Fixes

### Issue 1: Modal Doesn't Open
**Solution:**
```html
<!-- Make sure this is in your HTML head -->
<script src="https://checkout.razorpay.com/v1/checkout.js"></script>
```

### Issue 2: "Key Error" Message
**Solution:**
- Check your Key ID is correct
- Make sure you copied it fully
- Test in test mode first

### Issue 3: Payment Shows as Test in Dashboard
**This is normal in Test Mode!**
- Switch to Live mode to process real payments
- Real mode will show actual amounts

### Issue 4: WhatsApp Redirect Doesn't Work
**Solution:**
- Check WhatsApp number is correct: `918591201967`
- Use format: country code (91) + number without +
- Test on mobile device (desktop won't have WhatsApp)

## 📞 Razorpay Support

- **Documentation**: https://razorpay.com/docs/
- **Dashboard**: https://dashboard.razorpay.com/
- **Support Email**: support@razorpay.com
- **Chat Support**: In dashboard (click help icon)

## ✅ Go-Live Checklist

- [ ] Have Razorpay account (Free)
- [ ] Have Live Key ID (from Settings > API Keys)
- [ ] Replaced test key with live key in both files
- [ ] Bank account added to Razorpay
- [ ] KYC verification complete
- [ ] Test payment processed
- [ ] WhatsApp redirects working
- [ ] All links verified
- [ ] Uploaded to GitHub
- [ ] GitHub Pages enabled

## 🎉 You're Ready!

Once you've completed the checklist above:
1. Upload latest files to GitHub
2. Test with live card (real payment)
3. Check WhatsApp receives message
4. Verify money in Razorpay dashboard
5. Start accepting payments! 🚀

---

**Questions?** Check Razorpay docs or contact their support.
**Need Backend Later?** We can add order verification for additional security.
