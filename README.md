# Github Sandbox

# 📥 Download Files via Commit Message

A GitHub Actions workflow that lets you download files into your repository just by writing a special commit message 
no terminal or command line needed.

---

## ⚙️ Setup

0. Fork this repo
1. Go to your repository on GitHub
2. Click **Settings** → **Actions** → **General**
3. Scroll down to **Workflow permissions**
4. Select **Read and write permissions** and click **Save**
5. Finish

That's it — no tokens or secrets needed.

---

## 🚀 Usage

You trigger downloads by editing any file directly on GitHub and using a special commit message when saving.

### How to trigger a download

1. Open any file in your repository on GitHub (for example, this `README.md`)
2. Click the **pencil icon** (✏️) at the top right to edit it
3. Make any small change (add a space, a blank line, anything)
4. Scroll down to the **Commit changes** section
5. Select **Commit directly to the `main` branch**
6. In the commit message box, type one of the commands below
7. Click **Commit changes**

The workflow will run automatically and the downloaded files will appear in the `downloads/` folder.

---

## 📝 Commands

### Download files individually

Downloads each file and saves it by its original filename.

```
download: URL1 URL2 URL3
```

**Examples:**

```
download: https://example.com/file.zip
download: https://example.com/a.zip https://example.com/b.pdf https://example.com/c.zip
```

---

### Download and archive into a single ZIP

Downloads all files and bundles them into one timestamped `.zip` archive saved to `downloads/`.

```
download-zip: URL1 URL2 URL3
```

**Examples:**

```
download-zip: https://example.com/file.zip
download-zip: https://example.com/a.zip https://example.com/b.pdf https://example.com/c.zip
```

The resulting archive will be named like: `archive_20250423_153012.zip`

---

### Download Telegram (New! ✨) ### 
Downloads directly from a public Telegram post link!
Only Video && Audio

**Examples:**

```
download-tg: https://t.me/channelname/1234
```

---

## 📁 Output

| Command | Result |
|---|---|
| `download:` | Each file saved individually in `downloads/` with its original name |
| `download-zip:` | All files bundled into a single `archive_YYYYMMDD_HHMMSS.zip` in `downloads/` |
| `download-tg:` | Telegram file saved individually in `downloads/` with its original name |

---

## 👀 Checking the result

After committing, you can monitor the workflow:

1. Click the Actions tab in your repository to see progress and logs.
2. Once it completes, simply open the Links.md file in your repository!
3. **Links.md** acts as your personal database, automatically generating and logging direct, clickable download links for all your successfully downloaded files, beautifully grouped by date.

---

## ⚠️ Notes

- URLs must be publicly accessible (no login required)
- Separate multiple URLs with spaces
- The workflow skips itself using `[skip ci]` in its own commit message to avoid infinite loops
- If no valid `download:` or `download-zip:` command is found in the commit message, the workflow will exit without doing anything.(You can also manually find the files in the downloads/ folder).
- Due to the **100 MB** limit from GitHub, we set the maximum size allowed for each file to 90 MB by default. If the file size is higher than this value, it will be split and compressed (zip). On Android, you can use applications like MiXplorer to join the split files together.On Windows, you can use WinRAR or 7-Zip for this purpose.

---

## 👀 Download Link Structure
```
https://github.com/nzrmohammad/github-sandbox/raw/refs/heads/main/downloads/filename
```
