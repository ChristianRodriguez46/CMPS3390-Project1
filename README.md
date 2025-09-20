<div id="top">

<!-- HEADER STYLE: CLASSIC -->
<div align="center">


# CMPS3390-PROJECT1

<em>Empowering Seamless Decisions Through Innovative Simplicity</em>

<!-- BADGES -->
<img src="https://img.shields.io/github/last-commit/ChristianRodriguez46/CMPS3390-Project1?style=flat&logo=git&logoColor=white&color=0080ff" alt="last-commit">
<img src="https://img.shields.io/github/languages/top/ChristianRodriguez46/CMPS3390-Project1?style=flat&color=0080ff" alt="repo-top-language">
<img src="https://img.shields.io/github/languages/count/ChristianRodriguez46/CMPS3390-Project1?style=flat&color=0080ff" alt="repo-language-count">

<em>Built with the tools and technologies:</em>

<img src="https://img.shields.io/badge/JSON-000000.svg?style=flat&logo=JSON&logoColor=white" alt="JSON">
<img src="https://img.shields.io/badge/Markdown-000000.svg?style=flat&logo=Markdown&logoColor=white" alt="Markdown">
<img src="https://img.shields.io/badge/npm-CB3837.svg?style=flat&logo=npm&logoColor=white" alt="npm">
<img src="https://img.shields.io/badge/PostCSS-DD3A0A.svg?style=flat&logo=PostCSS&logoColor=white" alt="PostCSS">
<img src="https://img.shields.io/badge/Svelte-FF3E00.svg?style=flat&logo=Svelte&logoColor=white" alt="Svelte">
<img src="https://img.shields.io/badge/JavaScript-F7DF1E.svg?style=flat&logo=JavaScript&logoColor=black" alt="JavaScript">
<img src="https://img.shields.io/badge/TypeScript-3178C6.svg?style=flat&logo=TypeScript&logoColor=white" alt="TypeScript">
<img src="https://img.shields.io/badge/Vite-646CFF.svg?style=flat&logo=Vite&logoColor=white" alt="Vite">

</div>
<br>

---

## 📄 Table of Contents

