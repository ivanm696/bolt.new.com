ww.bolt.new@gmail.ccom
🔌 Примеры интеграции Bolt.new и WebContainer
Полные подключения WebContainer к твоему Bolt.new

📦 Вариант 1: Базовое подключение WebContainer
html<!DOCTYPE html>
<html>
<head>
    <title>Bolt with WebContainer</title>
    <script src="https://webcontainers.io/api"></script>
</head>
<body>

<div id="editor"></div>
<div id="preview"></div>

<script>
    import { WebContainer } from '@webcontainers/api';

    let webcontainerInstance;

    async function initContainer() {
        // Инициализируй WebContainer
        webcontainerInstance = await WebContainer.boot();
        console.log('WebContainer started!');
    }

    async function runCode(htmlCode, cssCode, jsCode) {
        // Создай файлы
        await webcontainerInstance.fs.mkdir('app', { recursive: true });
        
        await webcontainerInstance.fs.writeFile(
            'app/index.html',
            htmlCode
        );

        if (cssCode) {
            await webcontainerInstance.fs.writeFile(
                'app/style.css',
                cssCode
            );
        }

        if (jsCode) {
            await webcontainerInstance.fs.writeFile(
                'app/script.js',
                jsCode
            );
        }

        // Запусти простой HTTP сервер
        const process = await webcontainerInstance.spawn('npx', [
            'http-server',
            'app',
            '-p', '3000',
            '-o'
        ]);

        console.log('Server running on port 3000');
    }

    // Инициализация при загрузке
    window.addEventListener('load', initContainer);
</script>

</body>
</html>

🎯 Вариант 2: Полная интеграция с Bolt.new
Добавьте этот код в bolt-full-integration.htmlфункцию sendPrompt():
javascript// Добавь в начало файла
let webcontainerInstance = null;

// Инициализируй WebContainer при загрузке
async function initWebContainer() {
    try {
        const { WebContainer } = await import('@webcontainers/api');
        webcontainerInstance = await WebContainer.boot();
        console.log('✅ WebContainer initialized');
        updateAPIStatus(); // Обнови статус
    } catch (error) {
        console.error('❌ WebContainer error:', error);
    }
}

// Вызови при загрузке страницы
document.addEventListener('DOMContentLoaded', async () => {
    // ... существующий код ...
    await initWebContainer();
});

// Модифицируй sendPrompt() функцию:
async function sendPrompt() {
    const input = document.getElementById('prompt-input');
    const prompt = input.value.trim();

    if (!prompt) return;
    if (!config.apiKey) {
        showMessage('⚠️ Please add your API key in Settings', 'error');
        navigateTo('settings');
        return;
    }

    showMessage('🔄 Processing your request...', 'info');
    input.value = '';

    try {
        // Получи код от AI
        const aiCode = await callAI(prompt);
        
        // Выполни в WebContainer
        if (webcontainerInstance) {
            await executeInWebContainer(aiCode);
            showMessage('✅ Code executed in WebContainer!', 'success');
        } else {
            showMessage('⚠️ WebContainer not available', 'error');
        }
        
        console.log('AI Response:', aiCode);
    } catch (error) {
        showMessage('❌ Error: ' + error.message, 'error');
    }
}

// Добавь функцию для выполнения кода
async function executeInWebContainer(aiCode) {
    // Парси код (предполагай что AI вернул HTML)
    const { html, css, js } = extractCode(aiCode);

    // Создай структуру
    await webcontainerInstance.fs.mkdir('app', { recursive: true });

    // Напиши HTML файл
    const htmlContent = html || '<h1>Hello from Bolt.new</h1>';
    await webcontainerInstance.fs.writeFile('app/index.html', htmlContent);

    // Напиши CSS если есть
    if (css) {
        await webcontainerInstance.fs.writeFile('app/style.css', css);
    }

    // Напиши JS если есть
    if (js) {
        await webcontainerInstance.fs.writeFile('app/script.js', js);
    }

    // Запусти сервер
    await startServer();

    // Отобрази в iframe
    displayPreview();
}

// Функция для парсинга кода от AI
function extractCode(aiResponse) {
    // Ищи HTML блоки
    const htmlMatch = aiResponse.match(/<html[\s\S]*?<\/html>/i) ||
                      aiResponse.match(/<body[\s\S]*?<\/body>/i) ||
                      aiResponse.match(/<div[\s\S]*?<\/div>/i);
    
    const cssMatch = aiResponse.match(/<style[\s\S]*?<\/style>/i);
    const jsMatch = aiResponse.match(/<script[\s\S]*?<\/script>/i);

    let html = htmlMatch ? htmlMatch[0] : '';
    let css = cssMatch ? cssMatch[0].replace(/<\/?style[^>]*>/g, '') : '';
    let js = jsMatch ? jsMatch[0].replace(/<\/?script[^>]*>/g, '') : '';

    return { html, css, js };
}

