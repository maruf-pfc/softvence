# 📘 Infinite Marquee Slider (Webflow – Custom Code)

A fully custom, lightweight infinite scrolling announcement bar built using **GSAP CDN + pure HTML/CSS**.

Smooth, seamless, gap-free, and pauses on hover — perfect for conversion-focused landing pages.

---

## 📸 Preview (Screenshot)

<img width="2834" height="1628" alt="image" src="https://github.com/user-attachments/assets/01cfe2e3-8e1b-4fa4-aeee-7b9ba5565f07" />


---

## 🚀 Features

* Seamless infinite scrolling (no gaps ever)
* Pause animation on hover
* Fully custom code (no Webflow slider)
* Mobile smooth (GPU accelerated)
* Lightweight GSAP CDN
* Easy to customize speed, colors & content

---

## 🧩 Tech Used

* HTML5
* CSS3
* GSAP Animation Library (CDN)

---

## 📄 Full Implementation Code

Paste inside a **Webflow Embed element**:

```html
<!-- GSAP CDN -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>

<style>
.marquee {
  background: #000;
  color: #fff;
  overflow: hidden;
  padding: 12px 0;
  position: relative;
}

.marquee-track {
  display: flex;
  align-items: center;
  width: max-content;
  gap: 24px;
}

.marquee-item {
  font-size: 14px;
  display: flex;
  align-items: center;
  gap: 6px;
  white-space: nowrap;
}

.divider {
  width: 1px;
  height: 16px;
  background: #444;
}

.badge {
  background: #e53935;
  padding: 4px 8px;
  border-radius: 6px;
  font-weight: 700;
  margin-left: 6px;
}

.dot {
  width: 6px;
  height: 6px;
  background: #ff3b3b;
  border-radius: 50%;
}

/* Highlight colors */
.stars {
  color: #FFD700;
}

.highlight {
  color: #FFD700;
  font-weight: 700;
}
</style>

<div class="marquee">
  <div class="marquee-track" id="track">

    <div class="marquee-item">
      <span class="dot"></span>
      <span class="highlight">10,781</span> happy customers
    </div>

    <div class="divider"></div>

    <div class="marquee-item">
      <strong>Best Vendors In The Game</strong>
    </div>

    <div class="divider"></div>

    <div class="marquee-item">
      Rated 4.98/5 <span class="stars">★★★★★</span>
    </div>

    <div class="divider"></div>

    <div class="marquee-item">
      <span class="dot"></span>
      <strong>81</strong> live viewers
    </div>

    <div class="divider"></div>

    <div class="marquee-item">
      Price increasing in
      <span class="badge">29:35</span>
    </div>

  </div>
</div>

<script>
const track = document.getElementById("track");
const marquee = document.querySelector(".marquee");

// Duplicate content until it covers screen width twice
function fillTrack() {
  const content = track.innerHTML;
  while (track.scrollWidth < marquee.offsetWidth * 2) {
    track.innerHTML += content;
  }
}

fillTrack();

// Seamless infinite animation
const cycleWidth = track.scrollWidth / 2;

const tween = gsap.to(track, {
  x: -cycleWidth,
  duration: 18,
  ease: "linear",
  repeat: -1
});

// Pause on hover
marquee.addEventListener("mouseenter", () => tween.pause());
marquee.addEventListener("mouseleave", () => tween.play());
</script>
```

---

## ⚙️ How It Works (Simple Explanation)

1. The content row is duplicated repeatedly until it fills more than twice the screen width
2. GSAP animates the row horizontally by exactly one content cycle
3. When the first copy leaves the screen, the next is already visible — creating a seamless loop
4. Hover pauses the animation
5. Leaving hover resumes smoothly

👉 Result: continuous scrolling with zero gaps.

---

## 🎛 Customization

### 🔥 Speed

```js
duration: 18
```

| Value | Effect               |
| ----- | -------------------- |
| 10    | Fast                 |
| 15    | Medium               |
| 18    | Smooth (recommended) |
| 25    | Slow                 |

---

### 🎨 Change Colors

Stars:

```css
.stars { color: #FFD700; }
```

Customer number:

```css
.highlight { color: #FFD700; }
```

Background:

```css
.marquee { background: #000; }
```

---

### 📝 Edit Text

Just modify inside:

```html
<div class="marquee-item">...</div>
```

---

## 📥 How to Use in Webflow

1. Drag **Embed element** onto page
2. Paste full code
3. Publish
4. Done ✅

(No extra setup required)

---

## ✅ Best For

* Announcement bars
* Social proof sliders
* Live stats
* Converting landing pages
* SaaS & ecommerce sites

Just say — happy to help!
