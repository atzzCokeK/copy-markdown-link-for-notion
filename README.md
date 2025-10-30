# Copy Markdown Link for Notion

A Raycast extension that copies the current Notion page as a Markdown link in the format `[title](url)`.

## Features

- ✅ Works with Notion desktop app (both normal and fullscreen windows)
- ✅ Automatically extracts page title and URL
- ✅ Generates Markdown link: `[Page Title](https://notion.so/...)`
- ✅ Copies to clipboard with visual feedback
- ✅ Escapes special characters in title (e.g., `[`, `]`)
- ✅ Normalizes `notion://` URLs to `https://`

## Requirements

- macOS
- [Raycast](https://raycast.com/)
- Notion desktop app

## Installation

### From Raycast Store (Recommended)

Install from the [Raycast Store](https://www.raycast.com/a2c/copy-markdown-link-for-notion)

### Manual Installation for Development

1. Clone this repository:
```bash
git clone https://github.com/atzzCokeK/copy-markdown-link-for-notion.git
cd copy-markdown-link-for-notion
```

2. Install dependencies:
```bash
npm install
```

3. Build the extension:
```bash
npm run build
```

4. Import the extension in Raycast:
   - Open Raycast
   - Go to Extensions
   - Click "Add Extension"
   - Select this directory

## Usage

1. Open a Notion page in the Notion desktop app
2. Trigger the extension via Raycast (search for "Copy Markdown Link for Notion")
3. The Markdown link will be copied to your clipboard and displayed in a HUD

**Example output:**
```markdown
[My Project Documentation](https://www.notion.so/My-Project-Documentation-abc123)
```

## Permissions

This extension requires **Accessibility permissions** for Raycast to:
- Detect the frontmost application
- Read window titles
- Simulate keyboard shortcuts (Cmd + L)

If the extension doesn't work, check:
1. Open **System Settings** → **Privacy & Security** → **Accessibility**
2. Ensure **Raycast** is enabled

## How It Works

1. Checks if Notion is the frontmost application
2. Closes Raycast window to avoid interfering with keyboard shortcuts
3. Uses AppleScript to:
   - Get the page title from the window's AXTitle attribute
   - Trigger Cmd + L to copy the page URL
4. Formats the title and URL as a Markdown link
5. Copies to clipboard and shows a HUD notification

## Development

```bash
# Install dependencies
npm install

# Run in development mode
npm run dev

# Build for production
npm run build

# Lint code
npm run lint

# Fix linting issues
npm run fix-lint
```

## Troubleshooting

**"Please open Notion" message**
- Make sure the Notion desktop app is open and in focus

**"Failed to copy Notion link"**
- Ensure you're on a valid Notion page (not settings or empty views)
- Check that Raycast has Accessibility permissions

**Empty title or URL**
- Try again after ensuring the Notion page is fully loaded
- Check that Cmd + L works manually in Notion

## License

MIT

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.
