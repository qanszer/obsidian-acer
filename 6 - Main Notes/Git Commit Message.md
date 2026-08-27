
2025-09-14  19:10

Tags: [[Terminal]], [[Git]], [[Github]], [[Coding]], [[The Odin Project]]

---

# Git Commit Message


**The seven rules of a great Git commit message**
1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how

Example:
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequences of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789

====

git log --oneline
git shortlog 

google-chrome index.html

====

Git Commit Template:

```

<Type>(optional scope): <description>

[Optional body]

[Optional-footer(s):<text>]

```


---

## **Mandatory Core Types**

- **feat**: A new feature for the user, not a new feature for a build script.
- **fix**: A bug fix for the user, not a fix to a build script.

### **Standard Conventional Types**

- **docs**: Changes to the documentation only (like README.md or code comments).
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
- **refactor**: A code change that neither fixes a bug nor adds a feature.
- **perf**: A code change that improves performance.
- **test**: Adding missing tests or correcting existing tests.
- **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm).
- **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, GitHub Actions).
- **chore**: Other changes that don't modify src or test files (e.g., updating .gitignore).
- **revert**: Reverting a previous commit.

### **Anatomy of a Conventional Commit**

```git
<type>[optional scope]: <description>
[optional body]
[optional footer(s)]
```

## **Breaking Changes**

Any commit type can be marked as a **Breaking Change** (which triggers a Major semantic version bump) by adding a `!` immediately after the type or scope, or by adding `BREAKING CHANGE:` in the footer.

- _Example:_ `feat(api)!: send logging to external service`


---

## Optional Scopes

In Conventional Commits, the **scope** must be a noun wrapped in parentheses that immediately identifies the specific module, component, or section of the codebase affected by the new feature.

Here are the most useful and widely used examples of scopes for `feat`, categorized by application layer and architecture:

1. Authentication & Security

- `feat(auth):` Implementing login, registration, JWT tokens, OAuth, or 2FA.
- `feat(rbac):` Role-Based Access Control, user permissions, or admin privileges.
- `feat(session):` Session timeouts, cookies, or multi-device logout.

2. Frontend & User Interface

- `feat(ui):` Generic global UI components like buttons, modals, or dropdowns.
- `feat(nav):` Navigation bars, sidebars, routing, or breadcrumbs.
- `feat(theme):` Adding dark mode, custom styling variables, or localization/i18n.
- `feat(dashboard):` Adding a new metrics panel, user feed, or landing view.

3. Backend & API Layer

- `feat(api):` Global routing changes, new endpoints, or middleware additions.
- `feat(db):` Database migrations, new schemas, or indexing optimizations.
- `feat(worker):` Background jobs, cron tasks, or asynchronous queues (e.g., Celery, BullMQ).
- `feat(webhook):` Integrating third-party incoming payloads or outgoing event alerts.

4. Data & Core Processing

- `feat(search):` Implementing Elasticsearch, search filters, or autocomplete.
- `feat(billing):` Stripe integrations, checkout carts, invoices, or subscription tier changes.
- `feat(notify):` Email notifications, SMS alerts, or in-app push alerts.
- `feat(upload):` File uploads, AWS S3 image compression, or drag-and-drop file inputs.

5. Devops & Tooling

- `feat(config):` App-wide configuration, environment variables, or feature flags.
- `feat(logging):` Setting up Datadog, Sentry error tracking, or application telemetry.

**Pro-Tips for Defining Scopes**

- **Keep it short:** Use a single word or short hyphenated slug (e.g., `feat(user-profile):`).
- **Do not use filenames:** Use `feat(auth):` instead of `feat(auth-controller.ts):`.
- **Team alignment:** Keep a dictionary of allowed scopes in your project's `README.md` or enforce them strictly via a `commitlint.config.js` file.


---

# References

1. https://www.theodinproject.com/lessons/foundations-commit-messages#introduction
2. https://www.conventionalcommits.org/en/v1.0.0/