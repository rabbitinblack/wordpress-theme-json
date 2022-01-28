# WordPress Theme JSON
สร้างไว้เพื่อเก็บสิ่งที่เรียนเกี่ยวกับ theme.json ของ WordPress และทำ File ไว้เพื่อเป็น Default สำหรับงานตัวเองที่จะใช้ โดยดูจาก https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-json/ และตัว https://schemas.wp.org/trunk/theme.json ประกอบกัน

โดยโครงสร้างหลักที่อ่านมา จะเป็นดังนี้
```json
{
	"version": 2,
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"settings": {
	},
	"styles": {
	},
	"customTemplates": {
	},
	"templateParts": {
	}
}
```

## Properties ที่ใช้
- version
- [$schema](https://github.com/rabbitinblack/wordpress-theme-json#schema)
- settings
- styles
- customTemplates
- templateParts

### version
ในตอนที่อ่าน version ที่ให้ใช้เป็น version 2

### $schema
ใส่ https://schemas.wp.org/trunk/theme.json เพื่อช่วยในการเช็คว่าใส่ properties ถูกต้องมั้ย

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json"
}
```