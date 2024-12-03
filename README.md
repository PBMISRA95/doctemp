# DiMatApp Docs

This repository provides tools to help users create documentation for their applications using **Sphinx** with Markdown (`.md`) files as the primary source. Follow the instructions below for setup, rendering, and contributing.

---

## Table of Contents

1. [Introduction](#introduction)  
2. [Local Rendering](#local-rendering)  
    - [Using Docker](#docker)  
    - [Using Linux](#linux)  
    - [Using VSCode](#vscode)  
3. [Contributing and Reporting Issues](#contributing-and-reporting-issues)  
4. [Advanced Usage](#advanced-usage)  
    - [Customizing Sphinx Configuration](#customizing-sphinx-configuration)  
    - [Markdown Support](#markdown-support)  
5. [FAQs](#faqs)  

---

## 1. Introduction

The **DiMatApp Docs** module simplifies the process of generating and managing application documentation using **Sphinx** with Markdown files as the primary format. Whether you prefer Docker, Linux, or VSCode, this guide provides steps to render and serve your documentation locally.

---

## 2. Local Rendering

You can render the documentation locally using one of the methods below:

### Docker

1. **Build the Docker Image**  
   Run the following command to build the image:

   ```bash
   $ docker build -f Dockerfile.docs -t dimatapp-docs .
   ```

2. **Start the Docker Container**  
   Start the server to render the documentation:

   ```bash
   $ docker run -it --rm -v $PWD:/app -p 8000:8000 dimatapp-docs
   ```

   The documentation will be available at [`http://127.0.0.1:8000`](http://127.0.0.1:8000).

---

### Linux

1. **Install OS-Level Dependencies**  
   For Linux Debian-based systems:

   ```bash
   $ sudo apt install pandoc graphviz default-jre
   $ sudo apt-get install texlive-latex-recommended \
                         texlive-latex-extra \
                         texlive-fonts-recommended \
                         latexmk
   ```

2. **Install Python Dependencies**  
   Ensure Python dependencies are installed:

   ```bash
   $ pip install -r requirements.txt
   ```

3. **Start the Documentation Server**  
   Render the documentation using Sphinx:

   ```bash
   $ sphinx-autobuild docs/source docs/build/html
   ```

   The documentation will be accessible at [`http://127.0.0.1:8000`](http://127.0.0.1:8000).

---

### VSCode

1. **Install Live Server Extension**  
   Ensure you have the [Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) installed in VSCode.

2. **Build the HTML Documentation**  
   Run the following command in the terminal:

   ```bash
   $ make html
   ```

3. **Open Documentation with Live Server**  
   Navigate to the `docs/build/html` directory, right-click on the `index.html` file, and select **"Open with Live Server"**.

4. **View Documentation**  
   The documentation will open in your default web browser at [`http://127.0.0.1:5500`](http://127.0.0.1:5500).

---

## 3. Contributing and Reporting Issues

We welcome contributions and feedback!  

If you find an error or have a feature request, please create an issue in [this repository](https://gitlab.cc-asp.fraunhofer.de/dimat/templates/). Ensure your issue includes a clear description and, if applicable, steps to reproduce the problem.

---

## 4. Advanced Usage

### Customizing Sphinx Configuration

To customize your Sphinx setup for Markdown-based documentation, edit the `conf.py` file in the `docs/source` directory. Ensure the following extensions are enabled to support Markdown:

```python
extensions = [
    'myst_parser',  # Required for Markdown support
]
```

You can also define other configurations like themes, static assets, or additional extensions.

### Markdown Support

This project uses **MyST-Parser** to enable Markdown file compatibility with Sphinx. You can use Markdown syntax to create `.md` files, and Sphinx will parse these files to generate HTML documentation.

Refer to the [MyST-Parser documentation](https://myst-parser.readthedocs.io/) for advanced Markdown features, such as:

- Inline directives and roles
- Content includes
- Math and equations using `$...$`

---

## 5. FAQs

**1. How do I add new pages to the documentation?**  
   - Create a new `.md` file in the `docs/source` directory.  
   - Add the file to the `toctree` in the `index.md` file. Example:

     ```markdown
     ```{toctree}
     :maxdepth: 2
     :caption: Contents:

     new_page.md
     ```
     ```

**2. Can I use reStructuredText (`.rst`) along with Markdown?**  
   - Yes! Sphinx supports both formats. You can mix `.rst` and `.md` files in the same project, but ensure that all files are referenced in the `toctree`.

**3. How can I customize the appearance of the documentation?**  
   - Modify the `html_theme` and related options in `conf.py`. For example, to use the "Read the Docs" theme:

     ```python
     html_theme = 'sphinx_rtd_theme'
     ```

**4. Why is the Markdown file not rendering correctly?**  
   - Ensure the **MyST-Parser** is installed and added to the `extensions` in `conf.py`.  
   - Validate your Markdown syntax using a linter.

**5. How do I ensure a fresh build of the documentation?**  
   - Sometimes, rebuilding the documentation requires clearing the old build files to avoid interference with new content. To do this:
     1. Run the following command to delete the `_build` directory:

        ```bash
        $ make clean
        ```

     2. After cleaning, rebuild the documentation using:

        ```bash
        $ make html
        ```

     This ensures that the documentation is built fresh and includes only the latest changes.

---

For further assistance, feel free to raise an issue or consult the [Sphinx documentation](https://www.sphinx-doc.org/en/master/) and [MyST-Parser documentation](https://myst-parser.readthedocs.io/).

---
