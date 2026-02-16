# 📘 Webflow CMS Countdown Timer

Dynamic Offer Countdown Bar (Custom Code)

---

## 📌 Overview

This component creates a **dynamic countdown timer bar** powered by a Webflow CMS Date field.

It displays:

* Days
* Hours
* Minutes
* Seconds

The timer automatically updates every second and shows **“Offer expired”** when the countdown ends.

---

## 🎯 Features

- Fully custom code (no plugins)
- Webflow CMS dynamic date support
- Real-time countdown
- Clean black & gold urgency design
- Lightweight & performance friendly
- Auto-expiry handling

---

## 🖼 Visual Preview

Design Style:

* Black urgency bar
* White heading text
* Gold countdown numbers
* Clean minimal layout
* Responsive flex layout

Layout Preview:

<img width="991" height="80" alt="image" src="https://github.com/user-attachments/assets/cc22f9ea-6ab6-4775-96b3-f57db895b139" />

---

# ⚙️ Installation Guide (Webflow)

### Step 1 — Create CMS Field

In your Collection:

Add a field:

```
Field Type: Date/Time
Field Name: end-time-2
```

Example CMS value:

```
Feb 17, 2026
```

---

### Step 2 — Add Embed Block

Place a **Code Embed** where you want the countdown bar.

Paste the following code:

---

# 💻 Complete Code

```html
<style>
.countdown-bar {
  background:#000;
  color:#fff;
  display:flex;
  justify-content:center;
  align-items:center;
  gap:30px;
  padding:14px 20px;
  font-family:Arial, Helvetica, sans-serif;
}

.countdown-label {
  font-weight:600;
  line-height:1.2;
}

.timer {
  display:flex;
  gap:14px;
  font-weight:700;
}

.time-box {
  text-align:center;
  color:#FFD700;
  min-width:40px;
}

.time-box span {
  font-size:26px;
  display:block;
  line-height:1;
}

.time-box small {
  font-size:11px;
  color:#aaa;
  margin-top:4px;
  display:block;
}
</style>

<div class="countdown-bar">
  <div class="countdown-label">
    Time is running out!<br>
    The offer ends at:
  </div>

  <div 
    class="timer" 
    id="timer"
    data-end="{{wf {&quot;path&quot;:&quot;end-time-2&quot;,&quot;transformers&quot;:[{&quot;name&quot;:&quot;date&quot;,&quot;arguments&quot;:[&quot;MMM DD, YYYY&quot;]\}],&quot;type&quot;:&quot;Date&quot;\} }}">
  </div>
</div>

<script>
const timer = document.getElementById("timer");
const endTime = new Date(timer.dataset.end).getTime();

function updateTimer(){
  const diff = endTime - Date.now();

  if(diff <= 0){
    timer.innerHTML = "Offer expired";
    return;
  }

  const days = Math.floor(diff / 86400000);
  const hours = Math.floor(diff / 3600000) % 24;
  const mins = Math.floor(diff / 60000) % 60;
  const secs = Math.floor(diff / 1000) % 60;

  timer.innerHTML = `
    <div class="time-box">
      <span>${String(days).padStart(2,'0')}</span>
      <small>Days</small>
    </div>
    <div class="time-box">
      <span>${String(hours).padStart(2,'0')}</span>
      <small>Hrs</small>
    </div>
    <div class="time-box">
      <span>${String(mins).padStart(2,'0')}</span>
      <small>Mins</small>
    </div>
    <div class="time-box">
      <span>${String(secs).padStart(2,'0')}</span>
      <small>Sec</small>
    </div>
  `;
}

updateTimer();
setInterval(updateTimer,1000);
</script>
```

---

# 🧠 How It Works

### 1️⃣ CMS Binding

This part pulls the date dynamically:

```html
data-end="{{wf { ... } }}"
```

Webflow injects the CMS date into the `data-end` attribute.

---

### 2️⃣ Date Parsing

```javascript
const endTime = new Date(timer.dataset.end).getTime();
```

The script converts the CMS date into a timestamp.

---

### 3️⃣ Countdown Logic

The script calculates:

```
End Time – Current Time
```

Then extracts:

* Days
* Hours
* Minutes
* Seconds

---

### 4️⃣ Live Updates

```javascript
setInterval(updateTimer,1000);
```

Updates every second automatically.

---

# 🎨 Customization Guide

### Change Gold Color

```css
.time-box {
  color:#FFD700;
}
```

Replace with your brand color.

---

### Increase Timer Size

```css
.time-box span {
  font-size:32px;
}
```

---

### Change Text

Edit this section:

```html
Time is running out!
The offer ends at:
```

---

# ⚠ Troubleshooting

### If it shows "Invalid Date"

✔ Make sure CMS field is Date/Time
✔ Make sure field name matches exactly: `end-time-2`
✔ Publish site after changes

---

### If timer doesn't move

✔ Ensure script is inside Embed
✔ Make sure ID `timer` is not duplicated

---

# 🚀 Performance Notes

* Pure Vanilla JavaScript
* No external libraries
* Very lightweight
* Safe for production

---

# ✅ Final Result

You now have:

✔ Fully dynamic CMS countdown
✔ Professional urgency bar
✔ Auto-expiry handling
✔ Clean responsive layout
