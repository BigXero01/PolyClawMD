# Privacy Policy

## Data Collection

This application collects **no data**. Here's what happens:

### What We Store

- **Your API Key**: Stored in your browser's `localStorage` only. Never sent anywhere except to Anthropic.
- **Your Market Data**: Temporary, only in memory while you use the app. Lost on refresh.

### What We Don't Do

- ❌ No tracking
- ❌ No analytics
- ❌ No logs
- ❌ No cookies for tracking
- ❌ No third-party services (except Anthropic's API)
- ❌ No data persistence

### API Requests

Each analysis request goes directly from your browser to Anthropic's API at `api.anthropic.com`. Your market data is included in the request payload. See [Anthropic's Privacy Policy](https://www.anthropic.com/privacy) for their practices.

### Clearing Your Data

To remove your stored API key:

1. Open browser DevTools (F12)
2. Go to Console
3. Run: `localStorage.removeItem('anthropic_api_key')`
4. Refresh the page

Or use browser settings to clear site storage.

## Contact

Questions about privacy? Open an issue on GitHub.