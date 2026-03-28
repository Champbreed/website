---
title: Reviewing changes
content_type: concept
weight: 30
---

<!-- overview -->

This section describes how to review content to ensure the Kubernetes website remains stable and accurate.
While Netlify provides automated previews, certain infrastructure changes require extra manual verification. 
This guide outlines the mandatory steps for high-impact web changes.

<!-- body -->

## Mandatory Local Testing for Web Changes

For any Pull Request involving **Hugo upgrades**, **Docsy theme updates**, or changes to the site's build configuration, a successful Netlify preview is **not enough**.
Reviewers must verify that the site builds correctly in production mode to ensure the asset pipeline (minification and fingerprinting) is functional.

### Hugo production build

Reviewers or authors must perform a local build in production mode:

1. Sync your local environment with the PR branch and update dependencies:

   ```bash
    npm install
    ```
2. Run the following command locally:

   ```bash
   HUGO_ENV=production hugo --gc --minify
   ```
3. Verify the output:

Confirm the build completes without `failed to transform` or path resolution errors. If the local production build fails, 
the PR must not be merged, regardless of the Netlify preview status.


