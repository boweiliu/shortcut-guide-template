# shortcut-guide

Interactive guide to a desktop shortcut prototype for Imbue Studio: press Option+N from any Mac app to bring Studio
forward and raise the chat of the machine you have selected. A single static page
(`src/shortcut_guide/assets/guide.html`) served by a small Flask app; it keeps no data of its own.

## Run

The app runs as a window inside an Imbue Studio workspace; its supervisord program starts it. To run it by hand from the
workspace root:

```
uv sync --locked --project system/apps/shortcut_guide
system/apps/shortcut_guide/.venv/bin/shortcut-guide
```

- Port: `SHORTCUT_GUIDE_PORT` (default `8193`), bound on `127.0.0.1`.
- Data folder: `SHORTCUT_GUIDE_DATA_DIR` (default `data/.apps/shortcut-guide`; the app writes nothing there today).
- Routes: `/` (the guide), `/health`, `/_static/<name>` (two browser modules, `app_contract.js` and `context_menu.js`,
  read from the workspace shell's static folder).

## Test

`test_shortcut_guide_ratchets.py` holds the workspace's standard code-quality ratchets, including the type check with
`ty`. Run `uv run --project system/apps/shortcut_guide pytest` from the workspace root.

## Make it yours

The page is plain HTML in `assets/guide.html`: replace the copy and the example machine name, the three-step
walkthrough, or the "what comes next" list with your own product idea.
