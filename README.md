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
จากที่อ่านคือ ถ้าเป็น `true` มันจะไปเปลี่ยน settings ของทุก block ที่เป็น `false` ให้เป็น `true` ทั้งหมด โดยเป็นกลุ่มนี้
- `border`: color, radius, style, width
- `color`: link
- `spacing`: blockGap, margin, padding
- `typography`: lineHeight
แต่จากที่ทดลองทำ ก็ยังไม่รู้ว่าแตกต่างกันยังไง ระหว่าง `true` กับ `false`

### blocks
สำหรับตั้งค่า settings แยกสำหรับ block ที่กำหนด โดยสามารถดู https://developer.wordpress.org/block-editor/reference-guides/core-blocks/ เพื่อใช้ประกอบในการตั้งค่า settings ของแต่ละ block และดูชื่อ block ที่ใช้ในการตั้งค่าได้ที่ด้านล่าง [Block List](https://github.com/rabbitinblack/wordpress-theme-json#block-list)

### border
- `color` กำหนดสีของเส้นกรอบ
	- `true` ได้
	- `false` ไม่ได้
- `radius` กำหนดความมนของเส้นกรอบ
	- `true` ได้
	- `false` ไม่ได้
- `style` กำหนดลักษณะของเส้นกรอบ
	- `true` ได้
	- `false` ไม่ได้
- `width` กำหนดความกว้างของเส้นกรอบ
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
- `background` กำหนดสีให้ background
	- `true` ได้
	- `false` ไม่ได้
- `custom` ปรับค่าสีที่กำหนด
	- `true` ได้
	- `false` ไม่ได้
- `customDuotone` ปรับค่าสีสำหรับ Duotone
	- `true` ได้
	- `false` ไม่ได้
- `customGradient` ปรับค่าสีสำหรับ Gradient
	- `true` ได้
	- `false` ไม่ได้
- `defaultGradients` เลือกสีมาตรฐานของ Gradient ที่ WordPress เตรียมไว้ให้
	- `true` ได้
	- `false` ไม่ได้
- `defaultPalette` เลือกชุดสีมาตรฐานที่ WordPress เตรียมไว้ให้
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
- `link` เลือกสีสำหรับลิงก์
	- `true` ได้
	- `false` ไม่ได้
- `palette` สร้างชุดสีพื้นฐาน
	- `name` ชื่อของสีนี้
	- `slug` slug ของสีนี้ เพื่อนำไปสร้าง variable css ใน pattern นี้ `--wp--preset--color--{slug}`
	- `color` ค่าของสี โดยรูปแบบของค่าสีที่ใส่ สามารถดูได้จาก https://developer.mozilla.org/en-US/docs/Web/CSS/color
- `text` เลือกสีให้ตัวอักษร
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
- `blockGap` block สามารถกำหนดระยะห่างในแนวตั้ง *แต่จากที่ทดลองใช้งาน ยังงงกับมันอยู่ว่า จริง ๆ มันใช้งานอย่างไร*
	- `true` ได้
	- `false` ไม่ได้
- `margin` กำหนด margin
	- `true` ได้
	- `false` ไม่ได้
- `padding` กำหนด padding
	- `true` ได้
	- `false` ไม่ได้
- `units` กำหนด unit ที่จะให้ เป็น array
	- `px`
	- `em`
	- `rem`
	- `vh`
	- `vw`
	- `%`

```json
"spacing": {
	"blockGap": true,
	"margin": true,
	"padding": true,
	"units": [
		"px",
		"em",
		"rem",
		"vh",
		"vw",
		"%"
	]
}
```

### typography
- `customFontSize` กำหนดขนาดตัวอักษรเอง
	- `true` ได้
	- `false` ไม่ได้
- `fontStyle` กำหนด Style ของตัวอักษร
	- `true` ได้
	- `false` ไม่ได้
- `fontWeight` กำหนดน้ำหนักของตัวอักษร
	- `true` ได้
	- `false` ไม่ได้
- `letterSpacing` กำหนดระยะห่างของตัวอักษร
	- `true` ได้
	- `false` ไม่ได้
