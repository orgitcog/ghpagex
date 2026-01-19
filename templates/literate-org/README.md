# Literate Org (org-babel) GitHub Pages Template

This template provides a GitHub Actions workflow for creating and deploying reproducible literate programming documents using Org Mode with Babel support.

## About Literate Org with Babel

Org Babel allows you to execute code blocks within Org Mode documents and include their results in the exported output. This creates reproducible, executable documentation similar to Jupyter notebooks, but with the power and flexibility of Emacs and Org Mode.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Create Org files with embedded code blocks using Babel
4. Ensure you have a `build.el` file to configure and execute the export
5. Push your changes to trigger the workflow

## Requirements

- Org mode files with Babel code blocks (`.org` files)
- A `build.el` file to configure code execution and export
- Optional: Language-specific dependencies for code execution

## Example Literate Org File

```org
#+TITLE: My Literate Program
#+AUTHOR: Your Name

* Introduction

This document demonstrates literate programming with Org Babel.

* Code Example

Here's a simple calculation:

#+BEGIN_SRC emacs-lisp :exports both
(+ 2 2)
#+END_SRC

#+RESULTS:
: 4

* Data Analysis

Let's analyze some data:

#+BEGIN_SRC python :exports both :results output
import numpy as np
data = np.array([1, 2, 3, 4, 5])
print(f"Mean: {np.mean(data)}")
print(f"Std: {np.std(data)}")
#+END_SRC
```

## Example `build.el`

```elisp
(require 'org)
(require 'ob)
(require 'ox-html)

;; Enable Babel for various languages
(org-babel-do-load-languages
 'org-babel-load-languages
 '((emacs-lisp . t)
   (python . t)
   (shell . t)
   (lisp . t)))

;; Don't ask for confirmation before executing code
(setq org-confirm-babel-evaluate nil)

;; Configure HTML export
(setq org-html-validation-link nil)

;; Export all org files
(defun export-org-files ()
  (let ((output-dir "./public"))
    (make-directory output-dir t)
    (dolist (file (directory-files "." t "\\.org$"))
      (unless (string-match-p "/\\." file)
        (with-current-buffer (find-file-noselect file)
          (org-html-export-to-html)
          (let ((html-file (concat (file-name-sans-extension file) ".html")))
            (when (file-exists-p html-file)
              (rename-file html-file 
                          (concat output-dir "/" (file-name-nondirectory html-file))
                          t)))
          (kill-buffer))))))

(export-org-files)
```

## Features

- Executable documentation with results
- Support for multiple programming languages
- Perfect for OpenCog-based reasoning experiments
- Ideal for PLN rule exploration
- Reproducible AGI workflow documentation
- Combines code, results, and explanations

## Learn More

- [Org Babel Documentation](https://orgmode.org/worg/org-contrib/babel/)
- [Literate Programming](http://www.literateprogramming.com/)
- [Working with Source Code](https://orgmode.org/manual/Working-with-Source-Code.html)
- [GitHub Pages Documentation](https://docs.github.com/pages)
