<h1 align="center">Post_that</h1>
<p align="center">An n8n agent that generates social media posts with AI images, captions, and hashtags through Telegram.</p>

<br/>

<p align="center">
  <img src="https://github.com/user-attachments/assets/83c623b6-1f78-4c7e-a57f-1683d60cc1e9" width="100%" alt="Workflow Preview">
</p>

<hr/>

<h2>🚀 What It Does</h2>
<p>
Send a text prompt to a Telegram bot and the workflow will:
</p>
<ul>
  <li>Generate an AI image using <strong>Cloudflare Workers AI</strong></li>
  <li>Create a caption and hashtags using an <strong>AI language model</strong></li>
  <li>Send the final post (image + caption) back to Telegram</li>
  <li>Protect against large images with an automatic <strong>1MP size limit</strong></li>
</ul>

<hr/>

<h2>✨ Core Features</h2>
<ul>
  <li>Telegram bot prompt input</li>
  <li>AI image creation</li>
  <li>AI caption + hashtag generation</li>
  <li>Image size validation (blocks > 1MP)</li>
  <li>Reusable  sub-workflows</li>
  <li>Returns ready-to-post content automatically</li>
</ul>

<hr/>

<h2>🔄 Workflow Overview</h2>

<h3>Main Flow</h3>
<table>
  <tr><th>Step</th><th>Node</th><th>Purpose</th></tr>
  <tr><td>1</td><td>Telegram Trigger</td><td>Reads messages from Telegram</td></tr>
  <tr><td>2</td><td>OpenAI Chat Model</td><td>Extracts user prompt / intention</td></tr>
  <tr><td>3</td><td>Image Generation</td><td>Builds API params (prompt, seed, size)</td></tr>
  <tr><td>4</td><td>Check Image Size</td><td>Blocks >1MP images</td></tr>
  <tr><td>5</td><td>Call Cloudflare Workers AI</td><td>Generates the image</td></tr>
  <tr><td>6</td><td>Convert to File</td><td>Converts base64 to image</td></tr>
  <tr><td>7</td><td>Caption + Hashtags</td><td>AI generates caption + hashtags</td></tr>
  <tr><td>8</td><td>Send Photo Message</td><td>Sends image to Telegram</td></tr>
  <tr><td>9</td><td>Send Text Message</td><td>Sends caption + hashtags</td></tr>
</table>

<br/>

<h3>🧩 Sub-Workflows</h3>
<table>
  <tr><th>Name</th><th>Purpose</th></tr>
  <tr><td>Setup Workflow</td><td>Ensures required AI parameters exist</td></tr>
  <tr><td>Get Accounts / Get Flux Schnell Image</td><td>Handles Cloudflare API calls</td></tr>
  <tr><td>Call Cloudflare Workers AI Flux</td><td>Reusable image generator</td></tr>
</table>

<hr/>

<h2>⚙️ Parameters & Why They Matter</h2>
<table>
  <tr><th>Parameter</th><th>Use</th></tr>
  <tr><td>prompt</td><td>User request text</td></tr>
  <tr><td>width / height</td><td>Defaults to 1024 if not provided</td></tr>
  <tr><td>seed</td><td>Creates deterministic variations (<code>Math.floor(Math.random() * 100000000)</code>)</td></tr>
  <tr><td>image_size_validation</td><td>Blocks >1MP generation</td></tr>
</table>

<hr/>

<h2>💬 Telegram Bot Setup</h2>
<p>Create a Telegram bot using:</p>
<pre><code>@BotFather → /newbot</code></pre>
<p>Add the bot token to the <strong>Telegram Trigger</strong> node credentials in n8n.</p>

<hr/>

<h2>☁️ Cloudflare Workers AI Setup</h2>
<p>Get an API token from:</p>
<pre><code>https://dash.cloudflare.com/</code></pre>

<p><strong>Required:</strong></p>
<ul>
  <li>Workers AI enabled</li>
  <li>Access to image model (Flux, etc.)</li>
</ul>

<p>Add your <strong>API Token</strong> and <strong>Account ID</strong> to n8n credentials.</p>

<hr/>

<h2>📦 Deployment</h2>
<p>This project is fully contained inside n8n.</p>
<p><strong>No additional hosting required.</strong></p>

<pre><code>n8n → Import workflow → Run</code></pre>

<hr/>

<h2>🔮 Future Add-ons</h2>
<ul>
  <li>Auto-posting to Instagram</li>
  <li>Scheduled posting</li>
  <li>User queues</li>
  <li>Usage limits & quotas</li>
</ul>

<hr/>

<h2>💡 Why Use This?</h2>
<p>It automates content creation by eliminating:</p>
<ul>
  <li>Manual image editing</li>
  <li>Caption writing</li>
  <li>Hashtag searching</li>
  <li>Uploading and formatting</li>
</ul>

<p><strong>Type an idea → Get a full post ready to publish.</strong></p>

<hr/>
<a src="https://www.notion.so/Post_that-N8N-Project-2b039954225380ac84d0f06dd68019ce?source=copy_link"><h3>Checkout My Notion - Scribble notes for some insights how I made this!</h3></a>