// Запусти HTTP сервер
let serverProcess = null;

async function startServer() {
    // Останови старый процесс если есть
    if (serverProcess) {
        serverProcess.kill();
    }

    // Запусти новый
    serverProcess = await webcontainerInstance.spawn('npx', [
        'http-server',
        'app',
        '-p', '3000',
        '-c-1'
    ]);

    console.log('Server started on port 3000');
}

// Отобрази в iframe
function displayPreview() {
    let iframe = document.getElementById('preview-frame');
    
    if (!iframe) {
        iframe = document.createElement('iframe');
        iframe.id = 'preview-frame';
        iframe.style.cssText = `
            width: 100%;
            height: 500px;
            border: 1px solid #ccc;
            border-radius: 8px;
            margin-top: 20px;
        `;
        document.querySelector('.hero-section').appendChild(iframe);
    }

    // Жди пока сервер запустится
    setTimeout(() => {
        iframe.src = 'http://localhost:3000';
    }, 1000);
}

🎨 Вариант 3: С предпросмотром рядом
html<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; height: 600px;">
    <!-- Editor -->
    <div>
        <h3>Code Editor</h3>
        <textarea id="code-input" style="width: 100%; height: 100%; font-family: monospace;"></textarea>
    </div>

    <!-- Preview -->
    <div>
        <h3>Preview</h3>
        <iframe id="preview" style="width: 100%; height: 100%; border: 1px solid #ccc;"></iframe>
    </div>
</div>

<script>
    // Обнови preview при изменении кода
    document.getElementById('code-input').addEventListener('input', (e) => {
        const code = e.target.value;
        const iframe = document.getElementById('preview');
        
        // Используй Blob для безопасного выполнения
        const blob = new Blob([code], { type: 'text/html' });
        iframe.src = URL.createObjectURL(blob);
    });
</script>

🔄 Вариант 4: С сохранением файлов
javascript// Функция для сохранения проекта
async function saveProject(projectName) {
    const project = {
        name: projectName,
        files: {
            'index.html': await webcontainerInstance.fs.readFile('app/index.html', 'utf-8'),
            'style.css': await webcontainerInstance.fs.readFile('app/style.css', 'utf-8').catch(() => ''),
            'script.js': await webcontainerInstance.fs.readFile('app/script.js', 'utf-8').catch(() => ''),
        },
        timestamp: new Date().toISOString()
    };

    // Сохрани в localStorage
    localStorage.setItem('project_' + projectName, JSON.stringify(project));
    console.log('Project saved:', projectName);
}

// Функция для загрузки проекта
async function loadProject(projectName) {
    const project = JSON.parse(localStorage.getItem('project_' + projectName));
    
    if (!project) {
        console.error('Project not found');
        return;
    }

    // Напиши файлы
    for (const [filename, content] of Object.entries(project.files)) {
        if (content) {
            await webcontainerInstance.fs.writeFile('app/' + filename, content);
        }
    }

    // Перезагрузи
    displayPreview();
    console.log('Project loaded:', projectName);
}

// Функция для экспорта проекта
function exportProject(projectName) {
    const project = JSON.parse(localStorage.getItem('project_' + projectName));
    const dataStr = JSON.stringify(project, null, 2);
    
    // Скачай как JSON
    const dataBlob = new Blob([dataStr], { type: 'application/json' });
    const url = URL.createObjectURL(dataBlob);
    const link = document.createElement('a');
    link.href = url;
    link.download = projectName + '.json';
    link.click();
}

📊 Вариант 5: С управлением файлами
javascriptclass ProjectManager {
    constructor() {
        this.projects = new Map();
    }

    async createFile(path, content) {
        const dirs = path.split('/').slice(0, -1);
        let currentPath = '';
        
        for (const dir of dirs) {
            currentPath += dir + '/';
            await webcontainerInstance.fs.mkdir(currentPath, { recursive: true });
        }
        
        await webcontainerInstance.fs.writeFile(path, content);
    }

    async readFile(path) {
        return await webcontainerInstance.fs.readFile(path, 'utf-8');
    }

    async listFiles(path = '/') {
        const files = await webcontainerInstance.fs.readdir(path);
        return files;
    }

    async deleteFile(path) {
        await webcontainerInstance.fs.rm(path);
    }

    async renameFile(oldPath, newPath) {
        const content = await this.readFile(oldPath);
        await this.deleteFile(oldPath);
        await this.createFile(newPath, content);
    }

    async importProject(zipFile) {
        // Implement ZIP extraction
    }

    async exportProject(path) {
        // Implement ZIP creation
    }
}

const projectManager = new ProjectManager();

