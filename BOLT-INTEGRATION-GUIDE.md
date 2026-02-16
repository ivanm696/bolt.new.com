# 馃殌 Bolt.new Full Integration Guide

**袩芯谢薪褘泄 谢芯泻邪谢褜薪褘泄 AI builder 褋 褋懈薪褟褟 懈薪褌械褉褎械泄褋芯屑 Dashboard + Builder**

---

## 馃搵 效褌芯 胁薪褍褌褉懈?

鉁� **Dashboard** - 褋懈薪褟褟 锌邪薪械谢褜 褍锌褉邪胁谢械薪懈褟 (泻邪泻 褍 褌械斜褟)
鉁� **Builder** - 谐谢邪胁薪邪褟 褋褌褉邪薪懈褑邪 褋 锌褉芯屑锌褌芯屑 写谢褟 AI ("What will you build today?")
鉁� **Settings** - 褍锌褉邪胁谢械薪懈械 API 泻谢褞褔邪屑懈 懈 LLM
鉁� **AI 懈薪褌械谐褉邪褑懈褟** - 锌芯写写械褉卸泻邪 Claude, OpenAI, Groq
鉁� **袥芯泻邪谢褜薪芯械 褏褉邪薪懈谢懈褖械** - 胁褋械 写邪薪薪褘械 胁 斜褉邪褍蟹械褉械
鉁� **袦芯斜懈谢褜薪褘泄 写懈蟹邪泄薪** - 褉邪斜芯褌邪械褌 薪邪 谢褞斜芯屑 褍褋褌褉芯泄褋褌胁械

---

## 馃幆 袘褘褋褌褉褘泄 褋褌邪褉褌

### 1锔忊儯 袨褌泻褉芯泄褌械 褎邪泄谢 胁 斜褉邪褍蟹械褉械

```bash
# 袩褉芯褋褌芯 芯褌泻褉芯泄 bolt-full-integration.html 胁 斜褉邪褍蟹械褉械
# 袠谢懈 蟹邪锌褍褋褌懈 谢芯泻邪谢褜薪褘泄 褋械褉胁械褉:

python -m http.server 8000
# 袟邪褌械屑 锌械褉械泄写懈 薪邪 http://localhost:8000
```

### 2锔忊儯 袛芯斜邪胁褜褌械 API 泻谢褞褔

1. 袧邪卸屑懈 薪邪 胁泻谢邪写泻褍 **Settings** 鈿欙笍
2. 袙褘斜械褉懈 AI 锌褉芯胁邪泄写械褉邪:
   - **Claude** (Anthropic) - 褉械泻芯屑械薪写褍械褌褋褟
   - **OpenAI** (ChatGPT)
   - **Groq** (斜褘褋褌褉褘泄)
3. 袙褋褌邪胁褜 褋胁芯泄 API 泻谢褞褔
4. 袧邪卸屑懈 **Test Connection**

### 3锔忊儯 小芯蟹写邪胁邪泄 锌褉懈谢芯卸械薪懈褟!

1. 袩械褉械泄写懈 薪邪 **Builder** 
2. 袧邪锌懈褕懈 蟹邪锌褉芯褋: "Create a simple todo app"
3. 袞写懈 芯褌胁械褌邪 芯褌 AI
4. 袣芯写 锌芯褟胁懈褌褋褟 胁 泻芯薪褋芯谢懈 (谐芯褌芯胁芯 写谢褟 WebContainer)

---

## 馃攽 袚写械 锌芯谢褍褔懈褌褜 API 泻谢褞褔懈?

### Claude (Anthropic) 猸� 袪械泻芯屑械薪写褍械褌褋褟
- 小邪泄褌: https://console.anthropic.com/
- 袣谢褞褔 薪邪褔懈薪邪械褌褋褟 褋 `sk-ant-`
- 袘械褋锌谢邪褌薪褘泄 锌谢邪薪: $5 屑械褋褟褔薪褘泄 泻褉械写懈褌
- 袣邪褔械褋褌胁芯 泻芯写邪: 猸愨瓙猸愨瓙猸�

