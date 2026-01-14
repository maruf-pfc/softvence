# One-Page Table Print (Webflow Tabs + CMS)

This script allows you to **print a Webflow CMS table as a single-page PDF**
by converting the visible table into an image using `html2canvas`.

It is specifically designed for:
- Webflow CMS
- Webflow Tabs
- Complex grid / div-based tables
- Guaranteed **ONE PAGE** output
- Exact visual match with on-screen design

---

## ✨ Features

- ✅ Prints **only the active Tab Pane**
- ✅ Exact same design as on screen
- ✅ Always **one page**
- ✅ No CSS Grid / print bugs
- ✅ Works with CMS + filters + tabs
- ✅ Reliable across Chrome / Edge / Firefox

<table>
  <tr>
    <td align="center">
      <img
        src="https://github.com/user-attachments/assets/cf836dba-c7d8-4c38-aa32-09bd3e96e496"
        alt="Table on screen"
        width="600"
      />
      <br />
      <strong>On Screen</strong>
    </td>
    <td align="center">
      <img
        src="https://github.com/user-attachments/assets/0f3622c2-0a53-49dd-bcb8-befcbfc53175"
        alt="Printed PDF"
        width="600"
      />
      <br />
      <strong>Printed PDF</strong>
    </td>
  </tr>
</table>

## 📦 Dependencies

This script uses:

- **html2canvas v1.4.1**
  ```html
  https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js
  ```

---

## 🧩 Required Webflow Setup

### 1. Print Button

Your print button must have this ID:

```txt
print-btn
```

### 2. Tab Pane

The **Tab Pane that contains the table** must have this class:

```txt
print-area
```

⚠️ The class must be on the **Tab Pane itself**, not on a wrapper or collection item.

---

## 🧠 How It Works

1. Detects the active Webflow tab (`.w--tab-active`)
2. Captures the table area as an image
3. Opens a clean print window
4. Prints the image as **one A4 landscape page**

This avoids all browser print layout issues.

---

## 🧪 Browser Print Settings (IMPORTANT)

When saving as PDF:

* ❌ Disable **Headers and Footers**
* ✅ Layout: **Landscape**
* ✅ Scale: **100%**

---

## 🧾 Code

### Include html2canvas

```html
<script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>
```

### Print Script

```html
<script>
document.addEventListener("DOMContentLoaded", function () {
  const btn = document.getElementById("print-btn");

  btn.addEventListener("click", async function () {
    const target = document.querySelector(".w--tab-active.print-area");

    if (!target) {
      alert("Table not found");
      return;
    }

    // Capture the table as an image
    const canvas = await html2canvas(target, {
      scale: 2,
      useCORS: true,
      backgroundColor: "#f7f3ef"
    });

    const imgData = canvas.toDataURL("image/png");

    // Open a clean print window
    const win = window.open("", "_blank");

    win.document.write(`
      <html>
        <head>
          <title>Print Table</title>
          <style>
            @page {
              size: A4 landscape;
              margin: 10mm;
            }
            body {
              margin: 0;
              display: flex;
              justify-content: center;
              align-items: center;
            }
            img {
              max-width: 100%;
              max-height: 100%;
            }
          </style>
        </head>
        <body>
          <img src="${imgData}" />
        </body>
      </html>
    `);

    win.document.close();
    win.focus();

    setTimeout(() => {
      win.print();
      win.close();
    }, 300);
  });
});
</script>
```

---

## 🚫 Known Limitations

* Output is an **image**, not selectable text
* Very large tables may require adjusting `scale`
* Requires browser print dialog (no silent printing)

---

## 🟢 When to Use This

Use this approach if:

* You need **guaranteed one-page output**
* Your table is built with divs / grid
* Browser print CSS keeps breaking
* Visual accuracy matters more than text selection
