---
title: "How to Set Up Burp Suite with Firefox and FoxyProxy"
date: 2025-07-29
draft: false
tags: ["burp suite", "proxy", "pentesting", "firefox", "foxyproxy"]
categories: ["Security", "How-To"]
description: "Quick guide to setting up Burp Suite with Firefox using FoxyProxy for intercepting HTTP/HTTPS traffic."
---

# Yo, what are you up to today?

I’ve never really written a blog post before — especially not a tech one. But hey, let’s give it a shot. Maybe it’ll help someone.

## What is Burp Suite?

[Burp Suite](https://portswigger.net/burp) is a powerful proxy tool that sits between your browser and the web server. It allows you to intercept, inspect, and modify traffic — and it comes with **tons** of cool features.

Let’s set it up and get you started.

---

## 🛠️ Configuration

After downloading Burp Suite, you’ll need to set up your browser to work with it.  
We’ll use Firefox + [FoxyProxy](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/), a browser extension that lets you easily switch between proxy settings.

### Step-by-step setup:

1. Install **FoxyProxy Standard** from the link above.
2. Pin the extension to your toolbar if you want quick access.
3. Click the FoxyProxy icon → **Options** → **Proxies** → **Add New Proxy**.
4. Name it something like `Burp`.
5. Set **Proxy IP** to `127.0.0.1` and **Port** to `8080`.
6. Save the proxy settings.

Now in Firefox:
- Click the FoxyProxy icon.
- Select the profile you just created (`Burp` in my case).

Now your Firefox traffic goes through Burp Suite. ✅

---

## 🕵️ Intercepting Requests

1. Open **Burp Suite**.
2. Go to the **Proxy** tab → **Intercept** → Make sure it's set to *on*.
3. Visit any website in Firefox.

You should now see the HTTP(S) requests appearing in Burp — including methods, URLs, headers, etc.  
Pretty cool, right?

---

## 🎯 Scope

Setting a **scope** helps Burp filter traffic to only the domains you care about.

To do that:

- Right-click on any request in the **Proxy** tab.
- Choose **Add to Scope**.

Now, only requests to that domain will be shown in Burp tools like **Target**, **Proxy**, and **Logger**.  
No more noise from background traffic to other sites.

---

## 🔐 SSL Certificate (for HTTPS)

To properly intercept HTTPS traffic, you’ll need to install Burp’s SSL certificate in Firefox.

### Steps:

1. In Firefox, go to `http://burp`.
2. Download the **CA Certificate**.
3. Go to **Firefox Settings** → **Privacy & Security**.
4. Scroll to **Certificates** → click **View Certificates**.
5. Go to the **Authorities** tab.
6. Click **Import** and choose the downloaded certificate.
7. Check **“Trust this CA to identify websites”**.
8. Done.

Now you can inspect **HTTPS** traffic — even for sites like Google. 🤓

---

That’s it for today. Let me know if this helped, or if you want a part two.

**Peace! ✌️**