- `lineHeight` กำหนดระยะห่างของตัวอักษรระหว่างบรรทัด
	- `true` ได้
	- `false` ไม่ได้
- `textDecoration` กำหนดลักษณะของเส้นที่ใช้ตกแต่งตัวอักษร
	- `true` ได้
	- `false` ไม่ได้
- `textTransform` กำหนดการ Transform ให้ตัวอักษร https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform
	- `true` ได้
	- `false` ไม่ได้
- `dropCap` กำหนดให้ตัวอักษรเป็น Dropcap
	- `true` ได้
	- `false` ไม่ได้
- `fontSizes` สร้างขนาดของตัวอักษรไว้ให้เลือกได้ โดยกำหนดเป็น array
	- `name` ชื่อของขนาดตัวอักษร
	- 'slug' slug ของขนาดตัวอักษร เพื่อนำไปสร้าง variable css ใน pattern นี้ `--wp--preset--font-size--{slug}`
	- `size` ขนาดของตัวอักษร โดยสามารถกำหนดเป็น `px`, `em`, `rem`, `vh`, `vw` และ `%` ได้
- `fontFamilies` สร้างชุดของ font family เพื่อนำไปใช้งาน
	- `name` ชื่อของ font family นี้
	- `slug` slug ของ font family นี้  เพื่อนำไปสร้าง variable css ใน pattern นี้ `--wp--preset--font-family--{slug}`
	- `fontFamily` ค่าของ font family ที่จะนำไปใช้ https://developer.mozilla.org/en-US/docs/Web/CSS/font-family

```json
"typography": {
	"customFontSize": true,
	"fontStyle": true,
	"fontWeight": true,
	"letterSpacing": true,
	"lineHeight": true,
	"textDecoration": true,
	"textTransform": true,
	"dropCap": true,
	"fontSizes": [
		{
			"name": "Extra Small",
			"slug": "xs",
			"size": "0.75rem"
		},
		{
			"name": "Small",
			"slug": "sm",
			"size": "0.875rem"
		},
		{
			"name": "Default",
			"slug": "md",
			"size": "1rem"
		},
		{
			"name": "Large",
			"slug": "lg",
			"size": "1.125rem"
		},
		{
			"name": "Extra Large",
			"slug": "xl",
			"size": "1.25rem"
		},
		{
			"name": "2XL",
			"slug": "2xl",
			"size": "1.5rem"
		},
		{
			"name": "3XL",
			"slug": "3xl",
			"size": "1.875rem"
		},
		{
			"name": "4XL",
			"slug": "4xl",
			"size": "2.25rem"
		},
		{
			"name": "5XL",
			"slug": "5xl",
			"size": "3rem"
		}
	],
	"fontFamilies": [
		{
			"name": "Default",
			"slug": "default",
			"fontFamily": "Arial, sans-serif"
		}
	]
}
```

### custom
สร้าง variable css ใน pattern นี้ `--wp--custom--color--{key}--{nest-key}` โดย `key` และ `nest-key` ถ้าเราเขียนแบบ `camelCased` มันจะถูกเปลี่ยนเป็น `kebab-case` รวมถึงเพื่อ follow ตามข้อกำหนดในการเขียน css property naming scheme ที่ถ้า `key` ใน level ที่ต่างกัน จะแบ่งด้วย `--` ดังนั้นเราจะไม่ใช้ `key` และ `nest-key` ที่มี `--` ประกอบ

```json
"custom": {
	"borderStyle": {
		"solid": "solid"
	}
}
```

ตามตัวอย่างมันจะไปสร้าง
`--wp--custom--border-style--solid: "solid"`
ไว้ เราสามารถนำไปใช้ต่อได้

## styles
สำหรับกำหนด CSS ให้กับตัว body โดยสามารถกำหนด
- border
- color
- spacing
- typography
- elements
- blocks
โดยเราสามารถใช้ variable css ที่เรากำหนดใน settings มาใช้ด้วยได้ รวมถึง default ที่ WordPress เตรียมไว้ให้ เช่น `--wp--preset-color-white` หรือ `--wp--custom--border-style--solid`

