# WordPress Theme JSON
สร้างไว้เพื่อเก็บสิ่งที่เรียนเกี่ยวกับ theme.json ของ WordPress และทำ File ไว้เพื่อเป็น Default สำหรับงานตัวเองที่จะใช้

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
- [$schema](https://github.com/rabbitinblack/wordpress-theme-json#schema)
- version
- settings
- styles
- customTemplates
- templateParts

### $schema
ใส่ https://schemas.wp.org/trunk/theme.json เพื่อช่วยในการเช็คว่าใส่ properties ถูกต้องมั้ย

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json"
}
```