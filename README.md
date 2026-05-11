# ShelfTrack

A lightweight, GitHub-backed shelf inventory manager. No server required — all data lives in `inventory.csv` in this repository and is read/written directly via the GitHub API.

## Setup

### 1. Create your repository
Create a new GitHub repository (can be public or private).

### 2. Add the files
Upload both files to the repository root:
- `index.html` — the web app
- `inventory.csv` — your inventory data

### 3. Enable GitHub Pages
Go to **Settings → Pages**, set source to **Deploy from a branch**, pick `main` (or your branch) and `/ (root)`. Your site will be live at `https://<username>.github.io/<repo>/`.

### 4. Create a Personal Access Token
Go to **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens** (or classic tokens with `repo` scope). Make sure it has **read and write access to repository contents**.

> ⚠️ Keep your token private. Anyone with the token can modify your CSV. For a private repo + small team this is fine; don't publish your token publicly.

### 5. Configure the app
Open your GitHub Pages URL, expand **GitHub Configuration**, fill in:
- **Owner** — your GitHub username or org name
- **Repository** — the repo name
- **CSV File Path** — `inventory.csv` (or wherever you placed it)
- **Branch** — `main`
- **Token** — your PAT

Click **Save & Load Inventory**. Your items will appear.

## CSV Format

```
id,name,shelf,status,user
ITEM-001,Red Binder,1,in,Alice
ITEM-002,Blue Folder,2,out,Bob
```

| Column | Description |
|--------|-------------|
| `id` | Unique identifier for the item |
| `name` | Human-readable item name |
| `shelf` | Shelf number the item lives on |
| `status` | `in` (checked in) or `out` (checked out) |
| `user` | Name of the person who last checked it in/out |

You can edit `inventory.csv` directly in GitHub or via the app.

## Features

- **Search by ID** — look up any item instantly
- **Check In / Check Out** — updates status and records the user's name
- **Add Items** — adds a new row to the CSV via the GitHub API
- **Live table** — see all items at a glance
- All changes are committed to the CSV with descriptive commit messages

## Tips

- Config (owner, repo, path, branch) is saved to `localStorage` so you don't need to re-enter it. The token is intentionally **not** saved for security.
- For a shared team setup, each person enters their own token when they visit the page.
- You can pre-populate `inventory.csv` by editing it directly on GitHub.
