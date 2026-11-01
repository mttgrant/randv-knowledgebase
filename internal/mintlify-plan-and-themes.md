# Mintlify: plans, private access and themes

Checked 2026-11-01 against Mintlify's own pricing page and docs. Plans change often, so re-check before making a decision on these notes.

This folder is listed in `.mintignore`, so these notes are not published to the docs site.

## Current state

- Live site: `rand-v.mintlify.site`, deployed from `main` of `mttgrant/randv-knowledgebase`.
- Content is still the untouched Starter Kit, on the `mint` theme.
- A push to `main` publishes.
- Run locally with `mint dev` (http://localhost:3000).

## Plans

| Feature | Starter ($0) | Pro ($450/mo annual, $540/mo monthly) | Enterprise (custom) |
|---|---|---|---|
| Editor seats | 5 | Unlimited | Unlimited |
| Custom domain | Yes | Yes | Yes |
| Authentication | Mintlify auth | Password auth | OAuth, JWT, SSO |
| Preview deployments | No | Yes | Yes |
| Platform and agent analytics | No | Yes | Yes |
| AI assistant | No | Yes (25 credits per answer) | Yes (25 credits per answer) |
| White labeling | No | No | Yes |

Starter also includes the web editor, Git sync, search, the MCP server, the API playground, and custom components and CSS/JS.

## Making the site private

- Private authentication (sign in with a Mintlify organization account) is available on all plans.
- Everyone who reads the site must be a member of our Mintlify organization. Add them under Members in the dashboard.
- To turn it on: dashboard > Access > set Visibility to Private.
- With authentication on, every page needs sign-in by default. A page or group can be opened with `public: true`.
- Password access needs Pro. It is one shared password with no per-user tracking.
- Group-based restrictions need OAuth or JWT, which means Enterprise.

## How the team and devs edit

Both routes work on the same repo. Starter includes the web editor and Git sync.

| | Team | Devs |
|---|---|---|
| Where | Web editor at https://app.mintlify.com | Local files, previewed with `mint dev` |
| Going live | Edits autosave, then **Publish** commits to `main` and deploys | `git push` to `main` deploys |
| With review | **Create branch**: edits commit automatically and open a pull request | Normal branch and pull request |

- If a push lands while someone is editing, the editor merges it into their open pages. If both touched the same part of a page, it keeps both versions and highlights them for the editor to choose.
- Publish goes straight to the live site when `main` has no branch protection. With pull requests required, the team must use **Create branch**.
- Starter has no preview deployments, so a branch can't be checked on a preview link before merging.
- Viewers don't see **Publish**, so each team member needs a role that can publish.

Recommended before the team starts: require pull requests on `main`. Not done yet.

## Unconfirmed

- Whether web editors need GitHub accounts. The docs don't state it; commits are signed by the Mintlify GitHub App unless a person links their own account.
- Whether any editor branching or publishing feature differs by plan. The docs don't state it.

- Whether read-only members count toward the 5 editor seats on Starter. This decides whether Starter works for the whole team. Neither the authentication docs nor the fields checked on the pricing page say.
- Whether the "Powered by Mintlify" branding can be removed on Starter. No plan lists this directly. White labeling is Enterprise only.
- The site's current visibility. The docs don't state a default, so check dashboard > Access and treat the site as public until then.

## Themes

Set with `"theme": "<value>"` in `docs.json`. Each theme previews at `https://<value>.mintlify.site`.

| Value | Style |
|---|---|
| `mint` | Classic layout and familiar navigation |
| `maple` | Modern and clean, aimed at AI and SaaS products |
| `palm` | Polished fintech style with deep customization |
| `willow` | Minimal, distraction-free |
| `linden` | Retro terminal look with monospace fonts |
| `almond` | Card-based, minimalist |
| `aspen` | Complex navigation and custom components |
| `sequoia` | Minimal and elegant, for large content-heavy docs |
| `luma` | Clean, minimal and polished |

First ones to try for a knowledgebase: `sequoia`, then `almond`.

## Templates and examples

- Page layouts: https://github.com/mintlify/templates. Merge its `docs.json` files into ours; don't copy over ours.
- Customer list and case studies: https://www.mintlify.com/customers
- Community list of live sites: `awesome-mintlify` on GitHub.

## Keeping files off the site

- `.mintignore` removes a file completely: it is not published, not searchable and has no URL. It uses `.gitignore` syntax.
- Hidden pages are different and stay reachable by URL, so don't use them for sensitive content.
- `README.md`, `LICENSE.md`, `CHANGELOG.md` and `CONTRIBUTING.md` are ignored automatically.

## Sources

- https://www.mintlify.com/pricing
- https://www.mintlify.com/docs/deploy/authentication-setup
- https://www.mintlify.com/docs/customize/themes
- https://www.mintlify.com/docs/organize/mintignore
- https://www.mintlify.com/docs/deploy/preview-deployments
- https://www.mintlify.com/docs/editor/branching-and-publishing
- https://www.mintlify.com/docs/editor/publish