```
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxx
```

### OpenAI
- 小邪泄褌: https://platform.openai.com/api-keys
- 袣谢褞褔 薪邪褔懈薪邪械褌褋褟 褋 `sk-`
- 袘械褋锌谢邪褌薪褘泄 锌谢邪薪: $5 屑械褋褟褔薪褘泄 泻褉械写懈褌
- 袣邪褔械褋褌胁芯 泻芯写邪: 猸愨瓙猸愨瓙

```
OPENAI_API_KEY=sk-xxxxxxxxxxxxx
```

### Groq (袘褘褋褌褉芯 & 斜械褋锌谢邪褌薪芯)
- 小邪泄褌: https://console.groq.com/
- 袘械褋锌谢邪褌薪褘泄 锌谢邪薪: 斜械蟹 芯谐褉邪薪懈褔械薪懈泄!
- 袣邪褔械褋褌胁芯 泻芯写邪: 猸愨瓙猸�

```
GROQ_API_KEY=gsk_xxxxxxxxxxxxx
```

---

## 馃帹 袠薪褌械褉褎械泄褋

### Sidebar (褋谢械胁邪)
- 馃搳 **Dashboard** - 锌邪薪械谢褜 褍锌褉邪胁谢械薪懈褟
- 馃彔 **Builder** - 褋芯蟹写邪薪懈械 锌褉懈谢芯卸械薪懈泄
- 鈿欙笍 **Settings** - 泻芯薪褎懈谐褍褉邪褑懈褟

### Header (胁胁械褉褏褍)
- 袧邪蟹胁邪薪懈械 褌械泻褍褖械泄 褋褌褉邪薪懈褑褘
- 袦械薪褞 写谢褟 屑芯斜懈谢褜薪褘褏

### Content (芯褋薪芯胁薪邪褟 芯斜谢邪褋褌褜)
- 袟邪胁懈褋懈褌 芯褌 胁褘斜褉邪薪薪芯泄 褋褌褉邪薪懈褑褘

---

## 馃捑 袣邪泻 褉邪斜芯褌邪械褌 褏褉邪薪懈谢懈褖械?

### LocalStorage
```javascript
// API 泻谢褞褔 (褋芯褏褉邪薪褟械褌褋褟)
localStorage.setItem('apiKey', 'sk-ant-...');

// 袩褉芯胁邪泄写械褉
localStorage.setItem('aiProvider', 'claude');

// 袦芯写械谢褜
localStorage.setItem('model', 'claude-3-5-sonnet');

// 袦邪泻褋懈屑褍屑 褌芯泻械薪芯胁
localStorage.setItem('maxTokens', '4096');
```

### 袘械蟹芯锌邪褋薪芯褋褌褜
鉁� 袣谢褞褔懈 褋芯褏褉邪薪褟褞褌褋褟 褌芯谢褜泻芯 谢芯泻邪谢褜薪芯 胁 斜褉邪褍蟹械褉械
鉁� 袧械 芯褌锌褉邪胁谢褟褞褌褋褟 薪邪 褋械褉胁械褉
鉁� 袩褉懈 芯褔懈褋褌泻械 斜褉邪褍蟹械褉邪 褍写邪谢褟褞褌褋褟
鉁� 袠褋锌芯谢褜蟹褍泄 HTTPS 胁 锌褉芯写邪泻褕械薪械

---

## 馃 袣邪泻 锌芯写泻谢褞褔懈褌褜 WebContainer?

### 楔邪谐 1: 袟邪谐褉褍蟹懈 WebContainer SDK

```html
<script src="https://webcontainers.io/api"></script>
```

### 楔邪谐 2: 袠薪懈褑懈邪谢懈蟹懈褉褍泄 WebContainer

```javascript
import { WebContainer } from '@webcontainers/api';

let container;

async function initWebContainer() {
    container = await WebContainer.boot();
}

initWebContainer();
```

### 楔邪谐 3: 袙褘锌芯谢薪懈 泻芯写 芯褌 AI

