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
- [version](https://github.com/rabbitinblack/wordpress-theme-json#version)
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
### settings
สำหรับกำหนด Settings ของ block ทั้งหมด และสามารถกำหนด Settings ให้กับแต่ละ block ได้ ซึ่ง Settings จะกำหนดได้เฉพาะ Settings ที่ block นั้น ๆ มีด้วย

โดยแบ่งการตั้งค่าได้ด้งนี้
- appearanceTools
- blocks
- border
- color
- layout
- spacing
- typography
- custom

#### appearanceTools
อันนี้ยังไม่รู้ว่าแตกต่างกันยังไง ระหว่าง `true` กับ `false`