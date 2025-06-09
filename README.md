# Doxi-owo

目前暂时只是一个用于索引 [V2ex Better Comment]() 油猴脚本中 表情配置的 `列表仓库`。

> 基于这个配置实现自定义表情，默认配置见 doxi-owo-template.json

## 公共配置列表

[https://gist.github.com/search?q=filename:doxi-owo](https://gist.github.com/search?q=filename:doxi-owo)

如果要分享你的表情配置，需要上传到 Github 的 [gist](https://gist.github.com/) 中，并以 `doxi-owo-` 为前缀命名文件，如 `doxi-owo-dogxi.json`，`doxi-owo-v2ex-dogxi.json`等。

**上传 gist 默认是私密的，需要手动点击 `make public`！**

> 这里也十分推荐用这个方式备份配置 =w=

> [!NOTE]
>
> 如果担心图片用的 url 会被别人删除，可以批量下载后上传修改为自己的图床。
>
> (后面会编写脚本给大家快速转换的)

## 基础格式

```json
{
  "分类名1": {
    "type": "text", // 纯文本表情（颜文字、ASCII艺术等）
    "author": "匿名", // 可选参数：如有版权可著名
    "container": [
      { "icon": "٩(ˊᗜˋ*)و", "text": "开心" }, // text 可选：注释
      { "icon": "(/ω＼)", "text": "害羞" }
    ]
  },
  "分类名2": {
    "type": "emoji", // Unicode 表情符号
    "container": [
      { "icon": "😭", "text": "哭泣" },
      { "icon": "😛", "text": "吐舌" }
    ]
  },
  "分类名3": {
    "type": "image", // 图片表情
    "container": [
      {
        "icon": "https://i.imgur.com/2by85Ui.jpeg",
        "text": "小冒蜜",
        "width": 100, // 可选：图片宽度
        "height": 100 // 可选：图片高度
      }
    ]
  },
  "分类名4": {
    "type": "sticker", // 动态贴纸
    "container": [
      {
        "icon": "https://i.imgur.com/6W0VDcT.gif",
        "text": "猫脸蹭墙",
        "animated": true,
        "width": 80,
        "height": 80
      }
    ]
  }
  //...
}
```

## 格式要求

### 1. 基础规则

- 分类名不能重复
- 每个分类必须包含 `type` 和 `container` 字段
- `container` 数组中每个表情必须包含 `icon` 字段
- `text` 字段为可选，用于描述表情含义

### 2. 支持的类型

| 类型      | 说明                           | icon 格式        | 额外字段                      |
| --------- | ------------------------------ | ---------------- | ----------------------------- |
| `text`    | 纯文本表情、颜文字、ASCII 艺术 | 纯文本字符串     | 无                            |
| `emoji`   | Unicode 表情符号               | Unicode 表情字符 | 无                            |
| `image`   | 静态图片表情                   | 图片 URL         | `width`, `height`             |
| `sticker` | 动态贴纸/GIF                   | 图片/GIF URL     | `animated`, `width`, `height` |

> 有动图推荐使用 sticker 分类

### 3. 字段说明

#### 必需字段

- `type`: 表情类型，见上表
- `icon`: 表情内容，格式根据类型而定
- `container`: 表情数组

#### 可选字段

- `author`: 著名作者或版权
- `text`: 表情描述/注释
- `width`: 图片宽度（仅限 image/sticker 类型）
- `height`: 图片高度（仅限 image/sticker 类型）
- `animated`: 是否为动画（仅限 sticker 类型）

> 这里的高度和宽度为展示参数 需要上层应用进行适配。

### 4. 命名规范

- 表情描述尽量简短，便于用户理解
- 图片 URL 建议使用 HTTPS 协议
- 如果为 v2ex 使用需要上传 imgur 图床

---

项目灵感来自于：[DIYgod/OwO](https://github.com/DIYgod/OwO)
（有部分配置出入）