```javascript
async function executeAICode(code) {
    // 1. 袩芯谢褍褔懈 芯褌胁械褌 芯褌 AI
    const aiResponse = await callAI(prompt);
    
    // 2. 袪邪褋锌邪褉褋懈 泻芯写
    const { html, css, js } = parseCode(aiResponse);
    
    // 3. 袙褘锌芯谢薪懈 胁 WebContainer
    await container.fs.writeFile('/app.html', html);
    await container.fs.writeFile('/style.css', css);
    await container.fs.writeFile('/script.js', js);
    
    // 4. 袟邪锌褍褋褌懈 dev server
    const process = await container.spawn('node', [
        '-e',
        'require("http").createServer((req,res)=>res.end(fs.readFileSync("/app.html"))).listen(3000)'
    ]);
}
```

### 楔邪谐 4: 袩芯泻邪卸懈 褉械蟹褍谢褜褌邪褌

```javascript
// 袠褋锌芯谢褜蟹褍泄 iframe 写谢褟 芯褌芯斜褉邪卸械薪懈褟 褉械蟹褍谢褜褌邪褌邪
const iframe = document.createElement('iframe');
iframe.src = 'http://localhost:3000';
document.body.appendChild(iframe);
```

---

## 馃И 孝械褋褌懈褉芯胁邪薪懈械

### 孝械褋褌 1: 袩褉芯胁械褉褜 API 泻谢褞褔
1. 袩械褉械泄写懈 薪邪 Settings 鈿欙笍
2. 袧邪卸屑懈 **Test Connection**
3. 袛芯谢卸械薪 锌芯褟胁懈褌褜褋褟 鉁� 懈谢懈 鉂�

### 孝械褋褌 2: 小芯蟹写邪泄 锌褉芯褋褌芯械 锌褉懈谢芯卸械薪懈械
1. 袧邪 Builder 薪邪锌懈褕懈: "Create a hello world HTML page"
2. 袩褉芯胁械褉褜 泻芯薪褋芯谢褜 斜褉邪褍蟹械褉邪 (F12)
3. 袛芯谢卸械薪 斜褘褌褜 HTML 泻芯写

### 孝械褋褌 3: 袩褉芯胁械褉褜 褏褉邪薪懈谢懈褖械
```javascript
// 袙 泻芯薪褋芯谢懈 斜褉邪褍蟹械褉邪 (F12):
console.log(localStorage);
```

---

## 馃摫 袦芯斜懈谢褜薪邪褟 胁械褉褋懈褟

鉁� 袩芯谢薪芯褋褌褜褞 邪写邪锌褌懈胁薪邪
鉁� Sidebar 褋泻褉褘胁邪械褌褋褟 薪邪 屑芯斜懈谢褜薪褘褏
鉁� 袦械薪褞 褉邪褋泻褉褘胁邪械褌褋褟 锌褉懈 薪邪卸邪褌懈懈 鈽�
鉁� 校写芯斜薪邪褟 泻谢邪胁懈邪褌褍褉邪 薪邪 屑芯斜懈谢褜薪褘褏

---

## 馃悰 效邪褋褌褘械 锌褉芯斜谢械屑褘

### 鉂� "API Key not valid"

**袪械褕械薪懈械:**
- 袩褉芯胁械褉褜, 褔褌芯 泻谢褞褔 褋泻芯锌懈褉芯胁邪薪 锌芯谢薪芯褋褌褜褞
- 校斜械写懈褋褜, 褔褌芯 褝褌芯 薪芯胁褘泄 泻谢褞褔 (薪械 懈褋褌械泻褕懈泄)
- 袩芯锌褉芯斜褍泄 褋芯蟹写邪褌褜 薪芯胁褘泄 泻谢褞褔 薪邪 褋邪泄褌械 锌褉芯胁邪泄写械褉邪

### 鉂� "CORS error"

**协褌芯 薪芯褉屑邪谢褜薪芯!** 袘褉邪褍蟹械褉 斜谢芯泻懈褉褍械褌 蟹邪锌褉芯褋褘 泻 API.

