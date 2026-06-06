# Trading Analysis Agent

AI-powered market analysis tool for BTC price action, derivatives data, and Polymarket probability evaluation.

## Features

- **Real-time Market Analysis** - Analyze BTC price, volatility, and funding rates
- **Polymarket Evaluation** - Assess market probabilities and expected value
- **PhD-Level Expertise** - Powered by Claude API with advanced financial analysis
- **Mobile Responsive** - Works seamlessly on desktop, tablet, and mobile
- **No Backend Required** - Client-side only, runs entirely in your browser
- **Secure** - API keys stored locally, never sent to third parties

## Quick Start

### Prerequisites

- Claude API key from [console.anthropic.com](https://console.anthropic.com)

### Local Development

```bash
cd trading-agent
python -m http.server 3000
```

Then open `http://localhost:3000` in your browser.

### Deploy to Netlify

#### Option 1: Connect GitHub (Recommended)

1. Push this repository to GitHub
2. Go to [netlify.com](https://netlify.com) and click "New site from Git"
3. Select your GitHub repository
4. Leave build settings as default (static site)
5. Click "Deploy"

#### Option 2: Drag & Drop

1. Go to [netlify.com/drop](https://netlify.com/drop)
2. Drag the `trading-agent` folder onto the page
3. Done!

## How to Use

1. Get your Claude API key at [console.anthropic.com](https://console.anthropic.com)
2. Paste your API key into the Configuration section
3. Enter current market data (BTC price, volatility, funding rate)
4. (Optional) Add Polymarket market details
5. (Optional) Add custom context or questions
6. Click "Analyze Markets"
7. Review the analysis and raw response

## API Keys & Security

- API keys are **stored locally in your browser** using `localStorage`
- Keys are **never sent to any server** except the official Anthropic API
- Each request goes directly from your browser to Claude's API
- No data is logged or stored on any external service

To clear your saved key, use your browser's DevTools:

```javascript
localStorage.removeItem('anthropic_api_key');
```

## Customization

### Modify the Analysis Prompt

Edit the `buildPrompt()` function in `index.html` to customize the system prompt and analysis framework.

### Change Model

Select a different Claude model in the Configuration section:
- **Claude 3.5 Sonnet** - Best for complex analysis (recommended)
- **Claude 3 Opus** - More powerful, slower
- **Claude 3 Haiku** - Faster, lower cost

### Styling

Update the `<style>` section in `index.html` to customize colors, fonts, and layout.

## Example Workflow

1. **Market Setup**
   - BTC Price: 45,000
   - Volatility: 2.5%
   - Funding Rate: 0.05%

2. **Polymarket Question**
   - "Will BTC reach $50k by end of Q2?"
   - Current Odds: 65%

3. **Custom Context**
   - Add recent news, on-chain metrics, or specific concerns

4. **Get Analysis**
   - Market Assessment
   - BTC Technical & Macro Analysis
   - Polymarket Opportunity Evaluation
   - Trade Recommendations
   - Risk Assessment

## Requirements

- Modern web browser (Chrome, Firefox, Safari, Edge)
- Claude API key with sufficient quota
- Internet connection

## Cost Estimation

Using Claude 3.5 Sonnet:
- ~2,000 input tokens per analysis
- ~1,000 output tokens per analysis
- ~$0.03 per analysis

See [Anthropic pricing](https://www.anthropic.com/pricing) for current rates.

## Environment Variables (Optional)

For production deployments, you can set environment variables in Netlify:

```
ANTHROPIC_API_KEY=sk-...
```

Then modify `index.html` to read from `window.ENV`:

```javascript
const apiKey = window.ENV?.ANTHROPIC_API_KEY || document.getElementById('apiKey').value;
```

## Troubleshooting

### "API request failed"
- Check your API key is correct
- Verify your API key has available quota
- Check your internet connection

### "Slow responses"
- Switch to Claude 3 Haiku for faster (but less detailed) analysis
- Wait for lower API traffic times

### "CORS errors"
- Ensure you're using a valid Anthropic API key
- Check that your API key isn't expired

## License

MIT

## Disclaimer

This tool is for educational and analysis purposes. It is not financial advice. Always conduct your own research and consult professional advisors before making trading decisions. Crypto trading carries significant risk.

## Support

For issues with Claude API, see [Anthropic docs](https://docs.anthropic.com).
For Netlify deployment issues, see [Netlify docs](https://docs.netlify.com).