- [Overview](#-overview)
- [Getting Started](#-getting-started)
    - [Prerequisites](#-prerequisites)
    - [Installation](#-installation)
    - [Usage](#-usage)
    - [Testing](#-testing)
- [Features](#-features)
- [Project Structure](#-project-structure)
    - [Project Index](#-project-index)

---

## ✨ Overview

CMPS3390-Project1 is a developer-focused toolkit that simplifies building interactive, decision-based web applications using Svelte and Vite. It emphasizes a consistent development environment and modern frontend practices.

**Why CMPS3390-Project1?**

This project helps developers rapidly create responsive, modular web interfaces with a focus on performance and maintainability. The core features include:

- 🧩 **🔧 Environment Setup:** Guides for establishing a uniform Linux-based environment on Windows via WSL2, streamlining onboarding and collaboration.
- 🚀 **⚡ Modern Tooling:** Configures Svelte with Vite for fast, efficient build processes and hot module replacement.
- 🎨 **🖼️ Reusable Components:** Provides modular UI elements like modals and decision-making interfaces for seamless integration.
- 📝 **🔒 TypeScript Support:** Ensures type safety and improved developer productivity with comprehensive TypeScript configurations.
- 🔄 **🔧 Streamlined Workflows:** Simplifies development, testing, and deployment with well-defined scripts and configurations.

---

## 📌 Features

|      | Component            | Details                                                                                     |
| :--- | :------------------- | :------------------------------------------------------------------------------------------ |
| ⚙️  | **Architecture**     | <ul><li>Client-side SPA built with <strong>Svelte</strong></li><li>Uses <strong>Vite</strong> as build tool</li><li>TypeScript for type safety</li></ul> |
| 🔩 | **Code Quality**     | <ul><li>Consistent code style with <strong>Prettier</strong> (implied via PostCSS config)</li><li>TypeScript enhances robustness</li><li>Modular component structure in Svelte</li></ul> |
| 📄 | **Documentation**    | <ul><li>Basic README with project overview</li><li>Includes <strong>Markdown</strong> files</li><li>Configuration files like <code>jsconfig.json</code> aid IDE support</li></ul> |
| 🔌 | **Integrations**      | <ul><li>Build and dev tools: <strong>npm</strong></li><li>CSS frameworks: <strong>TailwindCSS</strong></li><li>PostCSS for CSS processing</li><li>Svelte plugin for Vite</li></ul> |
| 🧩 | **Modularity**        | <ul><li>Component-based architecture in Svelte</li><li>Separation of concerns via distinct packages (<em>Hello</em> and <em>indecision-machine</em>)</li></ul> |
| 🧪 | **Testing**           | <ul><li>Not explicitly detailed; likely minimal or manual testing</li><li>Potential for unit tests in TypeScript</li></ul> |
| ⚡️  | **Performance**       | <ul><li>Vite provides fast hot module replacement</li><li>Optimized CSS with TailwindCSS and PostCSS</li></ul> |
| 🛡️ | **Security**          | <ul><li>No explicit security features; standard web app practices</li><li>TypeScript reduces runtime errors</li></ul> |
| 📦 | **Dependencies**      | <ul><li>Relies on <strong>npm</strong></li><li>Key dependencies include <strong>Svelte</strong>, <strong>TailwindCSS</strong>, <strong>Vite</strong></li></ul> |

---

## 📁 Project Structure

```sh
└── CMPS3390-Project1/
    ├── Documentation.md
    ├── Hello
    │   ├── .gitignore
    │   ├── .vscode
    │   ├── README.md
    │   ├── index.html
    │   ├── jsconfig.json
    │   ├── package-lock.json
    │   ├── package.json
    │   ├── public
    │   ├── src
    │   ├── svelte.config.js
    │   └── vite.config.js
    └── indecision-machine
        ├── .gitignore
        ├── .vscode
        ├── README.md
        ├── index.html
        ├── jsconfig.json
        ├── package-lock.json
        ├── package.json
        ├── postcss.config.cjs
        ├── public
        ├── src
        ├── svelte.config.js
        └── vite.config.js
```

---

### 📑 Project Index

<details open>
	<summary><b><code>CMPS3390-PROJECT1/</code></b></summary>
	<!-- __root__ Submodule -->
	<details>
		<summary><b>Set up and log</b></summary>
		<blockquote>
			<div class='directory-path' style='padding: 8px 0; color: #666;'>
			<table style='width: 100%; border-collapse: collapse;'>
			<thead>
				<tr style='background-color: #f8f9fa;'>
					<th style='width: 30%; text-align: left; padding: 8px;'>File Name</th>
					<th style='text-align: left; padding: 8px;'>Summary</th>
				</tr>
			</thead>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Documentation.md'>Documentation.md</a></b></td>
					<td style='padding: 8px;'>- The code file in question serves as a foundational component within the overall architecture, primarily responsible for facilitating environment setup and ensuring consistent prerequisites for development<br>- It provides essential guidance and configuration details that enable developers to establish a compatible Linux-based environment on Windows via WSL2, which is crucial for maintaining uniformity across the development workflow<br>- By defining the target environment and necessary tooling, this file helps streamline onboarding and supports the seamless integration of various tools like Node.js, thereby underpinning the stability and reliability of the entire codebase.</td>
				</tr>
			</table>
		</blockquote>
	</details>
	<!-- Hello Submodule -->
	<details>
		<summary><b>Hello</b></summary>
		<blockquote>
			<div class='directory-path' style='padding: 8px 0; color: #666;'>
				<code><b>⦿ Hello</b></code>
			<table style='width: 100%; border-collapse: collapse;'>
			<thead>
				<tr style='background-color: #f8f9fa;'>
					<th style='width: 30%; text-align: left; padding: 8px;'>File Name</th>
					<th style='text-align: left; padding: 8px;'>Summary</th>
				</tr>
			</thead>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/svelte.config.js'>svelte.config.js</a></b></td>
					<td style='padding: 8px;'>- Configure Sveltes build process to utilize Vites preprocessing capabilities, enabling seamless integration of modern development features<br>- This setup ensures efficient compilation and preprocessing of Svelte components, supporting a smooth development experience within the overall project architecture<br>- It plays a crucial role in optimizing the build pipeline for faster development and deployment cycles.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/vite.config.js'>vite.config.js</a></b></td>
					<td style='padding: 8px;'>- Configures the development environment for the project by integrating Vite with Svelte<br>- It streamlines the build process, enabling efficient development and hot module replacement, which enhances the overall architectures responsiveness and modularity<br>- This setup ensures a smooth development experience tailored for a Svelte-based application within the larger project ecosystem.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/package.json'>package.json</a></b></td>
					<td style='padding: 8px;'>- Defines the project configuration and dependencies for a Svelte-based web application using Vite<br>- It manages development scripts for building, previewing, and running the app locally, ensuring a streamlined development workflow<br>- This setup facilitates rapid development and deployment of a modern, modular frontend interface within the overall architecture.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/jsconfig.json'>jsconfig.json</a></b></td>
					<td style='padding: 8px;'>- Defines TypeScript configuration for the project, ensuring seamless integration of JavaScript, Svelte, and JSON modules<br>- Facilitates accurate type checking, source mapping, and module resolution aligned with modern JavaScript standards<br>- Supports robust development and debugging workflows within the overall architecture, enhancing code quality and maintainability across the codebase.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/index.html'>index.html</a></b></td>
					<td style='padding: 8px;'>- Sets up the main entry point for the web application by defining the HTML structure and linking the primary JavaScript module<br>- It establishes the foundational layout and ensures the application loads correctly within the overall project architecture, serving as the initial interface that integrates the front-end components and scripts for user interaction.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/README.md'>README.md</a></b></td>
					<td style='padding: 8px;'>- Provides a foundational setup for developing Svelte applications with Vite, emphasizing ease of use, developer experience, and extensibility<br>- It facilitates rapid prototyping and local development, serving as a lightweight alternative to SvelteKit<br>- The structure supports future migration to more advanced frameworks while maintaining core functionalities like HMR and TypeScript integration.</td>
				</tr>
			</table>
			<!-- src Submodule -->
			<details>
				<summary><b>src</b></summary>
				<blockquote>
					<div class='directory-path' style='padding: 8px 0; color: #666;'>
						<code><b>⦿ Hello.src</b></code>
					<table style='width: 100%; border-collapse: collapse;'>
					<thead>
						<tr style='background-color: #f8f9fa;'>
							<th style='width: 30%; text-align: left; padding: 8px;'>File Name</th>
							<th style='text-align: left; padding: 8px;'>Summary</th>
						</tr>
					</thead>
						<tr style='border-bottom: 1px solid #eee;'>
							<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/src/main.js'>main.js</a></b></td>
							<td style='padding: 8px;'>- Initialize and mount the main Svelte application within the project architecture, establishing the primary user interface by rendering the App component into the designated DOM element<br>- This setup serves as the entry point for the frontend, orchestrating the connection between the core application logic and the webpage, thereby enabling user interactions and dynamic content display.</td>
						</tr>
						<tr style='border-bottom: 1px solid #eee;'>
							<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/src/App.svelte'>App.svelte</a></b></td>
							<td style='padding: 8px;'>- Facilitates user interaction by providing a button that triggers the display of a modal dialog<br>- It integrates the modal component into the main application, enabling seamless opening and closing of overlay content<br>- This setup supports a dynamic, interactive user interface within the overall architecture, enhancing user engagement and modularity of dialog management.</td>
						</tr>
						<tr style='border-bottom: 1px solid #eee;'>
							<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/src/vite-env.d.ts'>vite-env.d.ts</a></b></td>
							<td style='padding: 8px;'>- Defines TypeScript type declarations for Svelte and Vite, ensuring proper type checking and integration within the development environment<br>- Supports seamless development by enabling accurate autocompletion and error detection, thereby enhancing overall project stability and developer productivity in the context of a Svelte and Vite-based web application.</td>
						</tr>
					</table>
					<!-- lib Submodule -->
					<details>
						<summary><b>lib</b></summary>
						<blockquote>
							<div class='directory-path' style='padding: 8px 0; color: #666;'>
								<code><b>⦿ Hello.src.lib</b></code>
							<table style='width: 100%; border-collapse: collapse;'>
							<thead>
								<tr style='background-color: #f8f9fa;'>
									<th style='width: 30%; text-align: left; padding: 8px;'>File Name</th>
									<th style='text-align: left; padding: 8px;'>Summary</th>
								</tr>
							</thead>
								<tr style='border-bottom: 1px solid #eee;'>
									<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Hello/src/lib/Modal.svelte'>Modal.svelte</a></b></td>
									<td style='padding: 8px;'>- Provides a reusable modal dialog component for user interactions such as alerts and confirmations within the application<br>- Facilitates displaying, closing, and handling user clicks outside the modal content, ensuring a seamless and accessible user experience<br>- Integrates smoothly into the overall architecture by enabling consistent modal behavior across different parts of the project.</td>
								</tr>
							</table>
						</blockquote>
					</details>
				</blockquote>
			</details>
		</blockquote>
	</details>
	<!-- indecision-machine Submodule -->
	<details>
		<summary><b>indecision-machine</b></summary>
		<blockquote>
			<div class='directory-path' style='padding: 8px 0; color: #666;'>
				<code><b>⦿ indecision-machine</b></code>
			<table style='width: 100%; border-collapse: collapse;'>
			<thead>
				<tr style='background-color: #f8f9fa;'>
					<th style='width: 30%; text-align: left; padding: 8px;'>File Name</th>
					<th style='text-align: left; padding: 8px;'>Summary</th>
				</tr>
			</thead>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/svelte.config.js'>svelte.config.js</a></b></td>
					<td style='padding: 8px;'>- Defines the Svelte configuration for the project, integrating Vite preprocessing to streamline the build process<br>- It ensures that Svelte components are correctly preprocessed during development and production, facilitating efficient compilation and enhancing overall project performance within the architecture.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/postcss.config.cjs'>postcss.config.cjs</a></b></td>
					<td style='padding: 8px;'>- Configures PostCSS to integrate Tailwind CSS, enabling utility-first styling and the use of the @apply directive within the project<br>- Serves as a foundational styling setup that supports consistent, maintainable, and scalable CSS architecture across the entire codebase<br>- Facilitates seamless styling workflows aligned with Tailwinds framework, contributing to a cohesive user interface design.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/vite.config.js'>vite.config.js</a></b></td>
					<td style='padding: 8px;'>- Configures the development environment for the project by integrating Svelte and TailwindCSS with Vite<br>- It streamlines the build process, enabling efficient development and styling workflows within the overall architecture<br>- This setup ensures a smooth, modern frontend experience aligned with the projects goal of delivering a responsive, user-friendly application.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/package.json'>package.json</a></b></td>
					<td style='padding: 8px;'>- Defines the project configuration and dependencies for the indecision-machine application, establishing the build, development, and preview workflows<br>- It ensures the integration of Svelte and Tailwind CSS, facilitating a streamlined development environment for a web-based decision-making tool within a modular architecture.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/jsconfig.json'>jsconfig.json</a></b></td>
					<td style='padding: 8px;'>- Defines TypeScript configuration for the project, ensuring seamless integration of JavaScript, Svelte, and JSON modules<br>- Facilitates accurate type checking, source mapping, and module resolution aligned with modern JavaScript standards<br>- Supports robust development and debugging workflows within the overall architecture, enhancing code quality and maintainability across the codebase.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/index.html'>index.html</a></b></td>
					<td style='padding: 8px;'>- Sets up the main entry point for the Indecision Machine web application, establishing the HTML structure and linking essential resources<br>- It initializes the user interface by loading the primary JavaScript module, enabling interactive decision-making features within the app<br>- This file serves as the foundation for rendering and launching the applications core functionality.</td>
				</tr>
				<tr style='border-bottom: 1px solid #eee;'>
					<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/README.md'>README.md</a></b></td>
					<td style='padding: 8px;'>- Provides a foundational setup for developing Svelte applications with Vite, focusing on streamlined development experience, efficient hot module replacement, and TypeScript integration<br>- Serves as a lightweight template for building and customizing Svelte projects, with easy migration paths to SvelteKit if extended capabilities are needed<br>- Facilitates rapid onboarding and consistent project structure within the architecture.</td>
				</tr>
			</table>
			<!-- src Submodule -->
			<details>
				<summary><b>src</b></summary>
				<blockquote>
					<div class='directory-path' style='padding: 8px 0; color: #666;'>
						<code><b>⦿ indecision-machine.src</b></code>
					<table style='width: 100%; border-collapse: collapse;'>
					<thead>
						<tr style='background-color: #f8f9fa;'>
							<th style='width: 30%; text-align: left; padding: 8px;'>File Name</th>
							<th style='text-align: left; padding: 8px;'>Summary</th>
						</tr>
					</thead>
						<tr style='border-bottom: 1px solid #eee;'>
							<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/src/main.js'>main.js</a></b></td>
							<td style='padding: 8px;'>- Initialize and mount the main Svelte application within the project architecture, establishing the primary user interface entry point<br>- It connects the core App component to the DOM, enabling the rendering of the applications visual elements and facilitating user interaction as part of the overall system.</td>
						</tr>
						<tr style='border-bottom: 1px solid #eee;'>
							<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/src/App.svelte'>App.svelte</a></b></td>
							<td style='padding: 8px;'>- Implements an interactive decision-making interface that allows users to add, remove, and select options with adjustable weights<br>- Facilitates randomized choice selection based on weighted preferences, providing a seamless user experience for managing choices and generating decisions within the overall application architecture<br>- Enhances user engagement through dynamic list management and probabilistic outcomes.</td>
						</tr>
						<tr style='border-bottom: 1px solid #eee;'>
							<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/src/vite-env.d.ts'>vite-env.d.ts</a></b></td>
							<td style='padding: 8px;'>- Defines TypeScript type declarations for Svelte and Vite environments, ensuring seamless integration and type safety across the development setup<br>- Supports consistent development experience by enabling proper type recognition within the project, which is essential for maintaining robust, scalable architecture in the overall codebase.</td>
						</tr>
					</table>
					<!-- components Submodule -->
					<details>
						<summary><b>components</b></summary>
						<blockquote>
							<div class='directory-path' style='padding: 8px 0; color: #666;'>
								<code><b>⦿ indecision-machine.src.components</b></code>
							<table style='width: 100%; border-collapse: collapse;'>
							<thead>
								<tr style='background-color: #f8f9fa;'>
									<th style='width: 30%; text-align: left; padding: 8px;'>File Name</th>
									<th style='text-align: left; padding: 8px;'>Summary</th>
								</tr>
							</thead>
								<tr style='border-bottom: 1px solid #eee;'>
									<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/src/components/inputs.svelte'>inputs.svelte</a></b></td>
									<td style='padding: 8px;'>- Facilitates user input for selecting options and assigning weights within the decision-making interface<br>- Enables adding and removing choices dynamically, supporting interactive adjustments to the list of options<br>- Integrates seamlessly into the overall architecture by providing a user-friendly component for capturing decision parameters, contributing to the machines ability to process and evaluate weighted options effectively.</td>
								</tr>
								<tr style='border-bottom: 1px solid #eee;'>
									<td style='padding: 8px;'><b><a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/indecision-machine/src/components/randomizer.svelte'>randomizer.svelte</a></b></td>
									<td style='padding: 8px;'>- Provides an interactive button component that enables users to trigger decision-making actions within the application<br>- It visually indicates when the system is processing or thinking, enhancing user engagement and clarity<br>- As part of the overall architecture, it facilitates user-driven randomness and choice selection, supporting the application's goal of delivering dynamic, decision-based interactions.</td>
								</tr>
							</table>
						</blockquote>
					</details>
				</blockquote>
			</details>
		</blockquote>
	</details>
</details>

---

## 🚀 Getting Started

### 📋 Prerequisites

This project requires the following dependencies:
- **Look at setup:** <a href='https://github.com/ChristianRodriguez46/CMPS3390-Project1/blob/master/Documentation.md'>Documentation.md</a>
- **Programming Languages used:** JavaScript, Svelte, Css, Html
- **Package Manager:** Npm
- **Version Control:** Git

### ⚙️ Installation

Build CMPS3390-Project1 from the source and install dependencies:

1. **Clone the repository:**

    ```sh
    ❯ git clone https://github.com/ChristianRodriguez46/CMPS3390-Project1
    ```

2. **Navigate to the project directory:**

    ```sh
    ❯ cd CMPS3390-Project1
    ```

3. **Navigate to a project directory:**

```sh
❯ cd Hello
   ---OR---
❯ cd indecision-machine
```

4. **Install the dependencies:**

**Using [npm](https://www.npmjs.com/):**

```sh
both commands do the same thing

❯ npm install
 ---OR---
❯ npm i
```

### 💻 Usage

Run the project with:

**Using [npm](https://www.npmjs.com/):**

```sh
npm run dev
```

---

<div align="left"><a href="#top">⬆ Return</a></div>

---
