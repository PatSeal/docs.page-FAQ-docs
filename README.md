# Web Development Handbook

A practical, beginner-friendly web development guide built for [docs.page](https://docs.page).

The handbook starts with how browsers and servers communicate, then moves through HTML, CSS, JavaScript, object-oriented frontend architecture, backend APIs, databases, testing, security, deployment, and production maintenance. Application examples use encapsulated classes, composition, dependency injection, repository contracts, polymorphism, and the SOLID principles. Node.js, Express, and SQL provide a concrete full-stack stack.

## Read the documentation

After the changes are pushed to GitHub, the published handbook is available at:

<https://docs.page/PatSeal/docs.page-FAQ-docs>

docs.page reads `docs.json` and the MDX files under `docs/` directly from the repository. There is no local build step.

## Repository structure

```text
docs.json                 Site title, theme, and sidebar navigation
docs/
  index.mdx                       Main integration and implementation hub
  getting-started/
    index.mdx                     Section landing page
    *.mdx                         Web overview and first project pages
  fundamentals/
    index.mdx                     Section landing page
    *.mdx                         HTML, CSS, JavaScript, OOP, and DOM pages
  frontend/
    index.mdx                     Section landing page
    *.mdx                         Views, controllers, forms, accessibility, performance
  backend/
    index.mdx                     Section landing page
    *.mdx                         Use cases, APIs, validation, and authentication
  data/
    index.mdx                     Section landing page
    *.mdx                         Databases, repositories, SQL, and safe queries
  full-stack/
    index.mdx                     Section landing page
    *.mdx                         SOLID architecture, tutorial, tests, and security
  deployment/
    index.mdx                     Section landing page
    *.mdx                         Production, CI/CD, and monitoring
  reference/
    index.mdx                     Section landing page
    *.mdx                         Git, roadmap, OOP checklist, glossary, and FAQ
```

## Folder convention

- `docs/index.mdx` is the only page stored directly under `docs/`. It connects the sections and explains the complete implementation flow.
- Every section is a folder.
- Every section folder contains an `index.mdx` landing page.
- Every topic page belongs inside its section folder.
- `docs.json` mirrors the same folder structure in the sidebar.
- Internal links use the folder route: `docs/frontend/index.mdx` becomes `/frontend`, and `docs/frontend/forms-and-data.mdx` becomes `/frontend/forms-and-data`.

## Edit the handbook

1. Choose the section folder that owns the topic.
2. Edit its `index.mdx` or add the topic as another `.mdx` file inside that folder.
3. Update the section landing page when the new topic changes the recommended reading order.
4. Add or rename the matching entry in `docs.json`.
5. Link from the main `docs/index.mdx` only when the topic changes the end-to-end implementation path.
6. Use a root-relative internal link such as `/fundamentals/html`.
7. Preview a pushed branch at `https://docs.page/PatSeal/docs.page-FAQ-docs~branch-name`, or run `npx @docs.page/cli preview` locally.
8. Check the page on both a wide screen and a phone-sized screen before merging.

## Content principles

- Explain the idea before introducing syntax.
- Use short examples that demonstrate one concept at a time.
- Define unfamiliar terms when they first appear.
- Prefer standards and transferable concepts over framework-specific tricks.
- Keep application behavior behind cohesive object interfaces and inject dependencies.
- Prefer composition over inheritance unless the subtype is genuinely substitutable.
- Make every class responsible for one reason to change.
- Never place passwords, API keys, or other secrets in examples or commits.

## License

No license file is currently included. Add one before redistributing the content outside this repository.
