# Twitter/X Position Saver

A Tampermonkey userscript that saves your timeline position and returns to it on demand. Never lose your place in the Twitter/X timeline again!

## Features

- **Automatic position saving** – Continuously saves your current scroll position
- **Manual bookmarks** – Set a bookmark at any position and return to it later
- **Cross-page navigation** – Bookmarks work across different pages (home, profiles, replies, etc.)
- **Tab awareness** – Remembers which tab you were on (For You, Following, Replies, etc.)
- **Fast scrolling** – Quickly scrolls through the timeline to find your saved position
- **Abort support** – Press `Escape` to stop scrolling at any time

## Installation

1. Install [Tampermonkey](https://www.tampermonkey.net/) for your browser
2. Click on the script file [`twitter-position-saver.user.js`](twitter-position-saver.user.js)
3. Click "Raw" to open the script
4. Tampermonkey will prompt you to install – click "Install"

Or manually:
1. Open Tampermonkey dashboard
2. Create a new script
3. Copy and paste the contents of `twitter-position-saver.user.js`
4. Save

## Usage

After installation, you'll see two buttons in the bottom-right corner of Twitter/X:

| Button | Function |
|--------|----------|
| 💾 | Save a manual bookmark at your current position |
| 🔖 | Jump to your saved bookmark |
| 📍 | Jump to the automatically saved position |

### Keyboard Shortcut

- **Escape** – Abort the current scroll operation

## Configuration

You can adjust settings at the top of the script:

```javascript
const CONFIG = {
    maxAgeMinutes: 60,        // Auto-position expires after this time
    saveIntervalMs: 2000,     // How often to save position (ms)
    scrollStepDelayMs: 300,   // Delay between scroll steps (ms)
    maxScrollAttempts: 150,   // Max attempts before giving up
    showNotifications: true,  // Show status notifications
    debug: false              // Enable console logging
};
```

## How It Works

Twitter/X uses virtualized scrolling, which means tweets are dynamically loaded and unloaded as you scroll. This script:

1. Saves the Tweet ID of the topmost visible tweet
2. When restoring, scrolls to the top of the page
3. Repeatedly scrolls down until it finds the saved tweet
4. Highlights the tweet and centers it on screen

## Compatibility

- Works on both `twitter.com` and `x.com`
- Tested with Tampermonkey on Firefox and Chrome
- Should work with other userscript managers (Greasemonkey, Violentmonkey)

## License

MIT License – see [LICENSE](LICENSE) for details.

## Contributing

Contributions are welcome! Feel free to open issues or submit pull requests.