**袪械褕械薪懈械:** 袠褋锌芯谢褜蟹褍泄 CORS proxy:
```javascript
const corsProxy = 'https://cors-anywhere.herokuapp.com/';
const apiUrl = corsProxy + 'https://api.anthropic.com/v1/messages';
```

袠谢懈 褉邪蟹胁械薪懈 薪邪 褋械褉胁械褉械 褋 锌芯写写械褉卸泻芯泄 CORS.

### 鉂� "Rate limit exceeded"

**袩褉懈褔懈薪邪:** 袨褌锌褉邪胁谢褟械褕褜 屑薪芯谐芯 蟹邪锌褉芯褋芯胁.

**袪械褕械薪懈械:**
- 袩芯写芯卸写懈 薪械褋泻芯谢褜泻芯 屑懈薪褍褌
- 袠褋锌芯谢褜蟹褍泄 Groq (薪械褌 谢懈屑懈褌芯胁)
- 袣褍锌懈 锌谢邪褌薪褘泄 锌谢邪薪 薪邪 Anthropic/OpenAI

### 鉂� Sidebar 薪械 芯褌泻褉褘胁邪械褌褋褟 薪邪 屑芯斜懈谢褜薪芯屑

**袪械褕械薪懈械:**
- 袨斜薪芯胁懈 褋褌褉邪薪懈褑褍 (F5)
- 袩褉芯胁械褉褜 褔褌芯 JavaScript 胁泻谢褞褔械薪
- 袨褔懈褋褌懈 泻械褕 斜褉邪褍蟹械褉邪

---

## 馃摎 袩褉懈屑械褉褘 锌褉芯屑锌褌芯胁

### 袩褉芯褋褌褘械 锌褉芯械泻褌褘
```
Create a simple todo app with HTML, CSS, and JavaScript
```

### Intermediate
```
Build a weather app that fetches data from an API
```

### Advanced
```
Create a real-time chat application with WebSocket support
```

### Creative
```
Make a game where you control a character with arrow keys
```

---

## 馃殌 袪邪蟹胁褢褉褌褘胁邪薪懈械

### 袧邪 Vercel
```bash
npm init -y
# 小芯蟹写邪泄 vercel.json
{
  "public": ".",
  "cleanUrls": false
}

vercel
```

### 袧邪 GitHub Pages
```bash
git add .
git commit -m "Deploy Bolt.new"
git push origin main
```

### 袧邪 褋胁芯褢屑 褋械褉胁械褉械
```bash
# 小泻芯锌懈褉褍泄 bolt-full-integration.html 薪邪 褋械褉胁械褉
scp bolt-full-integration.html user@server:/var/www/html/

# 袠褋锌芯谢褜蟹褍泄 nginx 懈谢懈 Apache 写谢褟 褉邪蟹写邪褔懈 褎邪泄谢芯胁
```

---

## 馃攼 袘械蟹芯锌邪褋薪芯褋褌褜 胁 锌褉芯写邪泻褕械薪械

### 1. 袠褋锌芯谢褜蟹褍泄 HTTPS
```
https://yoursite.com (薪械 http://)
```

### 2. 袧械 锌芯泻邪蟹褘胁邪泄 API 泻谢褞褔 胁 泻芯写械
```javascript
// 鉂� 袧袝袩袪袗袙袠袥鞋袧袨
const apiKey = 'sk-ant-xxxxx'; // 袙懈写薪芯 胁 懈褋褏芯写薪懈泻械!

// 鉁� 袩袪袗袙袠袥鞋袧袨
const apiKey = localStorage.getItem('apiKey'); // 袙胁芯写懈褌 锌芯谢褜蟹芯胁邪褌械谢褜
```

### 3. 袠褋锌芯谢褜蟹褍泄 芯泻褉褍卸械薪懈械 写谢褟 褉邪蟹褉邪斜芯褌泻懈
```bash
# .env
VITE_API_ENDPOINT=https://api.anthropic.com

# 袛芯褋褌褍锌 褔械褉械蟹 process.env
```

