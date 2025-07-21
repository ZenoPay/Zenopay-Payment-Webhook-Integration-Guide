
# 🔔 Zenopay Payment Webhook Integration Guide

Zenopay allows you to receive real-time payment notifications from Zenopay users via webhooks. This guide explains how to register your webhook and process the payment data securely.

---

## ✅ Step 1: Register Your Webhook

To receive payment notifications, you must first register your webhook with Zenopay.

### 📩 How to Register

Send an email to:  
📧 **[support@zenopay.net](mailto:support@zenopay.net)**

Include:
- Your **Business or App Name**
- Your **Zenopay Account ID** (e.g., `zp092443`)
- Your **Webhook URL** (e.g., `https://yourdomain.com/webhook/zenopay`)

---

## 📥 Sample Webhook Payload

When a payment is made to your account, Zenopay will send a `POST` request to your webhook URL with the following JSON:

```json
{
  "status": "SUCCESS",
  "resultCode": "000",
  "message": "Webhook delivered successfully.",
  "data": {
    "account_id": "zp092443",
    "phone_number": "255652449389",
    "channel": "ZENOPAY",
    "amount": 150000,
    "currency": "TZS",
    "order_id": "ORDER_67890",
    "payment_status": "COMPLETED",
    "timestamp": "2025-07-21T15:00:00+0300",
    "notes": "Payment for invoice #INV-1001 from Zenopay user"
  }
}
