# 🌐 Hosting a Static Website Using Amazon S3

Amazon S3 (Simple Storage Service) can be used to host static websites — websites that include HTML, CSS, JavaScript, and images without any server-side scripting (like PHP, Node.js, etc.).

---

## 🧩 Prerequisites

Before starting, make sure you have:
- An **AWS account**
- A **domain name** (optional)
- Basic knowledge of **HTML/CSS/JS**

---

## 🚀 Step 1: Create an S3 Bucket

1. Log in to your **AWS Management Console**.
2. Open the **S3** service.
3. Click **Create bucket**.
4. Enter a **unique bucket name** (e.g., `my-website-bucket`).
5. Choose a **region**.
6. Uncheck **Block all public access** (to make the website publicly available).
7. Acknowledge the warning and click **Create bucket**.

---

## 🧾 Step 2: Upload Your Website Files

1. Open your newly created bucket.
2. Click **Upload**.
3. Add all your website files (HTML, CSS, JS, and images).
4. Click **Upload** to finish.

---

## ⚙️ Step 3: Configure Bucket for Static Website Hosting

1. Go to the **Properties** tab of your bucket.
2. Scroll down to **Static website hosting**.
3. Click **Edit** → Enable **Static website hosting**.
4. Select **Host a static website**.
5. Enter:
   - **Index document:** `index.html`
   - **Error document:** `error.html` (optional)
6. Click **Save changes**.
7. Copy the **Bucket website endpoint URL** (you’ll use this to access your website).

---

## 🔒 Step 4: Set Bucket Policy for Public Access

To make your website files public:

1. Open the **Permissions** tab.
2. Click **Bucket Policy** → **Edit**.
3. Paste the following JSON (replace `your-bucket-name` with your actual bucket name):

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

4. Click **Save changes**.

---

## 🌍 Step 5: Access Your Website

- Open the **Bucket website endpoint** link.
- Example:
  ```
  http://your-bucket-name.s3-website-us-east-1.amazonaws.com
  ```
- You should see your homepage load!

---

## 🌐 (Optional) Step 6: Connect a Custom Domain

To use your own domain:

1. Go to **Amazon Route 53** or your domain registrar.
2. Create a **CNAME record** that points your domain (e.g., `www.example.com`) to your **S3 website endpoint**.
3. Wait for DNS propagation (can take up to 24 hours).

---

## 🧹 Step 7: Clean Up (Optional)

If you no longer need the website:
1. Delete all objects inside the S3 bucket.
2. Then delete the bucket itself.

---

## ✅ Summary

| Step | Task | Description |
|------|------|-------------|
| 1 | Create S3 bucket | Set up storage for your site |
| 2 | Upload files | Add HTML, CSS, JS |
| 3 | Enable hosting | Turn on static website hosting |
| 4 | Set policy | Allow public access |
| 5 | Test site | Use endpoint URL |
| 6 | (Optional) Custom domain | Map domain via Route 53 |

---

## 💡 Tips

- Make sure filenames are **case-sensitive** (e.g., `Index.html` ≠ `index.html`).
- Always test using **Incognito mode** to avoid cached results.
- Use **AWS CloudFront** for faster content delivery (CDN).

---

### 🧰 Example Project Structure
```
my-website/
│
├── index.html
├── about.html
├── styles/
│   └── style.css
├── scripts/
│   └── main.js
└── images/
    └── logo.png
```

---

**Author:** Your Name  
**Date:** October 2025  
**License:** MIT

---

> 🎯 *Now your static website is live using Amazon S3!*