// Использование
await projectManager.createFile('app/index.html', '<h1>Hello</h1>');
await projectManager.createFile('app/style.css', 'h1 { color: blue; }');

🚀 Вариант 6: С установкой зависимостей
javascriptasync function installDependencies(packages) {
    showMessage('📦 Installing dependencies...', 'info');

    // Сначала инициализируй npm
    await webcontainerInstance.spawn('npm', ['init', '-y']);

    // Затем установи пакеты
    for (const pkg of packages) {
        console.log(`Installing ${pkg}...`);
        const process = await webcontainerInstance.spawn('npm', ['install', pkg]);
        
        process.output.pipeTo(new WritableStream({
            write(chunk) {
                console.log(chunk);
            }
        }));
    }

    showMessage('✅ Dependencies installed!', 'success');
}

// Использование
await installDependencies(['react', 'react-dom', 'axios']);

🌐 Вариант 7: С живой перезагрузкой
javascriptasync function setupLiveReload() {
    // Используй chokidar для отслеживания файлов
    const watchProcess = await webcontainerInstance.spawn('npx', [
        'chokidar',
        'app/**/*',
        '-c',
        'echo "File changed"'
    ]);

    watchProcess.output.pipeTo(new WritableStream({
        write(chunk) {
            console.log('File changed, reloading...');
            // Перезагрузи iframe
            document.getElementById('preview').src = document.getElementById('preview').src;
        }
    }));
}

🔗 Вариант 8: С подключением Cloudflare Workers
javascriptasync function deployToCloudflare(projectName) {
    // Инициализируй Wrangler
    await webcontainerInstance.spawn('npm', ['init', '-y']);
    await webcontainerInstance.spawn('npm', ['install', '-D', 'wrangler']);

    // Создай wrangler.toml
    const wranglerConfig = `
name = "${projectName}"
main = "src/index.ts"
compatibility_date = "2024-01-01"

[env.production]
routes = [
  { pattern = "yoursite.com/*", zone_name = "yoursite.com" }
]
`;

    await webcontainerInstance.fs.writeFile('wrangler.toml', wranglerConfig);

    // Деплой
    const deployProcess = await webcontainerInstance.spawn('npx', [
        'wrangler',
        'deploy'
    ]);

    console.log('Deploying to Cloudflare...');
}

📝 Полный пример в одном файле
javascriptclass BoltWebContainerIntegration {
    constructor() {
        this.container = null;
        this.serverProcess = null;
        this.projects = new Map();
    }

    // Инициализация
    async init() {
        const { WebContainer } = await import('@webcontainers/api');
        this.container = await WebContainer.boot();
        console.log('✅ WebContainer ready');
    }

    // Запуск кода
    async runCode(html, css = '', js = '') {
        await this.container.fs.mkdir('app', { recursive: true });
        await this.container.fs.writeFile('app/index.html', this.buildHTML(html, css, js));

        if (css) {
            await this.container.fs.writeFile('app/style.css', css);
        }

        if (js) {
            await this.container.fs.writeFile('app/script.js', js);
        }

        await this.startServer();
    }

    buildHTML(html, css, js) {
        return `
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bolt Preview</title>
    <style>${css}</style>
</head>
<body>
    ${html}
    <script>${js}</script>
</body>
</html>
        `;
    }

    async startServer() {
        if (this.serverProcess) this.serverProcess.kill();
        this.serverProcess = await this.container.spawn('npx', [
            'http-server', 'app', '-p', '3000', '-c-1'
        ]);
    }

    async saveProject(name, html, css, js) {
        this.projects.set(name, { html, css, js, timestamp: Date.now() });
        localStorage.setItem('bolt_projects', JSON.stringify(Array.from(this.projects.entries())));
    }

    loadProject(name) {
        return this.projects.get(name);
    }

    listProjects() {
        return Array.from(this.projects.keys());
    }
}

// Использование
const bolt = new BoltWebContainerIntegration();
await bolt.init();
await bolt.runCode('<h1>Hello World</h1>', 'h1 { color: blue; }', '');

🐛 Решение частных проблем
Ошибка CORS
javascript// Используй CORS proxy для API запросов
const corsProxy = 'https://cors-anywhere.herokuapp.com/';
Вебконтейнер не загружается
javascript// Проверь интернет и браузер поддерживает SharedArrayBuffer
if (!window.SharedArrayBuffer) {
    console.error('SharedArrayBuffer not supported');
}
3000 лелей
javascript// Используй другой порт
await spawn('http-server', ['app', '-p', '3001']);

📚 ность рост

API веб-контейнера:  https://webcontainers.io/api.
NPM в WebContainer:  https://webcontainers.io/guides/nodejs
Файловая система:  https://webcontainers.io/guides/filesystem.


Выбери нужный вариант и добавь в свой Bolt.new! 🚀