### 4. 袙邪谢懈写懈褉褍泄 胁褏芯写薪褘械 写邪薪薪褘械
```javascript
// 袩褉芯胁械褉褜 褔褌芯 褝褌芯 胁邪谢懈写薪褘泄 JSON 芯褌 AI
try {
    const code = JSON.parse(aiResponse);
} catch (e) {
    showError('Invalid AI response');
}
```

---

## 馃帗 效褌芯 写邪谢褜褕械?

### Level 1: 袨褋薪芯胁褘
- 鉁� 袟邪锌褍褋褌懈 谢芯泻邪谢褜薪芯
- 鉁� 袛芯斜邪胁褜 API 泻谢褞褔
- 鉁� 小芯蟹写邪泄 锌械褉胁芯械 锌褉懈谢芯卸械薪懈械

### Level 2: 袠薪褌械谐褉邪褑懈褟
- 猬� 袩芯写泻谢褞褔懈 WebContainer
- 猬� 袙褘锌芯谢薪褟泄 泻芯写 胁 斜褉邪褍蟹械褉械
- 猬� 袩芯泻邪卸懈 褉械蟹褍谢褜褌邪褌 胁 iframe

### Level 3: 袩褉芯写胁懈薪褍褌芯械
- 猬� 小芯褏褉邪薪褟泄 锌褉芯械泻褌褘 胁 袘袛
- 猬� 小芯胁屑械褋褌薪芯械 褉械写邪泻褌懈褉芯胁邪薪懈械
- 猬� 袙械褉褋懈芯薪懈褉芯胁邪薪懈械 泻芯写邪

### Level 4: Production
- 猬� 袪邪蟹胁械褉薪懈 薪邪 褋械褉胁械褉
- 猬� 袛芯斜邪胁褜 邪褍褌械薪褌懈褎懈泻邪褑懈褞
- 猬� 袠薪褌械谐褉懈褉褍泄 褋 GitHub

---

## 馃摓 袩芯屑芯褖褜

### 袛芯泻褍屑械薪褌邪褑懈褟
- Claude API: https://docs.anthropic.com/
- OpenAI API: https://platform.openai.com/docs/
- Groq API: https://console.groq.com/docs/
- WebContainer: https://webcontainers.io/

### 小芯芯斜褖械褋褌胁邪
- Reddit: r/webdev, r/learnprogramming
- Stack Overflow: tag `[bolt.new]`
- GitHub Discussions

---

## 馃挕 小芯胁械褌褘

1. **孝械褋褌懈褉褍泄 褋薪邪褔邪谢邪 谢芯泻邪谢褜薪芯** 锌械褉械写 写械锌谢芯械屑
2. **袠褋锌芯谢褜蟹褍泄 Claude** 写谢褟 谢褍褔褕械谐芯 泻邪褔械褋褌胁邪 泻芯写邪
3. **小芯褏褉邪薪褟泄 API 泻谢褞褔** 胁 斜械蟹芯锌邪褋薪芯屑 屑械褋褌械
4. **效懈褌邪泄 谢芯谐懈** 胁 泻芯薪褋芯谢懈 斜褉邪褍蟹械褉邪 (F12)
5. **袛械谢懈褋褜 褉械蟹褍谢褜褌邪褌邪屑懈** - 锌芯泻邪卸懈 写褉褍蟹褜褟屑!

---

## 馃搫 袥懈褑械薪蟹懈褟

MIT - 懈褋锌芯谢褜蟹褍泄 泻邪泻 褏芯褔械褕褜!

---

**袙械褉褋懈褟:** 1.0.0  
**小褌邪褌褍褋:** 鉁� 袚芯褌芯胁芯 泻 懈褋锌芯谢褜蟹芯胁邪薪懈褞  
**袩芯褋谢械写薪械械 芯斜薪芯胁谢械薪懈械:** 肖械胁褉邪谢褜 2026

校写邪褔懈 胁 褋芯蟹写邪薪懈懈 锌褉懈谢芯卸械薪懈泄! 馃殌
