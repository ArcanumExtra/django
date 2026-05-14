# Review Policies

## Admin shared CSS and icon assets
- **Paths**: `django/contrib/admin/static/admin/css/**`, `django/contrib/admin/static/admin/img/**`
- **Severity**: high
- **Reason**: Small visual changes in shared admin styles or SVG assets can regress layout/contrast across desktop and responsive views that automated tests may not fully catch.

## Permission rename and post-migrate handlers
- **Paths**: `django/contrib/auth/**`
- **Severity**: critical
- **Reason**: Permission-rename logic runs during migrations; incorrect conflict handling or matching can silently leave inconsistent permissions and create security/authorization drift after migrations are marked complete.

## Instructions
- If a PR mixes functional template fixes with broad whitespace/style cleanup, require human judgment on whether the extra churn is worth the review and regression risk.
- If a PR changes admin spacing/alignment with fixed pixel tweaks, require human review to decide whether it improves one context while regressing responsive or other admin pages.
- If a PR changes how rename/migration conflicts are surfaced (skip, warn, fail, retry, or delete stale data), require human judgment on the operational tradeoff between safety and automation.
