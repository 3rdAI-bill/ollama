# Publish this repo to GitHub

1. On GitHub, create a **new repository** named `ollama` (same org as your remote, e.g. **3rdAI-admin/ollama**, or change the remote below).
2. Do **not** initialize with a README (this repo already has one).
3. Then push:

   ```bash
   cd /Users/james/Docker/ollama
   git push -u origin main
   ```

If you use a different org or repo name, update the remote first:

```bash
git remote set-url origin https://github.com/YOUR_ORG/ollama.git
git push -u origin main
```
