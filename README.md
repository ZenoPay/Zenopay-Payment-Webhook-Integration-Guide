

# 🔁 Zenopay to Zenopay Payment Webhook Integration Guide

This guide explains how to receive **real-time notifications** when another Zenopay user sends a payment to your Zenopay account. These internal transfers (from Zenopay to Zenopay) are useful for peer-to-peer (P2P), wallet top-ups, float transfers, or merchant payments within the Zenopay ecosystem.

---

## ✅ Step 1: Register Your Webhook

To start receiving webhooks for Zenopay-to-Zenopay payments, you must register your webhook URL with the Zenopay team.

### 📩 How to Register

Send an email to:  
📧 **[support@zenopay.net](mailto:support@zenopay.net)**

Include:
- Your **Business or App Name**
- Your **Zenopay Account ID** (e.g., `zp092443`)
- Your **Webhook URL** (e.g., `https://yourdomain.com/webhook/zenopay`)

Once registered, Zenopay will notify your endpoint on every successful internal transfer to your account.

---

## 📥 Sample Webhook Payload

When another Zenopay user sends money to your account, you'll receive the following `POST` request at your webhook URL:

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
    "notes": "Transfer from another Zenopay user"
  }
}
````

---

## 🧾 Field Description

| Field            | Description                                      |
| ---------------- | ------------------------------------------------ |
| `account_id`     | Your Zenopay account ID (receiver)               |
| `phone_number`   | Sender's phone number                            |
| `channel`        | Payment method — will always be `ZENOPAY`        |
| `amount`         | Amount transferred                               |
| `currency`       | Transaction currency (e.g., `TZS`)               |
| `order_id`       | Internal reference for the transfer              |
| `payment_status` | Transaction status (`COMPLETED`, `FAILED`, etc.) |
| `timestamp`      | Time of the transaction (ISO 8601 format)        |
| `notes`          | Additional notes or reason for transfer (if any) |

---

## 🛡️ Security Best Practices

* Validate requests by checking source IPs or requesting HMAC signing.
* Store your API key securely — **never expose it publicly.**
* Always respond with HTTP `200 OK` to avoid retry delays.

---

## 🔁 Retry Policy

Zenopay will retry your webhook up to **3 times** if it doesn’t receive an HTTP `200 OK` response, with exponential backoff between attempts.

---

## 👨‍💻 Use Cases

* Merchant payments from Zenopay users
* Peer-to-peer wallet transfers
* Internal business wallet top-ups
* Float or reseller funding notifications

---

## 📬 Need Help?

Contact us at:
📧 **[support@zenopay.net](mailto:support@zenopay.net)**
We'll help you test, debug, or verify webhook delivery.

---

*© Zenopay — Smart Payments Within the Network*

```

---
