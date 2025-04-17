# Hugo Theme Cybe👾

A card-style hugo theme based on [stack](https://github.com/CaiJimmy/hugo-theme-stack).

一个基于stack主题的卡片风格Hugo主题

示例：[blog.fiveth.cc](https://blog.fiveth.cc/)

![image](https://github.com/user-attachments/assets/9a9f3694-3590-4b3b-b23a-8582d6d18406)

# Documentation

## 安装
1.删掉默认的配置文件`config.toml`

2.在`blog`根目录打开终端输入以下命令
```bash
git init
#获取主题文件
git submodule add https://github.com/kmeykranz/hugo-theme-cybe/ themes/hugo-theme-cybe
```

3.将获取到的主题文件中的`exampleSite`中的所有文件拷贝到`blog`根目录

4.打开`hugo.yaml`根据自己需要进行配置
## 自定义头像
1. 打开主题文件中的`\assets\img`文件夹
2. 把里面的avatar.png换成你的头像
## 自定义主页侧边栏名片
1. （用任意编辑器）打开主题文件中的`\layouts\partials\widget\author.html`
2. 在里面自行修改对应文字和链接即可

## 自定义”关于“页面
1. 打开主题文件中的`\layouts\page\about.html`
2. 往下划就会找到这段代码，更换里面的文字和链接就可以了
```html
    <!-- ---------在这里自定义关于页面--------- -->
    <!-- 卡片容器 -->
    <div class="author-page-content">
        <!-- 卡片 1：关于我 -->
        ...
        <!-- 卡片 2：我的人格 -->
        ...
        <!-- 卡片 3：我的爱好 -->
        ...
        <!-- 卡片 4：座右铭 -->
        ...
        <!-- 卡片 5：我的技能 -->
        <!-- 技能图标可以从这个网站获取 https://shields.io/ -->
        ...
        <!-- 卡片 6：与我联系 -->
        ...
    <div>
    <!-- ---------在上面自定义关于页面--------- -->
```

## 主页头图文字修改
在主题文件中打开`layouts\index.html`修改

## 自定义页脚
在主题文件中打开`layouts\partials\footer\custom.html`修改

## 其余设置
其余设置请参考原主题文档进行配置 https://stack.jimmycai.com/
