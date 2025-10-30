# Copy Markdown Link for Notion

A Raycast extension that copies the current Notion page as a Markdown link in the format `[title](url)`.

## Features

- ✅ Works with Notion desktop app (both normal and fullscreen windows)
- ✅ Automatically extracts page title and URL
- ✅ Generates Markdown link: `[Page Title](https://notion.so/...)`
- ✅ Copies to clipboard with visual feedback
- ✅ Escapes special characters in title (e.g., `[`, `]`)
- ✅ Preserves previous clipboard content on failure

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
2. Saves current clipboard content (restored on failure)
3. Closes Raycast window to avoid interfering with keyboard shortcuts
4. Uses AppleScript to:
   - Iterate through UI elements to find the window's AXTitle attribute (works in fullscreen)
   - Focus the window explicitly
   - Trigger Cmd + L to copy the page URL to clipboard
5. Validates the URL contains "notion.so"
6. Escapes square brackets in the title
7. Formats as a Markdown link: `[title](url)`
8. Copies to clipboard and shows a HUD notification with the result

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

**"Please open Notion (current: ...)" message**
- Make sure the Notion desktop app is open and the frontmost (focused) application
- The message shows which app is currently frontmost

**"Failed to copy Notion link. Please try again."**
- The URL doesn't contain "notion.so" (you might be on settings or an invalid page)
- Ensure you're on a valid Notion page (not settings or empty views)
- Check that Raycast has Accessibility permissions
- Your previous clipboard content is automatically restored

**"No Notion page link detected"**
- An unexpected error occurred during the process
- Try again after ensuring the Notion page is fully loaded
- Verify that Cmd + L works manually in Notion (it should copy the page URL)
- Check Accessibility permissions for Raycast

## License

MIT

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.
