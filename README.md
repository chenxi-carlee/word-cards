# 我的单词卡

一个自己做的背单词网站，参考了 Quizlet，另外加上了按记忆曲线复习的功能。整个网站只有一个 HTML 文件，不需要服务器，也不用注册账号。

## 功能

- **复习**：用简化版的 SM-2 记忆曲线算法安排复习。每个词按“忘了 / 模糊 / 记得 / 很熟”打分，记得越牢，下次出现隔得越久。每天最多学 15 个新词，页面上还能看到未来 7 天每天要复习多少词。
- **卡片**：点击翻面，可以标记“认识了 / 还在学”、打乱顺序，还能用浏览器朗读单词。
- **测验**：四选一的选择题，英译中、中译英都行，做完可以只练错题。
- **词表**：查看、编辑、删除单词，可以按词组和掌握情况筛选。
- **添加**：一次加一个词，也可以批量粘贴（一行一个，用 Tab、` - ` 或逗号隔开，从 Quizlet 导出的格式也能直接粘贴）。
- **备份**：导出、导入 JSON 备份文件，方便换设备。

快捷键：复习时按空格看答案，按 `1` `2` `3` `4` 打分；翻卡片时按空格翻面，按 ← → 切换上一个、下一个。

## 本地使用

直接用浏览器打开 `index.html` 就能用。

## 用 GitHub Pages 发布

1. 在 GitHub 上新建一个仓库，比如叫 `word-cards`。
2. 把这个文件夹里的文件推上去：
   ```bash
   git remote add origin https://github.com/<你的用户名>/word-cards.git
   git branch -M main
   git push -u origin main
   ```
3. 打开仓库的 **Settings → Pages**，在 “Build and deployment” 下把 Source 选成 “Deploy from a branch”，分支选 `main`，文件夹选 `/ (root)`，然后保存。
4. 等一两分钟，网站就会出现在 `https://<你的用户名>.github.io/word-cards/`。

## 数据存在哪里

单词和复习进度都存在浏览器的 `localStorage` 里，只有你自己的这个浏览器能看到。所以要注意：

- 换电脑或换浏览器后，旧的单词不会跟过来。请先在旧浏览器里点“添加 → 导出备份”，到新浏览器里再点“导入备份”。
- 清理浏览器数据或者用无痕模式，都会让单词丢失，记得定期导出备份。

## 示例词表

`data/sample-words.js` 里放着《Invisible Women》（Caroline Criado Perez 著）第一章的 49 个词汇和书中例句。词库为空时，点“载入示例词表”就能导入。想换成自己的词组，照着这个文件的格式改就行：

```js
window.SAMPLE_SETS = [
  {
    "set": "词组名称",
    "words": [
      { "term": "laudable", "meaning": "值得称赞的", "example": "书里的原句（可选）" }
    ]
  }
];
```

`data/sample-words.json` 是同一份词表的 JSON 版本，可以直接用“导入备份”导入。

## 文件结构

```
index.html              整个网站（HTML、CSS、JS 都在这一个文件里）
data/sample-words.js    示例词表，页面启动时会加载
data/sample-words.json  同一份词表的 JSON 格式
```

## 许可证

MIT