### border
- `color` กำหนดสีให้กรอบ
- `radius` กำหนดความมนให้กรอบ
- `style` กำหนดรูปแบบของกรอบ
- `width` กำหนดความหนาของกรอบ

```json
"border": {
	"color": "#FF0000",
	"radius": "5px",
	"style": "solid",
	"width": "1px"
}
```

### color
- `background` กำหนดสีพื้นหลัง
- `gradient` กำหนดสีพื้นหลังแบบ gradient
- `text` กำหนดสีตัวอักษร

```json
"color": {
	"background": "var(--wp--preset--color--black)",
	"gradient": "var(--wp--preset--gradient--black-white)",
	"text": "var(--wp--preset--color--white)"
}
```

### spacing
- `blockGap` กำหนดขนาดของระยะห่างระหว่าง block
- `margin` กำหนดขนาดของ margin โดยแบ่งเป็น
	- `top`
	- `right`
	- `bottom`
	- `left`
- `padding` กำหนดขนาดของ padding โดยแบ่งเป็น
	- `top`
	- `right`
	- `bottom`
	- `left`

```json
"spacing": {
	"blockGap": "var(--wp--custom--spacing--md)",
	"margin": {
		"top": "var(--wp--custom--spacing--md)",
		"right": "var(--wp--custom--spacing--md)",
		"bottom": "var(--wp--custom--spacing--md)",
		"left": "var(--wp--custom--spacing--md)"
	},
	"padding": {
		"top": "var(--wp--custom--spacing--md)",
		"right": "var(--wp--custom--spacing--md)",
		"bottom": "var(--wp--custom--spacing--md)",
		"left": "var(--wp--custom--spacing--md)"
	}
}
```

### typography
- `fontFamily` กำหนด font family
- `fontSize` กำหนดขนาดตัวอักษร
- `fontStyle` กำหนด style ของตัวอักษร
- `fontWeight` กำหนดความหนาของตัวอักษร
- `letterSpacing` กำหนดระยะห่างระหว่างตัวอักษร
- `lineHeight` กำหนดระยะห่างระหว่างบรรทัด
- `textDecoration` กำหนดลักษณะของเส้นที่ใช้ตกแต่งตัวอักษร
- `textTransform` กำหนดการ Transform ของตัวอักษร

```json
"typography": {
	"fontFamily": "var(--wp--preset--font-family--default)",
	"fontSize": "var(--wp--preset--font-size--md)",
	"fontStyle": "normal",
	"fontWeight": "normal",
	"letterSpacing": "0",
	"lineHeight": "var(--wp--custom--line-height--xl)",
	"textDecoration": "none",
	"textTransform": "none"
}
```

### elements
เป็นการกำหนด CSS ให้กับ element ซึ่งเราสามารถใช้ได้กับ 7 elements นี้
- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `link`

โดยแต่ละ element เราสามารถกำหนดสิ่งเหล่านี้ได้
- `border`
- `color`
- `spacing`
- `typography`

