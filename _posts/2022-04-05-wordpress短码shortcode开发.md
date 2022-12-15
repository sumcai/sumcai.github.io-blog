---
layout: post
title: wordpress短码shortcode开发
author: sumcai
article: false
tags: 
  - relive
categories: 
  - 建站
date: 2022-04-05 12:23:03
permalink: /other/Reliveshortcode/
---

# 开发步骤

## 修改文件

文件路径：`xxx-theme\admin\codestar-framework\config\shortcoder.php`

以添加提示框为例，示例代码：

```php
$prefix = 'csf_demo_shortcodes';
CSF::createSection( $prefix, array(
    'title'     => '提示框',
    'view'      => 'normal',
    'shortcode' => 'ri_tips',
    'fields'    => array(
        array(
            'id'     => 'type',
            'type'   => 'select',
            'title'  => '图标大小',
            'options' => array(
                'werror' => '红色错误框',
                'wwarn' => '黄色警告框',
                'wtips' => '蓝色计划框',
                'wnotice' => '绿色提醒框',
			),
        ),
        array(
            'id'     => 'content',
            'type'   => 'textarea',
            'title'  => '输入文本',
            'attributes' => array(
              'style'    => 'width: 100%;'
            ),
        ),
    ),
) );

function ri_tips_code( $atts, $content = null ) {
    $shortcode_atts = shortcode_atts(
        array(
            'type'     => '',
        ),
        $atts,
        'ri_tips'
    );

    $output = '<div class=' . $shortcode_atts['type'] . '>';
    $output .= do_shortcode($content);
    $output .= '</div>';
    return $output;
}

add_shortcode('ri_tips', 'ri_tips_code');
```



上门代码的显示效果：

