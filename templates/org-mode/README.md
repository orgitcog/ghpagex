# Org Mode GitHub Pages Template

This template provides a GitHub Actions workflow for exporting and deploying Org Mode files to GitHub Pages using Emacs' built-in publishing system (`ox-publish`).

## About Org Mode

Org Mode is a powerful plain-text markup system for Emacs that supports literate programming, task management, and technical documentation. The `ox-publish` system can export Org files to HTML, making it ideal for creating static documentation sites.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `publish.el` file in your repository root that configures `org-publish-project-alist`
4. Add your Org mode files to your repository
5. Push your changes to trigger the workflow

## Requirements

- A `publish.el` file that configures your Org publishing settings
- Org mode source files (`.org` files)
- Optional: Custom CSS and assets

## Example `publish.el`

```elisp
(require 'ox-publish)

(setq org-publish-project-alist
      '(("org-notes"
         :base-directory "."
         :base-extension "org"
         :publishing-directory "./public"
         :recursive t
         :publishing-function org-html-publish-to-html
         :headline-levels 4
         :auto-preamble t)
        ("org-static"
         :base-directory "."
         :base-extension "css\\|js\\|png\\|jpg\\|gif\\|pdf\\|mp3\\|ogg\\|swf"
         :publishing-directory "./public"
         :recursive t
         :publishing-function org-publish-attachment)
        ("org" :components ("org-notes" "org-static"))))
```

## Features

- Native Emacs toolchain
- Supports inline Emacs Lisp execution
- Perfect for literate programming and technical documentation
- Ideal for OpenCog/AGI research documentation
- Lightweight and fast

## Learn More

- [Org Mode Manual](https://orgmode.org/manual/)
- [Org Publishing](https://orgmode.org/manual/Publishing.html)
- [GitHub Pages Documentation](https://docs.github.com/pages)
