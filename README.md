# site
website with plugin architecture

mdx-bundler and plugins compile and assemble pages on the fly in the user's browser, reading .mdx files from the out/pages/ folder like regular static files.
This eliminates the need to run npm run build every time the content changes. You simply change the text or code in the .mdx file, upload it to the hosting, and the site instantly updates. For a static content site with plugins, this is the most efficient and fastest process.

This architecture is for creating a flexible website builder. You essentially have Next.js and Rust's Wasm engine (runtime) running directly inside the client's browser. The "out" folder isn't just a static copy of one version of the site, but a fully-fledged core application that automatically picks up, parses, and renders .mdx files on the fly. Why this solution is so great: Zero-code for the user: Users don't need to know anything about React, Node.js, Webpack, or the terminal. They don't need to install anything. Unlimited customization: Anyone can open the file in a regular Notepad, rewrite the text, sketch out Tailwind classes for the design, and the site will instantly become unique. Instant deployment: Simply drag and drop the edited "out" folder to GitHub Pages, Netlify, or any free hosting service, and everything works immediately. Overall, we've created a very powerful and easy-to-use system. A truly portable, next-generation website builder.

# Core (Rust Wasm + Next.js App Router + MDX)

Pages are rendered as static MDX files (without heavy and redundant server-side dependencies).

Utilizes the latest Tailwind CSS v4 featuring modern class syntax (`bg-linear-to-r`, `bg-size-[200%_200%]`).

## Client-Side Interactivity Directly inside MDX

For standalone UI elements (helper widgets, dynamic download buttons, event handlers), components are defined and rendered directly inside `.mdx` files using React client hooks (`useState`, `useEffect`).

This eliminates the need to clutter the `components` folder with dozens of tiny, isolated `.tsx` files for every minor interface element.

## Rust WebAssembly (Wasm) Integration

Heavy, isolated business logic (HTML generation, data structures parsing, heavy data processing, local servers simulation) is offloaded to high-performance Rust modules.

Rust prepares computed data or ready-to-use HTML strings, while the client-side MDX layer simply receives them and injects them into the DOM. This bypasses complex build setups and heavy backend controllers.

## What You Can Use inside .mdx Files

Inside interactive pages, you can freely mix and match:
* **Standard Markdown** — for text formatting, bullet lists, tables, and links.
* **Tailwind CSS v4 Classes** — for instant styling of any HTML tag.
* **React Hooks and Components** — built-in sliders (`swiper`), interactive charts (`echarts-for-react`), and animations (`motion`).
* **Icons** — pre-packaged icon sets from `lucide-react`, `@phosphor-icons/react`, and `react-icons`.
* **Rust Modules** — native backend logic calls via the local WASM server `mdx-local-server`.

## Guide

Download the archive, extract it, and edit the `.mdx` extension files inside the `pages` folder. **Do not change file names or folder paths.**

### Recommended Editors:

* **For a Quick Start (Notepad++)**
  * Download and install the free **Notepad++** text editor.
  * Right-click the required `.mdx` file and select **"Edit with Notepad++"**.
  * Modify the text or styles and save your changes (`Ctrl + S`).

* **Advanced Option (VS Code)**
  * Download and install **Visual Studio Code (VS Code)**.
  * Open the extracted project directory via `File` -> `Open Folder`.
  * Go to the Extensions tab (`Ctrl + Shift + X`), search for and install the **MDX** plugin (e.g., by *Jonathan Rowny*) for syntax highlighting.
  * Easily manage and edit your files using the built-in file explorer on the left sidebar.
 
* **Editing with Default Windows Notepad**
  * If you prefer not to install any third-party software, the default Windows **Notepad** application can easily open and save these files. The `.mdx` files are essentially plain text files with a custom extension. To do this: Right-click the `.mdx` file, select **"Open with"** → **"Notepad"**. Edit the text and save your work via **`Ctrl + S`**. 
  * **Important note:** Notepad will not damage the underlying code structure upon saving. However, since the built-in Notepad does not support syntax highlighting, all code will appear in a single color. Be extra cautious not to accidentally delete vital brackets, brackets closure, or tags while editing.

Find more on the developer website: https://zhivoglas.com/
Enjoy your creative process!
