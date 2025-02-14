# NaxoraTech-
All features coded


### **Frontend** 

#### **1️⃣ HTML (Frontend UI – `index.html`)**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nexora Tech AI Marketplace</title>
    <link rel="stylesheet" href="styles.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script defer src="script.js"></script>
</head>
<body>
    <header>
        <h1>Nexora Tech AI Design Packages</h1>
    </header>
    <section class="packages">
        <div class="package">
            <h2>Free Package</h2>
            <p>✅ 1 AI-Generated Logo</p>
            <p>✅ 1 AI-Generated YouTube Thumbnail</p>
            <p>✅ AI Font & Color Suggestions</p>
            <p><strong>Price:</strong> <span class="price" data-inr="₹0" data-usd="$0" data-aed="AED 0"></span></p>
            <a href="#" class="pay-btn free-btn">Get Free</a>
        </div>
        <div class="package">
            <h2>Pro AI Package</h2>
            <p>✅ 3 AI-Generated Logo Concepts</p>
            <p>✅ Unlimited AI YouTube Thumbnails</p>
            <p>✅ AI-Generated Product Packaging Design</p>
            <p>✅ AI Social Media Kit</p>
            <p><strong>Price:</strong> <span class="price" data-inr="₹2,499" data-usd="$30" data-aed="AED 110"></span></p>
            <a href="#" class="pay-btn pro-btn">Buy Now</a>
        </div>
        <div class="package">
            <h2>Ultra AI Branding</h2>
            <p>✅ 10 AI-Generated Logo Concepts</p>
            <p>✅ Unlimited AI Thumbnails + Optimization</p>
            <p>✅ AI Product Branding (Labels, Packaging, Merchandise)</p>
            <p>✅ AI Website UI/UX Design</p>
            <p><strong>Price:</strong> <span class="price" data-inr="₹4,999" data-usd="$75" data-aed="AED 275"></span></p>
            <a href="#" class="pay-btn ultra-btn">Buy Now</a>
        </div>
    </section>
</body>
</html>
``` 

#### **2️⃣ JavaScript (Dynamic Pricing & Payment Links – `script.js`)**
```javascript
$(document).ready(function () {
    // Fetch user's location & set currency dynamically
    $.getJSON("https://ipapi.co/json/", function (data) {
        let country = data.country_code;
        let currency = "INR"; // Default currency
        let paymentLinks = {
            "INR": {
                "free": "https://rzp.io/rzp/WARUoKZM",
                "pro": "https://rzp.io/rzp/WARUoKZM",
                "ultra": "https://rzp.io/rzp/U0AuyYTj"
            },
            "USD": {
                "free": "https://rzp.io/rzp/WARUoKZM",
                "pro": "https://rzp.io/rzp/pBgOQ7pK",
                "ultra": "https://rzp.io/rzp/S6axeG3"
            },
            "AED": {
                "free": "https://rzp.io/rzp/WARUoKZM",
                "pro": "https://rzp.io/rzp/ByAnY0LK",
                "ultra": "https://rzp.io/rzp/zi2q0RY"
            }
        };
        if (["US"].includes(country)) {
            currency = "USD";
        } else if (["AE"].includes(country)) {
            currency = "AED";
        }
        $(".price").each(function () {
            $(this).text($(this).data(currency.toLowerCase()));
        });
        $(".free-btn").attr("href", paymentLinks[currency]["free"]);
        $(".pro-btn").attr("href", paymentLinks[currency]["pro"]);
        $(".ultra-btn").attr("href", paymentLinks[currency]["ultra"]);
    });
});
``` 

#### **3️⃣ CSS (Styling – `styles.css`)**
```css
body {
    font-family: Arial, sans-serif;
    background-color: #121212;
    color: white;
    text-align: center;
    padding: 20px;
}
header {
    margin-bottom: 20px;
}
.packages {
    display: flex;
    justify-content: center;
    gap: 20px;
}
.package {
    background: #1e1e1e;
    padding: 20px;
    border-radius: 10px;
    width: 300px;
    text-align: left;
}
.package h2 {
    color: #ff9800;
}
.pay-btn {
    display: block;
    text-align: center;
    padding: 10px;
    background: #ff9800;
    color: white;
    border-radius: 5px;
    margin-top: 10px;
    text-decoration: none;
}
.pay-btn:hover {
    background: #e68900
