# eSoul WP docker template

## One-command install on a server

On a fresh server with Docker, PHP CLI and MySQL client available, you can bootstrap a new project directory
by downloading the template from GitHub (without git clone) and running the installer in one step.

Replace `<owner>`, `<repo>` and `<ref>` with your GitHub details (for example, a tagged release like `v1.0.0`).

### Using curl

```bash
curl -fsSL https://raw.githubusercontent.com/<owner>/<repo>/<ref>/scripts/remote-bootstrap.sh \
  | bash -s -- \
    --ref <ref> \
    --target-dir my-wp-site \
    --domain mysite.local \
    --db-name wp_db \
    --db-user wp_user \
    --db-pass 'supersecret' \
    --admin admin:admin@mysite.local
```

### Using wget

```bash
wget -qO- https://raw.githubusercontent.com/<owner>/<repo>/<ref>/scripts/remote-bootstrap.sh \
  | bash -s -- \
    --ref <ref> \
    --target-dir my-wp-site \
    --domain mysite.local \
    --db-name wp_db \
    --db-user wp_user \
    --db-pass 'supersecret' \
    --admin admin:admin@mysite.local
```

Bootstrap script options:

- `--repo URL` – override the GitHub HTTPS URL (defaults to `https://github.com/<owner>/<repo>` inside the script).
- `--ref REF` – branch or tag to download (defaults to `main`).
- `--target-dir DIR` – directory to extract into (defaults to `WP-project-template`).
- `--overwrite` – delete existing target directory before download.
- `--reuse-existing` – skip download if target directory already exists and just run `scripts/install.sh` inside it.

All other flags are passed directly to `scripts/install.sh` (e.g. `--domain`, `--db-name`, `--db-user`, `--db-pass`, `--admin`, `--no-db-import`, `--force`).
