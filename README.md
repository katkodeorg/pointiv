# Pointiv

Pointiv adds AI actions, tools, and extensions to selected text on macOS. Highlight text in any app, press a shortcut, and run the action you need without switching to a separate chat window.

[Website](https://pointiv.katkode.com) | [Developer Guide](https://pointiv.katkode.com/developers) | [Releases](https://github.com/katkodeorg/pointiv/releases) | [Homebrew Tap](https://github.com/katkodeorg/homebrew-tap)

## Install

Pointiv supports macOS 12 Monterey or later.

Install with Homebrew:

```bash
brew tap katkodeorg/tap
brew install --cask pointiv
```

Or install manually:

1. Download the latest `Pointiv_x.x.x_aarch64.dmg` from [Releases](https://github.com/katkodeorg/pointiv/releases).
2. Open the DMG and drag `Pointiv.app` to Applications.
3. Open Pointiv from Applications.

If macOS blocks the first launch, right-click `Pointiv.app`, choose **Open**, then confirm **Open**. You can also remove the quarantine flag:

```bash
xattr -dr com.apple.quarantine /Applications/Pointiv.app
```

## Update and Uninstall

Update a Homebrew install:

```bash
brew update
brew upgrade --cask pointiv
```

Uninstall the app and keep local data:

```bash
brew uninstall --cask pointiv
```

Remove the app and local data:

```bash
brew uninstall --cask pointiv --zap
```

## What Pointiv Does

Pointiv is built for quick actions on the text or context already in front of you.

- Rewrite, summarize, explain, translate, and improve text with AI.
- Run local tools for clipboard, JSON, regex, text transforms, screen capture, previews, and typing output back into the previous app.
- Create Google Calendar events and Gmail drafts from selected notes, with confirmation before sending.
- Schedule extension jobs and track them in the Tasks panel.
- Save useful snippets to encrypted local memory.
- Install community extensions from GitHub.

## How It Works

1. Select text or copy something useful.
2. Press `Cmd+Shift+P`.
3. Type a command or pick a suggested action.
4. Copy, preview, type, schedule, save, or send the result.

## Built-In Actions

- Input: selected text, clipboard, and screen capture.
- Tools: text transform, JSON converter, regex match, Calendar, Gmail, and vim-style background app editing.
- Output: copy to clipboard, type into the previous app, show confirmation, and show overlay.
- Core: memory, scheduler, history, dialogs, and settings.

## Extensions

Extensions are installed from GitHub. Each extension repo contains a `pointiv-extension.json` manifest and an artifact such as `extension.wasm`.

Build one from the Rust template:

```bash
git clone https://github.com/katkodeorg/example_extension_rust.ptr
cd example_extension_rust.ptr
./build.sh
```

Commit `extension.wasm`, `pointiv-extension.json`, and your source changes. Push to GitHub, then paste your repo URL in Pointiv at Settings > Extensions:

```text
https://github.com/<your-username>/<your-extension-repo>
```

Resources:

- [Extension developer guide](https://pointiv.katkode.com/developers)
- [Rust/WASM template](https://github.com/katkodeorg/example_extension_rust.ptr)
- [Rust SDK crate](https://crates.io/crates/pointiv-extension-api)
- [SDK source](https://github.com/katkodeorg/pointiv-extension-api)

Example manifest:

```json
{
  "id": "community.your-name.my-extension",
  "name": "My Extension",
  "description": "What it does",
  "version": "1.0.0",
  "author": "your-name",
  "keywords": ["tag"],
  "runtime": "wasm",
  "main": "extension.wasm",
  "permissions": ["storage", "network"]
}
```

## Extension Permissions

Extensions declare permissions before they can use host APIs.

- `storage`: per-extension key/value storage with JSON helpers.
- `clipboard_read`: read clipboard contents.
- `network`: make outbound HTTP requests.
- `ai`: call Pointiv AI.
- `google_calendar`: create Google Calendar events.
- `google_gmail`: send Gmail messages.

## Privacy and Local Data

Pointiv stores app data locally by default. Data leaves your Mac only when you use AI, Google tools, or an extension with network/API permissions.

Local files:

- `~/.pointiv/auth.json`: stored JWT, email, and plan.
- `~/.pointiv/history.db`: local command history.
- `~/.pointiv/rag.db`: encrypted memory store.
- `~/.pointiv/vault.key`: AES-256 encryption key.
- `~/.pointiv/scheduler.db`: scheduled job queue.
- `~/.pointiv/permissions.json`: granted extension permissions.
- `~/.pointiv/captures/`: screenshots from screen capture.

## Related Projects

- Website: [katkodeorg/pointiv-website](https://github.com/katkodeorg/pointiv-website)
- Homebrew tap: [katkodeorg/homebrew-tap](https://github.com/katkodeorg/homebrew-tap)
- Extension SDK: [katkodeorg/pointiv-extension-api](https://github.com/katkodeorg/pointiv-extension-api)
- Extension template: [katkodeorg/example_extension_rust.ptr](https://github.com/katkodeorg/example_extension_rust.ptr)

## Support and Contributing

Use [GitHub Issues](https://github.com/katkodeorg/pointiv/issues) for bug reports, feature requests, install problems, and extension ideas.

## License

This release repository does not currently include a `LICENSE` file.
