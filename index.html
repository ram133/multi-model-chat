...<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Multi-AI via OpenRouter</title>
<style>
body {
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
max-width: 900px;
margin: 0 auto;
padding: 16px;
background: #f8f9fa;
color: #222;
}
h1 {
font-size: 1.4rem;
margin-bottom: 12px;
}
label {
display: block;
margin: 10px 0 4px;
font-weight: 600;
}
input[type="password"],
textarea {
width: 100%;
padding: 10px;
font-size: 15px;
border: 1px solid #ccc;
border-radius: 6px;
box-sizing: border-box;
}
textarea {
height: 100px;
resize: vertical;
}
.models {
display: flex;
flex-wrap: wrap;
gap: 10px 18px;
margin: 12px 0 16px;
}
.models label {
font-weight: normal;
display: flex;
align-items: center;
gap: 6px;
margin: 0;
}
button {
background: #2563eb;
color: white;
border: none;
padding: 12px 20px;
font-size: 15px;
border-radius: 6px;
cursor: pointer;
}
button:disabled {
background: #94a3b8;
cursor: not-allowed;
}
.results {
margin-top: 24px;
}
.result {
background: white;
border: 1px solid #ddd;
border-radius: 8px;
padding: 14px;
margin-bottom: 16px;
}
.result h3 {
margin: 0 0 8px;
font-size: 1rem;
color: #1e40af;
}
.result pre {
white-space: pre-wrap;
word-wrap: break-word;
margin: 0;
font-family: inherit;
font-size: 14.5px;
line-height: 1.5;
}
.error {
color: #b91c1c;
}
.loading {
color: #64748b;
font-style: italic;
}
</style>
</head>
<body>
<h1>Multi-AI (OpenRouter)</h1>

<label for="apiKey">OpenRouter API Key</label>
<input type="password" id="apiKey" placeholder="sk-or-v1-..." />

<label for="prompt">Your Question / Prompt</label>
<textarea id="prompt" placeholder="Ask anything..."></textarea>

<label>Models to query</label>
<div class="models" id="modelList">
<!-- checkboxes will be added here -->
</div>

<button id="runBtn" onclick="run()">Generate</button>

<div class="results" id="results"></div>

<script>
const MODELS = [
{ id: "openai/gpt-4o", name: "GPT-4o" },
{ id: "openai/gpt-4o-mini", name: "GPT-4o Mini" },
{ id: "meta-llama/llama-3.1-70b-instruct", name: "Llama 3.1 70B" },
{ id: "mistralai/mistral-large", name: "Mistral Large" },
{ id: "qwen/qwen-2.5-72b-instruct", name: "Qwen 2.5 72B" }
];

// Build checkboxes
const modelList = document.getElementById("modelList");
MODELS.forEach(m => {
const label = document.createElement("label");
label.innerHTML = `<input type="checkbox" value="${m.id}" checked> ${m.name}`;
modelList.appendChild(label);
});

// Load saved API key
const savedKey = localStorage.getItem("openrouter_key");
if (savedKey) document.getElementById("apiKey").value = savedKey;

async function run() {
const apiKey = document.getElementById("apiKey").value.trim();
const prompt = document.getElementById("prompt").value.trim();
const checked = [...document.querySelectorAll('#modelList input:checked')].map(c => c.value);

if (!apiKey) return alert("Please enter your OpenRouter API key");
if (!prompt) return alert("Please enter a prompt");
if (checked.length === 0) return alert("Select at least one model");

// Save key
localStorage.setItem("openrouter_key", apiKey);

const btn = document.getElementById("runBtn");
const results = document.getElementById("results");
btn.disabled = true;
results.innerHTML = "";

// Create placeholders
checked.forEach(modelId => {
const name = MODELS.find(m => m.id === modelId)?.name || modelId;
const div = document.createElement("div");
div.className = "result";
div.id = "res-" + modelId.replace(/[\/\.]/g, "-");
div.innerHTML = `<h3>${name}</h3><div class="loading">Generating...</div>`;
results.appendChild(div);
});

// Fire all requests in parallel
await Promise.all(checked.map(async (modelId) => {
const div = document.getElementById("res-" + modelId.replace(/[\/\.]/g, "-"));
try {


const res = await fetch("https://openrouter.ai/api/v1/chat/completions", {
method: "POST",
headers: {
"Authorization": "Bearer " + apiKey,
"Content-Type": "application/json",
"HTTP-Referer": location.href,
"X-Title": "Multi-AI PWA"
},
body: JSON.stringify({
model: modelId,
messages: [{ role: "user", content: prompt }],
max_tokens: 1024
})
});

const data = await res.json();

if (!res.ok) {
throw new Error(data.error?.message || res.statusText);
}

const text = data.choices?.[0]?.message?.content || "(no content)";
div.innerHTML = `<h3>${MODELS.find(m => m.id === modelId)?.name || modelId}</h3><pre>${escapeHtml(text)}</pre>`;
} catch (err) {
div.innerHTML = `<h3>${MODELS.find(m => m.id === modelId)?.name || modelId}</h3><div class="error">Error: ${escapeHtml(err.message)}</div>`;
}
}));

btn.disabled = false;
}

function escapeHtml(text) {
return text
.replace(/&/g, "&amp;")
.replace(/</g, "&lt;")
.replace(/>/g, "&gt;");
}
</script>
</body>
</html>
