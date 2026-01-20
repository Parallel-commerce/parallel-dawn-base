You are working inside a Shopify Online Store 2.0 theme derived from Dawn. You must follow Shopify/Dawn conventions strictly.

Core principles

* Preserve Dawn’s architecture, accessibility, and progressive enhancement patterns.
* Prefer minimal, scoped changes. Do not “rebuild” existing Dawn sections unless explicitly instructed.
* Option A styling approach: keep Dawn component classes and layer Parallel styling via section wrapper classes and dedicated section CSS files.

Naming and prefixing

* All new sections must be named: sections/parallel-<name>.liquid
* All new section CSS must be named: assets/section-parallel-<name>.css
* All new snippets must be named: snippets/parallel-<name>.liquid (render-only helpers)
* Do not create new top-level folders or introduce build tooling.

CSS rules (strict)

* !important is forbidden by default.
* It may be used only when overriding third-party injected or inline styles that cannot be controlled, and must be:

  * narrowly scoped
  * accompanied by a short comment explaining why it is unavoidable
* Do not add generic global selectors to “fix” layouts (no blanket styling of a, button, div, section, *, etc).
* Prefer: section wrapper scoping, Dawn CSS variables/tokens, and section-specific CSS.

“Do not overwrite styles” guardrails

* Do not edit base.css or global component CSS unless explicitly required and justified.
* New styling should live in section-parallel-*.css and be scoped under a wrapper class unique to that section.
* Do not increase specificity excessively. Avoid long selector chains.

Markup and class rules

* Do not remove or rename Dawn classes unless explicitly required for function. In Option A, you generally keep Dawn markup/classes.
* Do not attach JS behaviour to visual/styling classes. Use data attributes or custom elements consistent with Dawn.

Section requirements

* Every new parallel section must:

  * include a complete {% schema %} with sensible defaults and presets
  * support blocks where content is repeatable
  * render a single top-level wrapper with both generic and specific classes:

    <section class="parallel-section parallel-<name>"> ... </section>
  * load its CSS via standard Dawn pattern (stylesheet_tag) and only when the section is used

Definition of Done (for every change)
When you propose or implement changes, always output:

1. Files changed
2. What changed and why
3. How to verify in Theme Editor and storefront
4. Any migration notes if schema/settings changed

If any instruction conflicts, follow this document.