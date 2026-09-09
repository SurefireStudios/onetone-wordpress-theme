# Contributing

Thanks for helping keep OneTone alive. This repository maintains security-patched builds
of the abandoned **OneTone** and **OneTone Pro** WordPress themes.

Contributions that help most:

- 🔐 Security hardening — escaping, sanitization, capability and nonce checks
- 🐘 PHP 8 compatibility fixes
- 🧪 Testing reports against current WordPress and PHP versions
- 📚 Documentation corrections

Found a **security vulnerability**? Do not open a public issue — follow
[SECURITY.md](SECURITY.md) instead.

## How this repository is laid out

There is no source tree here. The themes ship as two ready-to-install archives:

| Archive | Theme folder inside |
| --- | --- |
| `onetone-patched.zip` | `onetone/` |
| `onetone-pro-patched.zip` | `onetone-pro/` |

So a code change means: extract, edit, lint, repackage.

## Working on a change

### 1. Extract

```bash
git clone https://github.com/SurefireStudios/onetone-wordpress-theme.git
cd onetone-wordpress-theme
mkdir -p build && unzip -q onetone-patched.zip -d build
```

That gives you `build/onetone/`. Use `onetone-pro-patched.zip` the same way for Pro.

### 2. Edit

Match the surrounding code. The themes predate modern WordPress conventions, so keep
changes surgical rather than reformatting whole files — a small, reviewable diff is far
easier to verify than a rewrite.

When touching output or input, use WordPress' own APIs:

- Escape on output — `esc_html()`, `esc_attr()`, `esc_url()`, `wp_kses_post()`
- Sanitize on input — `sanitize_text_field()`, `absint()`, `wp_unslash()`
- Gate admin actions — `current_user_can()` plus `check_admin_referer()` / `wp_verify_nonce()`

### 3. Lint

Every PHP file must parse cleanly. CI runs this on each push and pull request:

```bash
find build -name '*.php' -print0 | xargs -0 -n1 php -l
```

Run it locally before opening a pull request.

### 4. Test on a real site

Please verify against a throwaway WordPress install:

- The theme activates without notices
- The homepage template and its sections render
- The Customizer opens and saves options
- If you touched shop templates, WooCommerce pages still work

Note in your pull request which WordPress and PHP versions you tested.

### 5. Repackage

Rebuild the archive with the theme folder at the **root** of the zip — WordPress rejects it
otherwise:

```bash
cd build && zip -qr ../onetone-patched.zip onetone && cd ..
```

Bump the `Version:` header in the theme's `style.css` and add an entry to its `readme.txt`
changelog if the change is user-facing.

## Pull requests

1. Fork the repository and branch from `main`.
2. Keep one logical change per pull request.
3. In the description, cover:
   - What the problem was and how you fixed it
   - Which archive(s) you rebuilt
   - The WordPress and PHP versions you tested against
4. Make sure the PHP lint workflow passes.

## Reporting a bug

[Open an issue](https://github.com/SurefireStudios/onetone-wordpress-theme/issues) with the
theme and version, your WordPress and PHP versions, active plugins that seem relevant, and
the steps to reproduce. Any PHP error or debug-log output is very welcome.

## License

By contributing, you agree that your work is released under the
[GNU General Public License v3.0](LICENSE), the same terms as the rest of this project.
