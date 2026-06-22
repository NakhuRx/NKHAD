# เว็บแอป ยาความเสี่ยงสูง โรงพยาบาลนาคู

จัดทำโดย ฝ่ายเภสัชกรรม โรงพยาบาลนาคู

## โครงสร้างไฟล์
```
repository/
├── index.html   ← หน้าเว็บหลัก
├── drugs.json   ← ข้อมูลยาทั้งหมด (แก้ไข/เพิ่มข้อมูลได้ที่ไฟล์นี้)
└── style.css    ← ธีมพาสเทล ฟอนต์ไทย
```

## วิธีนำขึ้น GitHub และเผยแพร่ด้วย GitHub Pages

1. สร้าง repository ใหม่บน GitHub (เช่นชื่อ `nakhu-hospital-high-alert-drugs`)
2. อัปโหลดไฟล์ทั้ง 3 ไฟล์นี้ขึ้นไปที่ repository (หรือ git push จากเครื่อง)
   ```bash
   git init
   git add index.html drugs.json style.css
   git commit -m "เว็บแอปยาความเสี่ยงสูง โรงพยาบาลนาคู"
   git branch -M main
   git remote add origin https://github.com/<ชื่อผู้ใช้>/<ชื่อ-repo>.git
   git push -u origin main
   ```
3. เปิด **Settings > Pages** ใน repository
4. เลือก Source = `main` branch, โฟลเดอร์ `/ (root)` แล้วกด Save
5. รอสักครู่ ระบบจะให้ลิงก์เว็บไซต์ เช่น
   `https://<ชื่อผู้ใช้>.github.io/<ชื่อ-repo>/`

## การแก้ไข/เพิ่มข้อมูลยา
เปิดไฟล์ `drugs.json` แล้วเพิ่มรายการในรูปแบบ:
```json
{
  "id": 18,
  "name": "ชื่อยา",
  "generic_name": "ชื่อสามัญ",
  "category": "กลุ่มยา",
  "risk_level": "สูง",
  "pregnancy_category": "C",
  "pregnancy_note": "คำอธิบายความเสี่ยงในหญิงตั้งครรภ์",
  "description": "คำอธิบายโดยย่อ",
  "indications": "ข้อบ่งใช้",
  "mixing": "วิธีผสมและบริหารยา",
  "compatible_fluids": "สารน้ำที่เข้ากันได้",
  "contraindications": "ข้อห้ามใช้",
  "monitoring": "สิ่งที่ต้องติดตาม",
  "precautions": ["ข้อควรระวัง 1", "ข้อควรระวัง 2"],
  "interactions": "ปฏิกิริยาระหว่างยา"
}
```
ระบบจะแสดงผล กรองตามกลุ่มยา และค้นหาได้อัตโนมัติ ไม่ต้องแก้ไขโค้ด HTML/CSS

ปัจจุบันมีข้อมูลยาความเสี่ยงสูงครบ 17 รายการตามคู่มือ HAD ของฝ่ายเภสัชกรรม (Adrenaline, Amiodarone, Atropine, Calcium Gluconate, Digoxin, Dopamine, Insulin, Magnesium Sulfate, Morphine, Nicardipine, Norepinephrine, Nitroglycerin, Phenytoin, Potassium Chloride, Streptokinase, Terbutaline, Warfarin)

## ฟีเจอร์
- ค้นหายาแบบ real-time
- กรองตามกลุ่มยา (สร้าง chip อัตโนมัติจากข้อมูลใน drugs.json)
- หน้ารายละเอียดยา (modal) แสดงข้อบ่งใช้, การผสม/บริหารยา, สารน้ำที่เข้ากันได้, ข้อควรระวัง, ข้อห้ามใช้, การติดตามผู้ป่วย, ข้อมูลหญิงตั้งครรภ์ และปฏิกิริยาระหว่างยา
- มีตราสัญลักษณ์กระทรวงสาธารณสุขที่ส่วนหัวของเว็บ
- ดีไซน์พาสเทล ฟอนต์ไทย (Noto Sans Thai / Mitr) รองรับมือถือ
