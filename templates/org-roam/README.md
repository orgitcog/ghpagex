# Org-Roam GitHub Pages Template

This template provides a GitHub Actions workflow for deploying org-roam or Denote knowledge bases as searchable static sites.

## About Org-Roam

Org-roam is a Roam Research replica for Emacs, built on top of the Org Mode ecosystem. It provides a powerful way to manage interconnected notes in a Zettelkasten-style knowledge graph, which is particularly useful for AGI research and knowledge management.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have a `build-site.el` file that exports your org-roam notes to HTML
4. Add your org-roam database and note files to your repository
5. Push your changes to trigger the workflow

## Requirements

- Org-roam database and note files
- A `build-site.el` script to export notes to HTML
- Optional: Custom CSS for styling your knowledge graph

## Example `build-site.el`

```elisp
(require 'org)
(require 'org-roam)
(require 'ox-html)

;; Initialize org-roam
(setq org-roam-directory (expand-file-name "."))
(setq org-roam-db-location (expand-file-name "org-roam.db"))

;; Configure HTML export
(setq org-html-validation-link nil)
(setq org-html-head-include-default-style nil)

;; Export all org-roam files to HTML
(defun export-all-org-roam-files ()
  (let ((output-dir "./public"))
    (make-directory output-dir t)
    (dolist (file (org-roam-list-files))
      (with-current-buffer (find-file-noselect file)
        (org-html-export-to-html)
        (let ((html-file (concat (file-name-sans-extension file) ".html")))
          (when (file-exists-p html-file)
            (rename-file html-file 
                        (concat output-dir "/" (file-name-nondirectory html-file))
                        t)))
        (kill-buffer)))))

(export-all-org-roam-files)
```

## Features

- Deploy knowledge graphs as static sites
- Perfect for Zettelkasten-style note systems
- Ideal for AGI research documentation
- Mirrors Hyperon's link structures
- Searchable and navigable knowledge base

## Learn More

- [Org-Roam Documentation](https://www.orgroam.com/)
- [Denote Package](https://protesilaos.com/emacs/denote)
- [Zettelkasten Method](https://zettelkasten.de/introduction/)
- [GitHub Pages Documentation](https://docs.github.com/pages)
