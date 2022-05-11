---
title: "Debian解决Noto Sans CJK字体默认为日文字形的问题"
date: 2022-05-11
draft: false
tags: [Debian]
categories: ["notes"]
---

使用中文为默认语言时，CJK字体应为默认中文字形，因此不存在CJK字体的默认字形问题。默认语言非中文时，会出现CJK字体默认字形的问题。可以通过以下代码检查：  
执行`fc-match -s | grep 'Noto Sans CJK'`。  
返回`NotoSansCJK-Regular.ttc: "Noto Sans CJK JP" "Regular"` 则代表默认字形为日文；  
返回`NotoSansCJK-Regular.ttc: "Noto Sans CJK SC" "Regular"` 则代表默认字形为简体中文。

本方案仅为当前用户修改配置文件，以解决CJK字体默认为日文字形的问题。

新建`~/.config/fontconfig/conf.d`文件夹，在文件夹内新建`64-language-selector-prefer.conf`文件，并在`~/.config/fontconfig/conf.d/64-language-selector-prefer.conf`添加如下内容，相上关代码如下。

```
mkdir -p ~/.config/fontconfig/conf.d

vi ~/.config/fontconfig/conf.d/64-language-selector-prefer.conf
```

```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Noto Sans CJK SC</family>
			<family>Noto Sans CJK TC</family>
			<family>Noto Sans CJK JP</family>
                        <family>Noto Sans CJK KR</family>
		</prefer>
	</alias>
	<alias>
		<family>serif</family>
		<prefer>
			<family>Noto Serif CJK SC</family>
			<family>Noto Serif CJK TC</family>
			<family>Noto Serif CJK JP</family>
                        <family>Noto Serif CJK KR</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Noto Sans Mono CJK SC</family>
			<family>Noto Sans Mono CJK TC</family>
			<family>Noto Sans Mono CJK JP</family>
                        <family>Noto Sans Mono CJK KR</family>
		</prefer>
	</alias>
</fontconfig>
```

执行`fc-cache -fv`更新字体缓存，执行`fc-match -s | grep 'Noto Sans CJK'`，返回`NotoSansCJK-Regular.ttc: "Noto Sans CJK SC" "Regular"` 则表示设置成功。


## 参考：
[修正简体中文显示为异体（日文）字形](https://wiki.archlinux.org/title/Localization_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)/Simplified_Chinese_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)#%E4%BF%AE%E6%AD%A3%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87%E6%98%BE%E7%A4%BA%E4%B8%BA%E5%BC%82%E4%BD%93%EF%BC%88%E6%97%A5%E6%96%87%EF%BC%89%E5%AD%97%E5%BD%A2)