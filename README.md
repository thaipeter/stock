# คลังอะไหล่เมาท์เทน — C-FACTORY WMS

> Smart Inventory Management System  
> Powered by Google Apps Script + Vanilla JS

---

## โครงสร้างโปรเจกต์

```
project/
│
├── index.html              ← Entry point (Netlify root)
├── netlify.toml            ← Netlify config
│
├── css/
│   ├── style.css           ← Global styles, dark theme, variables
│   ├── dashboard.css       ← Dashboard-specific component styles
│   └── responsive.css      ← Media queries & mobile overrides
│
├── js/
│   ├── api.js              ← Global state, GAS bridge, component loader, init
│   ├── app.js              ← All UI rendering, navigation, interactions
│   └── chart.js            ← Chart.js rendering functions
│
├── components/
│   ├── navbar.html         ← Top navigation bar
│   ├── sidebar.html        ← All modal dialogs
│   └── footer.html         ← QR Scanner panel
│
├── pages/
│   ├── dashboard.html      ← Dashboard overview section
│   ├── transactionsInOut.html ← รับเข้า/เบิกออก
│   ├── borrowedItems.html  ← Borrow management
│   ├── monthlyOrders.html  ← Orders, PO, low-stock
│   ├── items.html          ← Inventory items table
│   ├── tools.html          ← Tools & equipment table
│   ├── qrManagement.html   ← QR code management
│   ├── history.html        ← Transaction logs
│   └── settings.html       ← System settings
│
└── assets/
    ├── images/             ← Static images
    └── icons/              ← Custom icon files
```

---

## วิธี Deploy

### Netlify (แนะนำ)
1. Drag & drop โฟลเดอร์ `project/` ไปที่ [app.netlify.com](https://app.netlify.com)
2. หรือ connect GitHub repo แล้ว set publish directory = `.`

### Vercel
```bash
cd project
npx vercel --prod
```

### GitHub Pages
1. Push ทั้งหมดไป repository
2. Settings → Pages → Source: main branch, root `/`

---

## การตั้งค่า Google Apps Script

1. เปิด `code1_-_Copy.gs` ใน Google Apps Script
2. รัน `setupScriptProperties()` ครั้งแรกเพื่อบันทึก config
3. Deploy as Web App → Execute as: Me, Who has access: Anyone
4. Copy Web App URL ไปใส่ใน `api.js` (ตัวแปร `GAS_URL` ถ้ามี)

---

## Tech Stack
- **Frontend**: Vanilla JS, Bootstrap 5.3, Chart.js
- **Backend**: Google Apps Script (GAS)
- **Database**: Google Sheets
- **Auth**: LINE Bot + PIN-based login
- **QR**: html5-qrcode, jsQR, QRCode.js
