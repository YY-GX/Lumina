# Contributing to Lumina

Thank you for your interest in contributing to Lumina! This guide will help you get started.

## How to Contribute

1. **Fork** the repository on GitHub.
2. **Clone** your fork locally.
3. **Create a branch** for your change (`git checkout -b my-feature`).
4. **Make your changes** and commit them with clear messages.
5. **Push** your branch to your fork and open a **Pull Request**.

## Development Setup

```bash
git clone https://github.com/yourusername/lumina.git
cd lumina
npm install
npm run dev      # starts dev server at http://localhost:4321
```

Run a production build to verify everything works:

```bash
npm run build
npm run preview
```

## Pull Request Process

1. Ensure your PR targets the `main` branch.
2. Describe what your change does and why it is needed.
3. Include screenshots for any visual changes.
4. Make sure the project builds without errors (`npm run build`).
5. Keep PRs focused -- one feature or fix per PR.

## Code Style

- Use **TypeScript** where possible.
- Follow the existing code conventions in the repository.
- Use [Tailwind CSS](https://tailwindcss.com/) utility classes for styling.
- Keep components small and focused.
- Use semantic HTML elements for accessibility.

## Reporting Bugs

If you find a bug, please [open an issue](../../issues/new) with:

- A clear, descriptive title.
- Steps to reproduce the problem.
- Expected behavior vs. actual behavior.
- Browser and OS information.
- Screenshots or error messages, if applicable.