```json
"elements": {
	"h1": {
		"typography": {
			"fontFamily": "var(--wp--preset--font-family--default)",
			"fontWeight": "bold",
			"lineHeight": "var(--wp--custom--line-height--xs)",
			"fontSize": "var(--wp--preset--font-size--5-xl)"
		}
	},
	"h2": {
		"typography": {
			"fontFamily": "var(--wp--preset--font-family--default)",
			"fontWeight": "bold",
			"lineHeight": "var(--wp--custom--line-height--sm)",
			"fontSize": "var(--wp--preset--font-size--3-xl)"
		}
	},
	"h3": {
		"typography": {
			"fontFamily": "var(--wp--preset--font-family--default)",
			"fontWeight": "bold",
			"lineHeight": "var(--wp--custom--line-height--md)",
			"fontSize": "var(--wp--preset--font-size--xl)"
		}
	},
	"h4": {
		"typography": {
			"fontFamily": "var(--wp--preset--font-family--default)",
			"fontWeight": "bold",
			"lineHeight": "var(--wp--custom--line-height--xl)",
			"fontSize": "var(--wp--preset--font-size--md)"
		}
	},
	"h5": {
		"typography": {
			"fontFamily": "var(--wp--preset--font-family--default)",
			"fontWeight": "bold",
			"lineHeight": "var(--wp--custom--line-height--lg)",
			"fontSize": "var(--wp--preset--font-size--sm)"
		}
	},
	"h6": {
		"typography": {
			"fontFamily": "var(--wp--preset--font-family--default)",
			"fontWeight": "bold",
			"lineHeight": "var(--wp--custom--line-height--md)",
			"fontSize": "var(--wp--preset--font-size--xs)"
		}
	},
	"link": {
		"border": {
			"color": "var(--wp--preset--color--white)",
			"radius": "var(--wp--custom--border-radius--sm)",
			"style": "var(--wp--custom--border-style--solid)",
			"width": "var(--wp--custom--border-width--xs)"
		},
		"color": {
			"text": "var(--wp--preset--color--white)"
		},
		"spacing": {
			"margin": {
				"top": "var(--wp--custom--spacing--sm)",
				"right": "var(--wp--custom--spacing--sm)",
				"bottom": "var(--wp--custom--spacing--sm)",
				"left": "var(--wp--custom--spacing--sm)"
			},
			"padding": {
				"top": "var(--wp--custom--spacing--sm)",
				"right": "var(--wp--custom--spacing--sm)",
				"bottom": "var(--wp--custom--spacing--sm)",
				"left": "var(--wp--custom--spacing--sm)"
			}
		},
		"typography": {
			"fontWeight": "bold"
		}
	}
}
```

### blocks
สามารถกำหนด CSS ให้แต่ละ block ได้ ดูชื่อ block ที่ใช้ในการตั้งค่าได้ที่ด้านล่าง [Block List](https://github.com/rabbitinblack/wordpress-theme-json#block-list)
โดยแต่ละ block เราสามารถกำหนดสิ่งเหล่านี้ได้
- `border`
- `color`
- `spacing`
- `typography`

```json
"blocks": {
	"core/button": {
		"border": {
			"color": "var(--wp--preset--color--black)",
			"radius": "var(--wp--custom--border-radius--sm)"
		},
		"color": {
			"background": "var(--wp--preset--color--black)",
			"text": "var(--wp--preset--color--white)"
		},
		"spacing": {
			"margin": {
				"top": "var(--wp--custom--spacing--sm)",
				"right": "var(--wp--custom--spacing--sm)",
				"bottom": "var(--wp--custom--spacing--sm)",
				"left": "var(--wp--custom--spacing--sm)"
			},
			"padding": {
				"top": "var(--wp--custom--spacing--sm)",
				"right": "var(--wp--custom--spacing--sm)",
				"bottom": "var(--wp--custom--spacing--sm)",
				"left": "var(--wp--custom--spacing--sm)"
			}
		},
		"typography": {
			"fontSize": "var(--wp--preset--font-size--lg)"
		}
	}
}
```

## customTemplates
สร้าง Template ให้ใช้สำหรับ post, page หรือ custom post type ที่กำหนดได้ โดยทำเป็น File HTML เก็บไว้ใน Folder ชื่อ `templates`
วิธีการกำหนดการใช้งานจะมี
- `name` ชื่อของ File Template ใน Folder
- `title` ชื่อของ Template
- `postTypes` กำหนด post type ที่สามารถใช้งาน Template นี้ได้ในรูปแบบ Array ค่า Default ของมันจะเป็น `page`

```json
"customTemplates": [
	{
		"name": "blank",
		"title": "Blank",
		"postTypes": [
			"page",
			"post"
		]
	}
]
```

## templateParts
สร้าง Template เป็น Part เพื่อนำไปประกอบใน Custom Template หรือในการ Edit ที่หลังบ้าน WordPress ได้ โดยเป็น File HTML เก็บไว้ที่ Folder `parts`
วิธีการกำหนดการใช้งานจะมี
- `name` ชื่อของ File Template ใน Folder
- `title` ชื่อของ Template
- `area` กำหนด area ที่ Part นี้จะไปแสดงผล เท่าที่ดูตอนนี้จะมี `header`, `footer` และ `general`

```json
"templateParts": [
	{
		"name": "header",
		"title": "Header",
		"area": "header"
	}
]
```

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