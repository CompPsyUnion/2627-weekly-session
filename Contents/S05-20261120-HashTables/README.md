# 哈希表周常分享材料

胡桐舟的周常分享主题为“从 Git Commit 到哈希表：碰撞、拉链法与双哈希”。分享提议见 [Issue #19](https://github.com/CompPsyUnion/2627-weekly-session/issues/19)。

## 文件导航

| 文件 | 用途 |
| --- | --- |
| [hash-table-slides.html](hash-table-slides.html) | 用浏览器打开的课程幻灯片 |
| [hash-table-lecture.md](hash-table-lecture.md) | 上课投屏与课后阅读讲义，含演示、手算例题、互动题及折叠答案 |

## 课程大纲与目标

面向理解数组、循环和取模的初学者。课程通过 Git 内容寻址导入，依次讲解 Key 到桶的映射、碰撞实验、拉链法、线性探测、双哈希、装载因子与扩容，最后用 Python 演示去重、计数和缓存。

完成课程后，参与者应能手算双哈希探测序列，解释非零步长和互质条件，并区分哈希定位、Key 相等性与容器顺序语义。

## 本地预览

- 用浏览器打开 `hash-table-slides.html`，可在「碰撞实验」页调整哈希参数和桶数，观察冲突结果。
- 用 VS Code 或其他 Markdown 工具打开 `hash-table-lecture.md`。使用支持 `<details>` 的预览器可展开答案。
