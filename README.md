# 🪔 เทียนปัญญา E-Book Builder

เครื่องมือ Web Application ฟรี สำหรับนักเรียน ม.2 ในการสร้าง e-book ด้วย AI
เรื่อง "เทียนพรรษา: ศิลปะแห่งความเชื่อ สู่การเป็นมรดกทางภูมิปัญญา"

---

## ✨ Live Demo (ทดสอบ)

เปิดไฟล์ `index.html` ในเบราว์เซอร์ได้เลย ไม่ต้องติดตั้งอะไร — ใช้งานได้ทันที
ทุกข้อมูลจะถูกบันทึกใน `localStorage` ของเบราว์เซอร์อัตโนมัติ (ไม่หายเวลาปิดหน้า)

---

## 📦 ไฟล์ในโปรเจกต์

| ไฟล์ | คำอธิบาย |
|---|---|
| `index.html` | **Web App หลัก** — นักเรียนเข้าใช้งาน (1737 บรรทัด, ~70 KB) |
| `google-apps-script.gs` | Google Apps Script สำหรับเก็บข้อมูลเข้า Google Sheet |
| `README.md` | คู่มือนี้ |

---

## 🚀 วิธี Deploy (3 ทางเลือก — เรียงจากง่ายสุด)

### ⭐ ทางเลือก A: GitHub Pages (แนะนำ — ฟรี 100%, ไม่มีโฆษณา)

**ข้อดี:** ฟรี 100%, มี HTTPS, custom domain ได้, version control, เร็ว
**ข้อเสีย:** นักเรียนต้อง login GitHub (ถ้าใช้ private repo)

1. **สมัคร GitHub** ที่ https://github.com (ฟรี)
2. **สร้าง Repository ใหม่** ชื่อ `thian-ebook-builder` (public)
3. **อัปโหลดไฟล์** `index.html` ขึ้น repository
4. **ไป Settings → Pages**
   - Source: `main` branch
   - Folder: `/ (root)`
   - Save
5. **รอ 1-2 นาที** เว็บจะอยู่ที่:
   `https://[username].github.io/thian-ebook-builder/`

**แชร์ลิงก์ให้นักเรียนได้เลย!** 🎉

---

### ทางเลือก B: Netlify Drop (ง่ายที่สุด — ไม่ต้องสมัคร)

**ข้อดี:** ไม่ต้องสมัคร, ลากวางไฟล์ = ได้เว็บทันที
**ข้อเสีย:** URL เปลี่ยนทุกครั้ง (ถ้าไม่ sign up)

1. ไปที่ https://app.netlify.com/drop
2. **ลากไฟล์ `index.html`** ไปวางในกล่อง
3. **รอ 10 วินาที** → ได้ URL ทันที เช่น `https://random-name-123.netlify.app`
4. (ถ้าอยากได้ URL ถาวร) Sign up ฟรี → เปลี่ยนชื่อ site ได้

---

### ทางเลือก C: Google Apps Script (รวมข้อมูลเข้า Google Sheet)

**ข้อดี:** ข้อมูลนักเรียนเข้า Google Sheet อัตโนมัติ — ครูตรวจง่าย
**ข้อเสีย:** โหลดช้ากว่าเล็กน้อย

#### ขั้นตอน:

**ตอนที่ 1: สร้าง Google Sheet + Apps Script**

1. ไปที่ https://sheets.google.com → สร้าง Sheet ใหม่ (ว่างๆ)
2. ตั้งชื่อ Sheet เช่น "E-Book Builder Submissions"
3. ไปที่ **Extensions → Apps Script**
4. ลบโค้ดเดิมทั้งหมด → paste เนื้อหาใน `google-apps-script.gs`
5. บันทึก (Ctrl+S / Cmd+S)

**ตอนที่ 2: Deploy เป็น Web App**

1. คลิก **Deploy → New deployment**
2. คลิกไอคอนเฟือง ⚙️ → เลือก **Web app**
3. ตั้งค่า:
   - Description: "E-Book Builder API"
   - Execute as: **Me (your email)**
   - Who has access: **Anyone** (สำคัญ! เพื่อให้นักเรียนส่งได้)
4. คลิก **Deploy** → อนุญาต permissions
5. **Copy Web App URL** ที่ได้ (จะอยู่ในรูป `https://script.google.com/macros/s/.../exec`)

**ตอนที่ 3: นำ URL ไปใส่ในเว็บ**

แก้ไข `index.html` บรรทัดที่มี:
```javascript
const url = localStorage.getItem('gas-webapp-url') || '';
```

ให้นักเรียนเปิด Console (F12) แล้วพิมพ์:
```javascript
localStorage.setItem('gas-webapp-url', 'https://script.google.com/macros/s/YOUR_URL/exec');
```

หรือครูแก้ไขในไฟล์แล้ว deploy ใหม่

**ตอนที่ 4: แชร์ให้นักเรียน**

- ถ้าใช้ GitHub Pages + Google Apps Script: นักเรียนเข้าเว็บ → กรอก → กด "ส่งให้ครู"
- ข้อมูลจะไปปรากฏใน Google Sheet อัตโนมัติ

---

### ทางเลือก D: Vercel / Cloudflare Pages

เหมือน GitHub Pages — ต้อง sign up แต่เร็วมาก

- **Vercel:** https://vercel.com → Import repo หรือลากไฟล์
- **Cloudflare Pages:** https://pages.cloudflare.com → Connect GitHub

