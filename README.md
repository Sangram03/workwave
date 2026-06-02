## Step-by-Step Guide to Create a VS Code Extension

### 1. Install Prerequisites

Install:

* [Node.js](https://nodejs.org?utm_source=chatgpt.com)
* [Visual Studio Code](https://code.visualstudio.com?utm_source=chatgpt.com)

Verify installation:

```bash
node -v
npm -v
```

---

### 2. Install Yeoman and VS Code Extension Generator

```bash
npm install -g yo generator-code
```

Verify:

```bash
yo --version
```

---

### 3. Create a New Extension Project

```bash
yo code
```

Select:

```text
? What type of extension do you want to create?
> New Extension (TypeScript)
```

Fill in:

```text
Extension Name: workwave
Identifier: workwave
Description: Productivity extension for VS Code
```

---

### 4. Open the Project

```bash
cd workwave
code .
```

---

### 5. Understand the Project Structure

```text
workwave/
│
├── src/
│   └── extension.ts
├── package.json
├── README.md
├── tsconfig.json
└── .vscode/
```

---

### 6. Add Your First Command

Open:

```ts
src/extension.ts
```

Replace the activate function with:

```ts
import * as vscode from 'vscode';

export function activate(context: vscode.ExtensionContext) {

    let disposable = vscode.commands.registerCommand(
        'workwave.helloWorld',
        () => {
            vscode.window.showInformationMessage(
                'Hello from WorkWave!'
            );
        }
    );

    context.subscriptions.push(disposable);
}

export function deactivate() {}
```

---

### 7. Register the Command

Open:

```json
package.json
```

Inside `contributes`:

```json
"commands": [
  {
    "command": "workwave.helloWorld",
    "title": "WorkWave: Hello World"
  }
]
```

---

### 8. Run the Extension

Press:

```text
F5
```

A new Extension Development Host window opens.

Open Command Palette:

```text
Ctrl + Shift + P
```

Run:

```text
WorkWave: Hello World
```

You should see:

```text
Hello from WorkWave!
```

---

### 9. Build the Extension

```bash
npm install
npm run compile
```

---

### 10. Package the Extension

Install VSCE:

```bash
npm install -g @vscode/vsce
```

Package:

```bash
vsce package
```

Output:

```text
workwave-0.0.1.vsix
```

Running:

```
vsce package

---

### 11. Install the VSIX

```bash
code --install-extension workwave-0.0.1.vsix
```

or in VS Code:

```text
Extensions → ⋯ → Install from VSIX
```

---

### 12. Publish to Marketplace

Create a publisher account at:

[Visual Studio Marketplace](https://marketplace.visualstudio.com/manage?utm_source=chatgpt.com)

Login:

```bash
vsce login <publisher-name>
```

Publish:

```bash
vsce publish
```

---
