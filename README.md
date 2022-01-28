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

# Properties ที่ใช้
- [version](https://github.com/rabbitinblack/wordpress-theme-json#version)
- [$schema](https://github.com/rabbitinblack/wordpress-theme-json#schema)
- [settings](https://github.com/rabbitinblack/wordpress-theme-json#settings)
- styles
- customTemplates
- templateParts

## version
ในตอนที่อ่าน version ที่ให้ใช้เป็น version 2

## $schema
ใส่ https://schemas.wp.org/trunk/theme.json เพื่อช่วยในการเช็คว่าใส่ properties ถูกต้องมั้ย

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json"
}
```

## settings
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

### appearanceTools
อันนี้ยังไม่รู้ว่าแตกต่างกันยังไง ระหว่าง `true` กับ `false`

### blocks
สำหรับตั้งค่า settings แยกสำหรับ block ที่กำหนด โดยสามารถดู https://developer.wordpress.org/block-editor/reference-guides/core-blocks/ เพื่อใช้ประกอบในการตั้งค่า settings ของแต่ละ block และดูชื่อ block ที่ใช้ในการตั้งค่าได้ที่ด้านล่าง [Block List](https://github.com/rabbitinblack/wordpress-theme-json#block-list)

### border
- `color` สามารถกำหนดสีของเส้นกรอบ
	- `true` ได้
	- `false` ไม่ได้
- `radius` สามารถกำหนดความมนของเส้นกรอบ
	- `true` ได้
	- `false` ไม่ได้
- `style` สามารถกำหนดลักษณะของเส้นกรอบ
	- `true` ได้
	- `false` ไม่ได้
- `width` สามารกำหนดความกว้างของเส้นกรอบ
	- `true` ได้
	- `false` ไม่ได้

```json
"border": {
	"color": true,
	"radius": true,
	"style": true,
	"width": true
}
```

### color
- `background` สามารถกำหนดสีให้ background
	- `true` ได้
	- `false` ไม่ได้
- `custom` สามารถปรับค่าสีที่กำหนด
	- `true` ได้
	- `false` ไม่ได้
- `customDuotone` สามารถปรับค่าสีสำหรับ Duotone
	- `true` ได้
	- `false` ไม่ได้
- `customGradient` สามารถปรับค่าสีสำหรับ Gradient
	- `true` ได้
	- `false` ไม่ได้
- `defaultGradients` สามารถเลือกสีมาตรฐานของ Gradient ที่ WordPress เตรียมไว้ให้
	- `true` ได้
	- `false` ไม่ได้
- `defaultPalette` สามารถเลือกชุดสีมาตรฐานที่ WordPress เตรียมไว้ให้
	- `true` ได้
	- `false` ไม่ได้
- `duotone` สร้างชุดสีสำหรับ Duotone
	- `name` ชื่อของ duotone นี้
	- `slug` slug ของ duotone นี้ เพื่อนำไปสร้าง variable css ใน pattern นี้ `--wp--preset--duotone--{slug}`
	- `colors` สีที่ใช้สำหรับ duotone เป็นคู่สีแบบ array
- `gradients` สร้างชุดสีสำหรับ Gradients
	- `name` ชื่อของ gradient นี้
	- `slug` slug ของ gradient นี้ เพื่อนำไปสร้าง variable css ใน pattern นี้ `--wp--preset--gradient--{slug}`
	- `gradient` สามารถใช้ https://cssgradient.io/ เพื่อปรับแต่ง gradient ที่ต้องการแล้วนำมาใส่
- `link` สามารถเลือกสีสำหรับลิงก์
	- `true` ได้
	- `false` ไม่ได้
- `palette` สร้างชุดสีพื้นฐาน
	- `name` ชื่อของสีนี้
	- `slug` slug ของสีนี้ เพื่อนำไปสร้าง variable css ใน pattern นี้ `--wp--preset--color--{slug}`
	- `color` ค่าของสี โดยรูปแบบของค่าสีที่ใส่ สามารถดูได้จาก https://developer.mozilla.org/en-US/docs/Web/CSS/color
- `text` สามารถเลือกสีให้ตัวอักษร
	- `true` ได้
	- `false` ไม่ได้

```json
"color": {
	"background": true,
	"custom": true,
	"customDuotone": true,
	"customGradient": true,
	"defaultGradients": true,
	"defaultPalette": true,
	"duotone": [
		{
			"name": "Black and White",
			"slug": "black-and-white",
			"colors": [ "#000000", "#ffffff" ]
		}
	],
	"gradients": [
			{
			"name": "Black to White",
			"slug": "black-white",
			"gradient": "linear-gradient(135deg,rgb(0,0,0) 50%,rgb(255,255,255) 100%)"
		}
	],
	"link": true,
	"palette": [
		{
			"name": "Black",
			"slug": "black",
			"color": "#000000"
		},
		{
			"name": "White",
			"slug": "white",
			"color": "#FFFFFF"
		}
	],
	"text": true
}
```

### layout
- `contentSize` กำหนดความกว้างของกล่องสำหรับ content
- `wideSize` กำหนดความกว้างของกล่องสำหรับการใช้ align wide

```
"layout": {
	"contentSize": "840px",
	"wideSize": "1100px"
}
```

### spacing
- `blockGap` ทำให้ block สามารถกำหนดระยะห่าง
> แต่จากที่ทดลองใช้งาน ยังงงกับมันอยู่ว่า จริง ๆ มันใช้งานอย่างไร <
	- `true` ได้
	- `false` ไม่ได้
- `margin`
- `padding`
- `units`

# Block List
- core/archives
- core/audio
- core/block
- core/button
- core/buttons
- core/calendar
- core/categories
- core/code
- core/column
- core/columns
- core/comment-author-name
- core/comment-author-avatar
- core/comment-content
- core/comment-date
- core/comment-edit-link
- core/comment-reply-link
- core/comment-template
- core/comments-query-loop
- core/cover
- core/embed
- core/file
- core/freeform
- core/gallery
- core/group
- core/heading
- core/home-link
- core/html
- core/image
- core/latest-comments
- core/latest-posts
- core/list
- core/loginout
- core/media-text
- core/missing
- core/more
- core/navigation
- core/navigation-link
- core/nextpage
- core/page-list
- core/paragraph
- core/post-author
- core/post-comments
- core/post-comments-count
- core/post-comments-form
- core/post-comments-link
- core/post-content
- core/post-date
- core/post-excerpt
- core/post-featured-image
- core/post-navigation-link
- core/post-template
- core/post-terms
- core/post-title
- core/preformatted
- core/pullquote
- core/query
- core/query-pagination
- core/query-pagination-next
- core/query-pagination-numbers
- core/query-pagination-previous
- core/query-title
- core/quote
- core/rss
- core/search
- core/separator
- core/shortcode
- core/site-logo
- core/site-tagline
- core/site-title
- core/social-link
- core/social-links
- core/spacer
- core/table
- core/table-of-contents
- core/tag-cloud
- core/template-part
- core/term-description
- core/text-columns
- core/verse
- core/video
- core/widget-area
- core/legacy-widget
- core/widget-group