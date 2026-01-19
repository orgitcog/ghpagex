# Texinfo HTML GitHub Pages Template

This template provides a GitHub Actions workflow for generating HTML manuals from Texinfo (`.texi`) files and deploying them to GitHub Pages.

## About Texinfo

GNU Texinfo is the official documentation format of the GNU project. It's ideal for creating comprehensive manuals for Emacs Lisp systems, Common Lisp projects, and other software documentation. Texinfo files can be converted to multiple formats including HTML, PDF, and Info files.

## Usage

1. Copy the `deploy.yml` file to `.github/workflows/` in your repository
2. Update the `branches: [$default-branch]` to match your default branch (e.g., `main` or `master`)
3. Ensure you have `.texi` source files in your repository
4. Optional: Customize the `makeinfo` options in the workflow
5. Push your changes to trigger the workflow

## Requirements

- Texinfo source files (`.texi` files)
- A main documentation file (e.g., `manual.texi`)
- Optional: Custom CSS for HTML styling

## Example Texinfo File Structure

```
repository/
├── manual.texi          # Main documentation file
├── intro.texi           # Chapter files (optional)
├── api.texi
└── appendix.texi
```

## Basic Texinfo Example

```texinfo
\input texinfo @c -*-texinfo-*-
@setfilename manual.info
@settitle My System Manual

@titlepage
@title My System Manual
@author Your Name
@end titlepage

@node Top
@top My System

This is the manual for my system.

@menu
* Introduction::
* API Reference::
@end menu

@node Introduction
@chapter Introduction

Welcome to the manual...

@bye
```

## Features

- GNU-standard documentation format
- Clean, professional output
- Perfect for Emacs Lisp and Common Lisp system documentation
- Ideal for AtomSpace or PLN module documentation
- Cross-reference support
- Multiple output format support

## Learn More

- [Texinfo Manual](https://www.gnu.org/software/texinfo/manual/texinfo/)
- [Writing Texinfo Documentation](https://www.gnu.org/software/texinfo/manual/texinfo/html_node/index.html)
- [GitHub Pages Documentation](https://docs.github.com/pages)
