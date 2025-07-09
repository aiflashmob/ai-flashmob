# 🤖 AI Flashmob MCP Server

A Model Context Protocol (MCP) server that enables AI assistants like Claude to generate educational flashcards from text and images using the AI Flashmob platform.

## 🚀 Features

- **Text-to-Flashcards**: Generate AI flashcards from any text content
- **Image-to-Flashcards**: Analyze images and create educational flashcards
- **Category Management**: Browse and organize your flashcard categories
- **Flashcard Browsing**: View all flashcards from specific categories
- **Secure Authentication**: HMAC-SHA256 request signing for secure API access
- **Credit Management**: Automatic AI credit consumption and tracking

## 📋 Prerequisites

- Node.js 18.0.0 or higher
- An AI Flashmob account with API credentials
- Claude Desktop or another MCP-compatible client

## 🔧 Installation

### Method 1: Global Installation (Recommended for Regular Use)

```bash
npm install -g ai-flashmob-mcp
```

**Benefits:**

- ✅ Command available everywhere
- ✅ Faster startup (already installed)
- ✅ Works offline once installed

### Method 2: Using npx (No Installation Required)

```bash
npx ai-flashmob-mcp
```

**Benefits:**

- ✅ No installation needed
- ✅ Always uses latest version
- ✅ Perfect for trying it out

### Which Method Should You Choose?


| Feature        | Global Install       | npx                    |
| -------------- | -------------------- | ---------------------- |
| **Setup**      | One-time install     | No setup needed        |
| **Speed**      | Fast startup         | Slower first run       |
| **Updates**    | Manual update needed | Always latest          |
| **Disk Space** | Uses ~40MB           | Downloads each time    |
| **Best For**   | Regular users        | Testing/occasional use |

### Get Your API Credentials

1. Log into your [AI Flashmob account](https://ai-flashmob.com)
2. Go to **Profile → API Credentials** section
3. Copy your **Public User ID** and **API Secret Key**

## ⚙️ Configuration

### Claude Desktop Setup

Add this to your Claude Desktop configuration file:

**Location:** `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS)

#### For Global Installation:

```json
{
  "mcpServers": {
    "ai-flashmob": {
      "command": "ai-flashmob-mcp",
      "env": {
        "PUBLIC_USER_ID": "your-public-user-id",
        "SECRET_KEY": "your-secret-key"
      }
    }
  }
}
```

#### For npx Usage:

```json
{
  "mcpServers": {
    "ai-flashmob": {
      "command": "npx",
      "args": ["ai-flashmob-mcp@latest"],
      "env": {
        "PUBLIC_USER_ID": "your-public-user-id",
        "SECRET_KEY": "your-secret-key"
      }
    }
  }
}
```

### Environment Variables


| Variable         | Required | Description                        |
| ---------------- | -------- | ---------------------------------- |
| `PUBLIC_USER_ID` | ✅       | Your public user identifier (UUID) |
| `SECRET_KEY`     | ✅       | Your 64-character secret key       |

**After setup:**

1. Restart Claude Desktop
2. Test by asking: *"What MCP tools do you have available?"*

## 🛠️ Available Tools

### 1. Generate Flashcards from Text

Create educational flashcards from any text content.

**Usage:**

```
Generate flashcards from this text: "JavaScript is a programming language..."
```

**Parameters:**

- Text content (10-7000 characters)
- Maximum cards (1-10, default: 5, used in prompt, not guaranteed to work)
- Optional category ID for organization

### 2. Generate Flashcards from Image

Analyze images and create educational flashcards from visual content.

**Usage:**

```
Generate flashcards from this image: [upload or paste image]
```

**Parameters:**

- Base64-encoded image or image upload
- Image format (png, jpeg, jpg, webp)
- Maximum cards (1-10, default: 5, used in prompt, not guaranteed to work)
- Optional category ID for organization

### 3. Browse Categories

View all your flashcard categories with details and counts.

**Usage:**

```
Show me all my flashcard categories
```

**Response includes:**

- Category names and ids
- Number of flashcards in each category
- Creation dates

### 4. View Category Flashcards

Browse all flashcards from a specific category.

**Usage:**

```
Show me all flashcards in category 5
```

**Response includes:**

- Complete flashcard content (front/back)
- Study progress status
- Bookmark indicators
- Creation dates

## 🔐 Security

Your API credentials are securely processed using:

- **HMAC-SHA256 request signing** - Your secret key never travels over the network
- **Timestamp validation** - Prevents replay attacks
- **Secure authentication** - Industry-standard security practices

## 🐛 Troubleshooting

### Common Issues

**Authentication Failed**

```
❌ Authentication failed: Invalid credentials
```

**Solution:** Verify your `PUBLIC_USER_ID` and `SECRET_KEY` are correct in the configuration.

**Insufficient Credits**

```
❌ Insufficient credits: You need more AI credits
```

**Solution:** Add AI credits to your account or upgrade your plan.

**Connection Issues**

```
❌ Unable to connect to API
```

**Solution:** Check your internet connection. If the issue persists, verify the AI Flashmob service status.

**Invalid Input**

```
❌ Invalid request: Text must be between 10 and 7000 characters
```

**Solution:** Ensure your input meets the parameter requirements.

### Testing Your Setup

After configuration, test by asking Claude:

```
"Generate a few flashcards from this text: Node.js is a JavaScript runtime environment"
```

## 📊 Usage Limits

- **different number of requests based on user tier**
- **1 AI credit consumed** per flashcard generation, refer to [pricing](https://ai-flashmob.com/) for latest details

## 🆘 Support

For help:

1. Check this README for common solutions
2. Verify your configuration matches the examples above
3. Ensure you have sufficient AI credits in your account
4. Contact [AI Flashmob support](https://ai-flashmob.com/) with your `PUBLIC_USER_ID` (never share your `SECRET_KEY`)

## 📄 License

MIT License - see the full license in the package.

## 🔄 Updates

**For Global Installation:**

```bash
npm update -g ai-flashmob-mcp
```

**For npx Usage:**

```bash
# No action needed - npx always uses the latest version
npx ai-flashmob-mcp  # Automatically gets latest
```

---

**🎓 Happy Learning with AI-Powered Flashcards!**

Ready to supercharge your study sessions? Install the MCP server and start generating intelligent flashcards directly through Claude!