![image-20220425214459925](https://ax0kqy8quzyr.compat.objectstorage.ap-osaka-1.oraclecloud.com/bucket-blog/2022/04/image-20220425214459925.png)

点击插入短码，编辑器中将添加`[ri_tips type="werror"]测试内容[/ri_tips]`



预览显示效果：

![image-20220425214727028](https://ax0kqy8quzyr.compat.objectstorage.ap-osaka-1.oraclecloud.com/bucket-blog/2022/05/image-20220425214727028.png)



## 字段类型

有很多内置的字段类型，对应不同的内容展现方式，下面一一说明。

### border

边框粗细、线性、颜色

![1649133008802](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/44e0f5eda4759728dd7443a96cd70f95.png)

### spacing

上下左右空白

![1649132962301](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/58e7fee2d6fa4289874eca3d5215b3f5.png)

### dimensions

尺寸

![1649133112228](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/556c57abb146d39b4f24f799b1d99e2b.png)

### checkbox

复选框


![1649133502003](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/29b75d6956071d7c4e56fcb6eb68d8e6.png)

```php
array(
    'id'    => 'header_sticky',
    'type'  => 'checkbox',
    'title' => '显示设置',
    'label' => '在手机端开启',
)
```

### radio

单选框

![1649133737075](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/d3740a2f040318a0ea8015955f97ac1b.png)

```php
array(
    'id'     => 'icon3',
    'type'   => 'radio',
    'title'  => '显示设置',
    'label'   => '在手机端开启',
    'inline'  => true,
    'options' => array(
        'left'  => '靠左',
        'right' => '靠右',
    ),
    'default'    => 'right',
)
```

### code_editor

代码编辑框

![1649133985979](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/70e9e057fdd83f74ccd37ff1a86e6924.png)

### color

调色板

![1649134021235](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/752b359f2d513d8e89718aba26e9354b.png)

### color_group

渐变色板

![1649134071782](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/61cb26d8a1b50a0a472eac1756bc5884.png)

### date

日期

![1649134214226](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/f19ac649f184274c0b4e9db314630756.png)

### gallery

相册

### ![1649134166460](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/1719981f4a88abfedfdeaae390ea27a9.png)
### icon

font-awesome

![1649134338052](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/8d3f58a85f96a7f5ed400631a463230a.png)

### image_select

图片选择

![1649134457868](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/702a628e7dcb0b900b9206f13cb3f9d4.png)

```php
array(
    'id'     => 'icon1',
    'type'   => 'image_select',
    'title' => '文章页样式',
    'options' => array(
        '1'   => get_stylesheet_directory_uri() . '/static/images/admin/single-1.png',
        '2'   => get_stylesheet_directory_uri() . '/static/images/admin/single-2.png',
        ),
    'default'   => '1',
    'radio'     => true,
    'attributes'   => array(
        'data-depend-id' => 'post_layout',
        ),
)
```

### link_color

超链接颜色(普通色、悬浮色)

![1649134568146](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/71a53dd60860e419e123154525e51d8e.png)

### map

地图

![1649134638694](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/01e01c0d78c37ec011e56bb9516a2b37.png)

### media

媒体

![1649134761456](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/a25d50d4d867786e38bb909b394a10e6.png)

### select

![1649134961164](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/11783e036fedc99c73495e10a66d5857.png)

```php
array(
    'id'     => 'icon3',
    'type'    => 'select',
    'title'   => '选择颜色',
    'options' => array(
        '#dd3333' => '红色',
        '#eeee22' => '黄色',
        '#81d742' => '绿色',
        '#1e73be' => '蓝色',
        '#8224e3' => '紫色',
    ),
    'default' => '#dd3333',
)
```

### slider

滑框

![1649135069025](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/59d1a09ed6d3dc34d840ed2713b74bde.png)

### switcher

开关

![1649135269132](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/4dea028b5c33bb0beaaeeeede6480666.png)

### tabbed

标签页

![1649135611290](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/0421e16d2716a06ab6841a860bc0a8ae.png)

```php
array(
	'id'     => 'icon1',
	'type'  => 'tabbed',
	'title' => '页脚模块设置',
	'tabs'  => array(
		array(
			'title'  => '关于我们',
			'fields' => array(
				array(
					'id'        => 'footer_3_about_title',
					'type'      => 'text',
					'title'     => '标题',
					'attributes'=> array('style'=> 'width: 100%;'),
				),
				array(
					'id'        => 'footer_3_about_desc',
					'type'      => 'textarea',
					'title'     => '描述',
					'attributes'=> array('style'=> 'width: 100%;'),
					'after'     => '如需换行，请使用 br 标签...',
				),
			),
		),
		array(
			'title'  => '快捷导航',
			'fields' => array(
				array(
					'id'        => 'footer_3_menu_title',
					'type'      => 'text',
					'title'     => '标题',
					'attributes'=> array('style'=> 'width: 100%;'),
				),
			),
		),
	),
)
```



### text

文本框

![1649135299066](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/970062bf12d164094cb7a47aaa51178d.png)

### textarea

富文本框

![1649135318648](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/29765229f21404484cbe88419fb78d13.png)

### upload

上传文件

![1649136104227](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/f5d1b5dbd66b88d61152c0a43e7550be.png)

### heading

### subheading

标题

![1649136166665](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/431cae98a084ad26684a146455d3e42c.png)

### notice

![1649136586927](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/198d4973a90ddd30de8dfdaf094baf5d.png)

```php
array(
	'id'     => 'icon',
	'type'  => 'notice',
	'style' => 'info',
	'content'  => 'style == info',
),
array(
	'id'    => 'icon1',
	'type'  => 'notice',
	'style' => 'success',
	'content'  => 'style == success',
),
array(
	'id'    => 'icon2',
	'type'  => 'notice',
	'style' => 'warning',
	'content'  => 'style == warning',
),
array(
	'id'     => 'icon3',
	'type'  => 'notice',
	'style' => 'danger',
	'content'  => 'style == danger',
)
```



### number

![1649136386910](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/f50e8060fb211f76699e4c8eaa366d82.png)



```
.$syntax_language.
```