---

## 🛠️ การใช้งาน (สำหรับครู)

### ใช้ในห้องเรียน (แนะนำ 5 คาบ × 50 นาที)

| คาบ | กิจกรรม | เวลา |
|---|---|---|
| **คาบ 1** | แนะนำเครื่องมือ + ทดลองใช้ | 50 นาที |
| **คาบ 2** | ขั้น 1-4 (ข้อมูล, ธีม, ตัวละคร, โครงเรื่อง) | 50 นาที |
| **คาบ 3** | ขั้น 5 (Storyboard 12 หน้า) | 50 นาที |
| **คาบ 4** | ขั้น 6 (สร้าง Prompt + ใช้ AI ทำภาพ) | 50 นาที |
| **คาบ 5** | รวมเล่ม e-book (Canva) + นำเสนอ | 50 นาที |

### Flow การเรียนรู้ (Design Thinking)

1. **Empathize** → นักเรียนตั้งคำถามจากข้อสงสัย (Step 2)
2. **Define** → เลือกธีม/สไตล์ (Step 2)
3. **Ideate** → ออกแบบตัวละคร + โครงเรื่อง (Step 3-4)
4. **Prototype** → เขียน Storyboard (Step 5)
5. **Test** → สร้าง Prompt → ใช้ AI ทำภาพ → ทดสอบ (Step 6)
6. **Present** → นำเสนอ + เครดิต (Step 7)

---

## 📊 Features ที่มีในเว็บ

✅ **Stepper 7 ขั้น** — นำทางชัดเจน ไม่หลง
✅ **Visual Options** — เลือกธีม/สไตล์/โครงเรื่องด้วยภาพ
✅ **Character Builder** — สร้างตัวละคร 1-3 ตัว พร้อม trait chips
✅ **Color Picker** — เลือกสีประจำตัวละคร
✅ **Storyboard 12 หน้า** — ตารางเขียนเนื้อหา + ฉาก
✅ **Prompt Generator** — สร้าง prompt อัตโนมัติตามสไตล์ที่เลือก
✅ **Copy/Download** — คัดลอกทีละหน้า หรือ download .txt
✅ **LocalStorage** — บันทึกข้อมูลอัตโนมัติ ไม่หายเวลาปิดหน้า
✅ **Google Sheet Integration** — ส่งงานเข้า Sheet ครู (ผ่าน Apps Script)
✅ **Credits Page** — สร้างหน้าเครดิตอัตโนมัติ
✅ **Responsive** — ใช้ได้ทั้งมือถือ/แท็บเล็ต/คอม
✅ **Print-friendly** — พิมพ์เป็น PDF ได้
✅ **No dependencies** — ไม่พึ่ง framework ภายนอก (มี Google Fonts เท่านั้น)

---

## 🎨 Design System

| Token | Value | ใช้ที่ |
|---|---|---|
| `--gold` | #D4A574 | เน้น, ปุ่ม accent |
| `--crimson` | #C8423C | ปุ่มหลัก, active state |
| `--ink` | #1A1A2E | พื้นหลัง header/footer, ข้อความหลัก |
| `--paper` | #FAF6EE | พื้นหลังหลัก |
| `--teal` | #2D5F6B | สีรอง |

**Font:** Sarabun (body), Chakra Petch (heading/UI), Noto Serif Thai (กาพย์)

---

## 🔧 การปรับแต่ง

### เปลี่ยนสี/ฟอนต์
แก้ CSS variables ใน `<style>` ของ `index.html`:
```css
:root {
  --gold: #D4A574;
  --crimson: #C8423C;
  ...
}
```

### เพิ่มสไตล์หนังสือ
แก้ array `STYLES` ใน `<script>`:
```javascript
const STYLES = [
  { id: 'manga', icon: '🇯🇵', title: 'Manga ญี่ปุ่น', desc: '...', previewClass: '...', keywords: '...' },
  ...
];
```

### เพิ่มธีม
แก้ array `THEMES` ใน `<script>`:
```javascript
const THEMES = [
  { id: 'new-theme', icon: '🆕', title: 'ธีมใหม่', desc: '...', color: '#HEX' },
  ...
];
```

---

## 🐛 Troubleshooting

| ปัญหา | วิธีแก้ |
|---|---|
| เว็บโหลดไม่ขึ้น | ตรวจสอบ URL, ลอง Refresh, ตรวจ Internet |
| นักเรียนบันทึกไม่ได้ | ตรวจ localStorage (เปิด DevTools → Application → Local Storage) |
| ส่งงานไม่เข้า Sheet | ตรวจ Apps Script URL, ตรวจ Permissions "Anyone" |
| Prompt ภาษาอังกฤษแปลก | น้องสามารถแก้ใน `<script>` ส่วน `buildPrompt()` |
| ข้อมูลหายเมื่อปิด | localStorage อาจถูก clear — ใช้ "บันทึก" บ่อยๆ |

---

## 📜 License

ใช้ภายในโรงเรียนเสียมทองพิทยาคมและโรงเรียนเครือข่าย สพม.อุบลราชธานี อำนาจเจริญ
พัฒนาโดย: นายสรวิศ  แหวนเงิน
นวัตกรรม "เทียนปัญญา" (THIAN Model) | ภาคเรียนที่ 1 ปีการศึกษา 2569
