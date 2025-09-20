## Prerequisites & Target Environment

* **Host OS**: Windows 10/11 (no separate VM required because WSL provides a Linux environment).
* **Linux**: WSL2 with **Ubuntu** distribution (you will run all dev commands inside the Ubuntu terminal).

> If you do **not** already have WSL Ubuntu:
> Open PowerShell **as Administrator** and run:
>
> ```bash
> wsl --install -d Ubuntu
> ```
>
> Reboot if prompted, launch “Ubuntu” from the Start menu, and create your Linux username/password.
> **Explanation**: This installs the Windows Subsystem for Linux (WSL) and the Ubuntu userland so you get a real Linux shell on your Windows machine. The Linux environment is isolated, so tools you install here won’t affect your Windows global installations.

---

## Tooling Inventory (reference links)

* **Node.js (LTS)** — downloads nodejs with npm
  [https://nodejs.org/en/download](https://nodejs.org/en/download)
  it is best to choose latest LTS and make sure to select correct version and architecture based on OS. For windows it is best to download Windows installer (.msi)

* **nvm (Node Version Manager)** — recommended for Linux/WSL
  [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)

* **Git** — version control
  [https://git-scm.com](https://git-scm.com)

* **Visual Studio Code (Windows)** — IDE
  [https://code.visualstudio.com/download](https://code.visualstudio.com/download)

* **VS Code “Remote – WSL” extension** — edit Linux files from Windows VS Code
  [https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)

* **Svelte for VS Code** — language features
  [https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)

**Explanation**: You will install Node and Git **inside WSL Ubuntu**, while VS Code runs in Windows and attaches into WSL using the Remote-WSL extension. This gives you the convenience of Windows desktop apps while compiling and running the app inside Linux.

---

## Open the Correct Terminal (WSL Ubuntu)

Run the Ubuntu app from the Start menu and confirm you are in Linux:

```bash
uname -a
echo $SHELL
```

**Explanation**: These commands confirm you’re in the Linux (WSL) shell and show your kernel and shell. You’ll run the remaining setup and dev commands here unless stated otherwise.

## Install Node.js + npm (choose **one** method)

### Option A) Recommended: nvm (Node Version Manager)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
nvm install --lts
nvm alias default --lts
node -v
npm -v
```

**Explanation**: The first line installs **nvm**, which lets you easily install or switch Node versions per project; the `export`/`source` lines load nvm into your current shell (the installer also adds them to `~/.bashrc` for future sessions). `nvm install --lts` fetches the current Long-Term Support Node (which includes npm), and setting the default ensures new shells pick it up; the final two commands confirm your install.

> Tip: If a new shell doesn’t recognize `nvm`, run `source ~/.bashrc` or open a fresh Ubuntu terminal. The installer appends the nvm init lines to your shell profile so it loads automatically next time.

### Option B) Alternative: NodeSource APT (system-wide Node)

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
node -v
npm -v
```

**Explanation**: This uses the official NodeSource repository to install the LTS Node system-wide via `apt`. It’s simpler than nvm but less flexible if you later need to test multiple Node versions.

---

## Configure Git (inside WSL Ubuntu)

```bash
git --version
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

**Explanation**: The first command verifies Git is available. The next two set your author identity used for commits so your repository history is properly attributed.

---

## Install VS Code (Windows) + Extensions

1. Install **VS Code** on Windows from the website above, then launch it.
2. In VS Code, install the **Remote – WSL** extension and **Svelte for VS Code**.

**Explanation**: VS Code runs on Windows but attaches into your WSL Ubuntu filesystem and processes, giving you Linux-native builds with Windows-native UX. The Svelte extension provides syntax highlighting, IntelliSense, and diagnostics for `.svelte` files.

> To open your WSL project in VS Code later: from WSL run `code .` in the project folder. The first run may prompt you to install the VS Code server inside WSL automatically.

---

## Scaffold a New Svelte 5 Project (two supported options)

### Option A — **Official SvelteKit (Recommended for Svelte 5)**

SvelteKit is the official application framework for Svelte 5, including routing, file-based pages, SSR/SSG, and adapters.

```bash
mkdir -p ~/projects && cd ~/projects
npm create svelte@latest hello
# choose: "Skeleton project" (minimal)
# choose: TypeScript / ESLint / Prettier as preferred
cd hello
npm install
```

**Explanation**: `npm create svelte@latest hello` scaffolds a modern SvelteKit app named `hello` with the official starter and up-to-date tooling. `npm install` downloads all dependencies from `package.json` so the dev server can run.

### Option B — **Vite Svelte Template (SPA)**

This generates a lighter, client-side SPA without SvelteKit’s routing/SSR features.

```bash
mkdir -p ~/projects && cd ~/projects
npm create vite@latest app1 -- --template svelte
cd app1
npm install
```

**Explanation**: `npm create vite@latest app1 -- --template svelte` scaffolds a basic Svelte single-page application using Vite as the build tool. This is appropriate for very simple front-end prototypes that do not require routing, SSR, or adapters.

> Which should I use? For most Svelte 5 apps, use **SvelteKit** (Option A). Choose the **Vite Svelte template** only if you specifically wants a minimal SPA(Single page application) or you are building a single-view demo.

---

## Run the Dev Server (WSL Ubuntu) and Open in Browser (Windows)

**SvelteKit**

```bash
npm run dev
```

**Vite SPA**

```bash
npm run dev
```

Open the printed URL (typically `http://localhost:5173`) in your Windows browser.

**Explanation**: Vite starts a local dev server inside WSL; Windows forwards `localhost` so you can visit the app from Edge/Chrome on Windows. If you can’t connect, run `npm run dev -- --host 0.0.0.0` to listen on all interfaces, then reload the page or open the LAN URL shown.

## Initialize Git in the Project (WSL Ubuntu)

```bash
git init
git add .
git commit -m "chore: scaffold Svelte project (SvelteKit or Vite) on WSL"
```

**Explanation**: These commands create a repository, stage all files, and make your first commit. Version control from the beginning helps you track changes and collaborate.

> Optional: Add a remote and push.

```bash
git remote add origin <YOUR-REMOTE-URL>
git branch -M main
git push -u origin main
```

**Explanation**: This links your local repo to a hosted service (e.g., GitHub) for backup and collaboration. The `-u` flag sets upstream tracking so future pushes are simpler.

---

## Environment & PATH Notes (WSL vs Windows)

* Node installed via **nvm/apt inside WSL** is separate from any Node you might install on Windows; each environment has its own PATH. This isolation prevents conflicts and keeps Linux builds consistent with Linux servers.
* If you change Node versions with `nvm use <version>`, open a fresh shell or run `hash -r` to refresh the shell’s command cache. This ensures the `node` and `npm` shims point at the selected version.

---
---

<br><br>

# Svelte 5 + TailwindCSS: Two Apps, One Beginner-Friendly Workflow

**Stack:** Node.js • Svelte 5 • Vite • TailwindCSS • VS Code
**Editor extensions I used:** Tailwind CSS IntelliSense (Tailwind Labs), Svelte for VS Code

I wrote and tested two tiny apps—`hello` and `indecision-machine`—to demonstrate Svelte 5 fundamentals, TailwindCSS styling, and a clean beginner workflow in VS Code. This is a read-only walkthrough of the code and why it works, with short, exact snippets and plain-language explanations.

---

## Quick Start (Svelte 5 + Vite)

```bash
# scaffold the app (kebab-case name!)
npm create vite@latest indecision-machine -- --template svelte
cd indecision-machine
npm i
```

Verify Svelte 5 and Svelte’s new mount API:

* `package.json` should include `"svelte": "^5"`.
* `src/main.js`:

  ```js
  // Svelte 5 mount API
  import { mount } from 'svelte'
  import './app.css'
  import App from './App.svelte'
  mount(App, { target: document.getElementById('app') })
  ```

Run it:

```bash
npm run dev
```

---

## Tailwind with Vite (two simple options)

### OPTION A — Vite plugin (no PostCSS file needed)

Follow Tailwind docs: [https://tailwindcss.com/docs/installation/using-vite](https://tailwindcss.com/docs/installation/using-vite)

```bash
npm i -D tailwindcss @tailwindcss/vite
```

`vite.config.js`:

```js
// Enable Tailwind via Vite plugin
import { defineConfig } from 'vite'
import { svelte } from '@sveltejs/vite-plugin-svelte'
import tailwind from '@tailwindcss/vite'

export default defineConfig({
  plugins: [svelte(), tailwind()],
})
```

`src/app.css`:

```css
/* Tailwind v4 import */
@import "tailwindcss";
```

Restart the dev server after changes.

---

### OPTION B — PostCSS plugin (what we used earlier)

```bash
npm i -D tailwindcss @tailwindcss/postcss postcss
```

`postcss.config.js`:

```js
// Wire Tailwind via PostCSS
export default {
  plugins: { '@tailwindcss/postcss': {} },
}
```

`src/app.css`:

```css
@import "tailwindcss";

/* Example: reuse utilities with @apply */
button.custom {
  @apply mt-5 mb-5 py-5 rounded-lg w-1/2 outline outline-1 outline-offset-1;
}
```

Import `app.css` in `src/main.js`, then restart.

> VS Code IntelliSense tip: Even with Tailwind v4, a small config helps scanning.
>
> ```js
> export default {
>   content: ['./index.html','./src/**/*.{svelte,js,ts}'],
>   theme: { extend: {} },
>   plugins: [],
> }
> ```

---

## Svelte Elements & Directives Reference (used in these apps)

**Component instance binding (`bind:this`)**

```svelte
<Modal bind:this={modal} />
```

I bind the component instance to a local variable so I can call its exported methods.

**DOM element binding (`bind:this`)**

```svelte
<dialog
  bind:this={dlg}
```

I bind the native `<dialog>` element to `dlg` to call its methods.

**Two-way binding (`bind:value`)**

```svelte
<input
    id="option"
    type="text"
    bind:value={option}
```

The input’s value stays in sync with the component variable.

**Event handlers + modifiers**

```svelte
<button class="btn" on:click={openModal} aria-haspopup="dialog">
  Hello
```

Here I handle a click; the `aria-haspopup="dialog"` announces the dialog.

```svelte
<form on:submit|preventDefault={onAdd} class="flex justify-center gap-3">
```

The `|preventDefault` modifier stops the page reload on submit.

**Slots (named and default)**

```svelte
<h2 id="hello-title">
  <slot name="title">Hello World</slot>
```

A named slot with a default.

```svelte
<div class="body">
  <slot><!-- default body if none provided -->Hello World</slot>
```

The default slot content displays if nothing is provided.

**Keyed each + selection**

```svelte
{#each choices as c (c.id)}
            <li class="border-b last:border-b-0">
```

Keying by `c.id` keeps DOM updates predictable.

**Class directive vs expression**

```svelte
class:bg-blue-50={c.id === selectedId}
class:ring-1={c.id === selectedId}
class:ring-blue-300={c.id === selectedId}
```

Conditional classes via directives.

```svelte
class={waiting ? "custom animate-pulse" : "custom"}
```

A class expression toggles a spinner effect.

**Reactive declarations (`$:`)**

```svelte
$: disableAdd = (input ?? "").trim() === "";
$: disableRemove = selectedId === null;
$: disableRandomizer = isWaiting || choiceCount.length === 0;
```

These recompute automatically when referenced values change.

**ARIA on dialog**

```svelte
<dialog
  bind:this={dlg}
  on:click={onBackdropClick}
  aria-labelledby="hello-title"
>
```

The dialog is named by the element with `id="hello-title"`.

**Native `<dialog>` closing via form**

```svelte
<form method="dialog">
  <h2 id="hello-title">
```

`method="dialog"` allows built-in “close” behavior (no extra JS).

---

## Svelte Command Comparisons

| Pattern                                        | What it does                                                                                    | Exact snippet                                                                                          |
| ---------------------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **Two-way binding** vs **one-way prop**        | `bind:option={input}` keeps parent and child in sync; `{addOption}` passes a function downward. | `<Inputs bind:option={input} bind:weight {addOption} {removeSelected} {disableAdd} {disableRemove} />` |
| **Explicit disabled** vs **boolean shorthand** | `disabled={expr}` computes disabled; `{disabled}` forwards a boolean prop directly.             | `disabled={disableAdd}` • `{disabled}`                                                                 |
| **Class directive** vs **class expression**    | `class:x={cond}` toggles one class; `class={expr}` computes a class string.                     | `class:bg-blue-50={c.id === selectedId}` • `class={waiting ? "custom animate-pulse" : "custom"}`       |
| **Event handler** vs **event modifier**        | `on:click={fn}` handles events; `on:submit`                                                     | `preventDefault` prevents default submission.  `on:click={openModal}` • `on\:submit preventDefault`    |
| **Instance binding** vs **prop passing**       | `bind:this={modal}` lets me call exported methods; `{decide}` passes a function prop.           | `<Modal bind:this={modal} />` • `<Randomizer {decide} ... />`                                          |

---

## Apps Overview

### App 1 — `hello` (modal with instance binding and `<dialog>`)

**Compact file map**

* `./App.svelte` (opens a modal component, binds the instance)
* `./lib/Modal.svelte` (wraps native `<dialog>`, exports `open`/`close`, handles backdrop clicks, slots and ARIA)

**Data flow in words**

* I bind the `Modal` component instance and call its exported `open()` method when the “Hello” button is clicked.
* Inside the modal, I bind the `<dialog>` element to call `showModal()`/`close()`, close on backdrop click, and let a `<form method="dialog">` handle closing via its buttons.

**Key behaviors (short snippets)**

*Component instance binding and method call*

```svelte
let modal; // bound to the Modal instance

function openModal() {
  modal.open(); // shows the <dialog>
}
```

I store the component instance and call its exported method.

*Exported methods + optional chaining on `<dialog>`*

```svelte
export function open() {
    dlg?.showModal();
  }
export function close() {
    dlg?.close();
  }
```

I use `?.` so calls are safe even if `dlg` is not yet set.

*Backdrop click closes only when clicking outside the inner content*

```svelte
function onBackdropClick(e) {
    if (e.target === dlg) close();
  }
```

I compare the event target with the dialog element.

*Accessible dialog structure*

```svelte
<dialog
  bind:this={dlg}
  on:click={onBackdropClick}
  aria-labelledby="hello-title"
>
```

I bind the element, attach the handler, and name the dialog for screen readers.

*Slots and `method="dialog"`*

```svelte
<form method="dialog">
    <h2 id="hello-title">
      <slot name="title">Hello World</slot>
```

The form’s method enables native closing; the named slot provides a default title.

**Verification checklist**

* Click “Hello” shows the modal via `modal.open()`.
* Pressing the button in the form closes the modal (no JS needed).
* Clicking the shaded backdrop (not inner content) closes the modal.
* The modal is labeled by the heading referenced in `aria-labelledby`.

**Pitfalls I avoided**

* I used `bind:this` on both the component and the `<dialog>` so I can call methods directly.
* I used `method="dialog"` so I did not need to manually wire the “OK” button.

---

### App 2 — `indecision-machine` (inputs, weighted list, selection, guarded actions, optional delay)

**Compact file map**
*Read the paths as they appear in source; both `components/*` and `lib/*` variants are present.*

* `./App.svelte` (state, weighted list logic, selection, wait/decide, rendering)
* `./components/inputs.svelte` (form: option, weight, add/remove)
* `./components/randomizer.svelte` (decide button with optional waiting state)
* `./app.css` (Tailwind import and small `@apply` helpers)

**Data flow in words**

* I manage `choices` and a derived `choiceCount` that duplicates each choice’s `id` by its `weight`. Random selection from `choiceCount` yields a weighted pick.
* The list is selectable; “Remove” is guarded and requires a selection. “Add” is guarded and ignores empty input.
* An optional “wait” state disables controls and shows a “Thinking…” label before the result.

**Short, exact snippets and what they prove**

*Weighted duplication (derive `choiceCount`)*

```svelte
const times = Math.max(1, Math.floor(Number(c.weight) || 1));
      for (let i = 0; i < times; i++) {
        choiceCount.push(c.id); // duplicate id "weight" times
      }
```

The id is pushed multiple times based on weight.

*Add a choice and rebuild derived array*

```svelte
choices = choices.concat({ id: id++, label: clean, weight: safeW });

rebuildChoiceCount(); // keep the derived array in sync
```

I add immutably and then recompute the derived data.

*Remove the selected item and rebuild derived array*

```svelte
choices = choices.filter((c) => c.id !== selectedId);
    selectedId = null;
    rebuildChoiceCount(); // keep derived array in sync
```

I remove by id, clear selection, and recompute weights.

*Guarded reactive flags (disable buttons while invalid or waiting)*

```svelte
$: disableAdd = (input ?? "").trim() === "";
$: disableRemove = selectedId === null;
$: disableRandomizer = isWaiting || choiceCount.length === 0;
```

These update automatically as the user types, selects, or waits.

*Randomizer with delay and weighted pick*

```svelte
isWaiting = true; // start waiting
setTimeout(() => {
      const pickedId =
        choiceCount[Math.floor(Math.random() * choiceCount.length)];
```

A brief wait precedes a weighted random selection.

*Selection highlight via class directives*

```svelte
class:bg-blue-50={c.id === selectedId}
class:ring-1={c.id === selectedId}
class:ring-blue-300={c.id === selectedId}
```

The selected row is visually distinct.

*Two-way bound inputs (option and weight)*

```svelte
<label for="option" class="text-sm font-medium">Option:</label>
                <input
                    id="option"
                    type="text"
                    bind:value={option}
```

The `option` input is two-way bound.

```svelte
<label for="weight" class="text-sm font-medium">Weight:</label>
                <input
                    id="weight"
                    type="number"
                    bind:value={weight}
```

The `weight` input is two-way bound.

*Parent passes props and bindings to inputs*

```svelte
<Inputs
        bind:option={input}
        bind:weight
        {addOption}
```

I bind the parent variables and pass functions to the child.

*Decide button with disabled and waiting states*

```svelte
<Randomizer {decide} disabled={disableRandomizer} waiting={isWaiting} />
```

The parent controls both the disabled and waiting props.

---

## Problems & Micro-Solutions

**Problem:** “How do I make sure weight is a positive integer ≥ 1?”
**solution:**

```svelte
const times = Math.max(1, Math.floor(Number(c.weight) || 1));
```

**Beginner explanation:** Convert to a number, floor to drop decimals, default to 1 if invalid, then clamp to at least 1.

---

**Problem:** “How do I add a new choice without mutating the array?”
**solution:**

```svelte
choices = choices.concat({ id: id++, label: clean, weight: safeW });
```

**Beginner explanation:** `concat` returns a new array; Svelte re-renders on reassignment. `id++` uses the current id then increments.

---

**Problem:** “How do I rebuild the weighted pool after changes?”
**solution:**

```svelte
rebuildChoiceCount(); // keep the derived array in sync
```

**Beginner explanation:** After add/remove, I recompute the duplicated id list so the randomizer reflects current weights.

---

**Problem:** “How do I remove the selected item safely?”
**solution:**

```svelte
choices = choices.filter((c) => c.id !== selectedId);
    selectedId = null;
```

**Beginner explanation:** `filter` creates a new array without the selected id; then I clear the selection.

---

**Problem:** “How do I show a short delay before picking?”
**solution:**

```svelte
isWaiting = true; // start waiting
setTimeout(() => {
```

**Beginner explanation:** I flip a waiting flag and start a timer; UI can show “Thinking…” and disable buttons until the timeout completes.

---

**Problem:** “How do I do a weighted random pick?”
**solution:**

```svelte
const pickedId =
        choiceCount[Math.floor(Math.random() * choiceCount.length)];
```

**Beginner explanation:** I choose a random index from the duplicated `choiceCount` array so higher weights appear more often. \[0-choiceCount]

---

**Problem:** “How do I guard buttons based on input, selection, or waiting?”
**solution:**

```svelte
$: disableRandomizer = isWaiting || choiceCount.length === 0;
```

**Beginner explanation:** This reactive line recomputes whenever `isWaiting` or `choiceCount` changes and disables the button accordingly.

---

## Troubleshooting — From chat

**Invalid package name error**
Use kebab-case when scaffolding:

```bash
npm create vite@latest indecision-machine -- --template svelte
```

**Tailwind CLI not found / missing PostCSS plugin**
Ensure PostCSS config declares the Tailwind plugin:

```js
export default {
  plugins: { '@tailwindcss/postcss': {} },
}
```

**No styles from `@apply`**
Use the correct outline utilities:

```css
@apply mt-5 mb-5 py-5 rounded-lg w-1/2 outline outline-1 outline-offset-1;
```
<br><br>
---
---

### Styling (Tailwind utilities and small `@apply`)

**Global Tailwind import**

```css
@import "tailwindcss";
```

I bring in Tailwind’s utilities once from `app.css`.

**Reusable button style**

```css
button.custom {
  @apply mt-5 mb-5 py-5 rounded-lg w-1/2 outline outline-1 outline-offset-1;
}
```

I consolidate multiple utilities into a single class name with `@apply`.

---

### Mounting the App (Svelte 5)

```js
// Svelte 5 mount API
import { mount } from 'svelte'
import './app.css'
import App from './App.svelte'
mount(App, { target: document.getElementById('app') })
```

Svelte 5 mounts the root component with `mount(...)` instead of `new App(...)`. This is the first file I check when upgrading or debugging startup.

<br>

---
---

<br>

**Randomizer disabled when empty or waiting**
Parent controls disabled and waiting props:

```svelte
<Randomizer {decide} disabled={disableRandomizer} waiting={isWaiting} />
```

---

## Common Issues and Fixes

**Package names**
Svelte’s scaffolder enforces npm naming rules; I use lowercase plus dashes (e.g., `indecision-machine`).

**Tailwind / PostCSS configuration**
Option A uses the Vite plugin; Option B uses `@tailwindcss/postcss`. After editing config, I restart the dev server.

**Small decision delay**
I add a boolean and a timeout to prevent double clicks and to show a “Thinking…” state, then re-enable controls when the timeout ends.

---

## Working with State and Events in Svelte

**Reactive declarations (`$:`)**

```svelte
$: disableAdd = (input ?? "").trim() === "";
```

When `input` changes, this recomputes automatically.

**Props and shorthand**

```svelte
<Randomizer {decide} disabled={disableRandomizer} waiting={isWaiting} />
```

I mix shorthand (`{decide}`) and explicit props (`disabled={...}`).

**Component instance binding**

```svelte
<Modal bind:this={modal} />
```

I gain a handle to call exported methods.

**Conditional classes**

```svelte
class:ring-1={c.id === selectedId}
```

Classes toggle based on selection.

**Event handlers and modifiers**

```svelte
<form on:submit|preventDefault={onAdd}
```

The modifier prevents the default submit, keeping the SPA experience.

---

### Appendix: App-Specific Notes

* **`hello`** uses `<dialog>` with `method="dialog"` for native closing, a backdrop click handler to close only when clicking outside, and instance binding (`bind:this`) to expose `open()`/`close()` cleanly.
* **`indecision-machine`** keeps logic plain: immutable array updates via `concat`/`filter`, a derived `choiceCount` for weighted random selection, selection-guarded removal, and reactive flags to disable buttons and the randomizer.
