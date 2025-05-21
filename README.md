# MCP Weather Server

A ready-to-use implementation of the Model Context Protocol (MCP) that extends Claude with real-time weather data capabilities.

<iframe width="560" height="315" src="https://youtu.be/Y4bpWRLdRoA?si=TVuUyR79K_N-Zxoo" frameborder="0" allowfullscreen></iframe>

## What is MCP?

Model Context Protocol (MCP) is an open communication framework that allows AI models like Claude to interact with external tools. This enables Claude to access real-time data, process files, and interact with external services - capabilities not available to most LLMs out of the box.

Learn more about MCP:
- [MCP Official Documentation](https://modelcontextprotocol.io) <!-- Replace with actual link to Claude MCP docs -->
- [Getting Started with MCP](https://modelcontextprotocol.io/quickstart/server) <!-- Replace with actual link to MCP getting started guide -->
- [Postmans MCP Developer Community](https://discord.gg/kTnA7cpn) <!-- Replace with actual link to MCP community -->

## What This Repository Contains

This repository provides:

1. **Complete MCP Weather Server**: A fully functional implementation that gives Claude access to real-time weather data
3. **Template Code**: Use as a starting point for your own MCP projects
4. **Configuration Examples**: Sample configuration files for connecting to Claude Desktop

## Features

The MCP Weather Server implements two primary tools:

- **get-forecast**: Retrieve current weather conditions and forecasts for any location by latitude/longitude
- **get-alerts**: Check for active weather alerts in any US state

Once connected, Claude can:
- Answer questions about current weather conditions
- Provide detailed weather forecasts
- Alert users to severe weather warnings
- Make recommendations based on weather data

## Quick Start

### Prerequisites

- Node.js 16+ and npm
- [Claude Desktop](#) <!-- Replace with actual link to Claude Desktop download page -->
- Basic knowledge of TypeScript/JavaScript

### Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/SterlingChin/mcp-weather-server.git
   cd mcp-weather-server
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Build the project:
   ```bash
   npm run build
   ```

### Connecting to Claude Desktop

1. Open your Claude Desktop configuration file:
   - Mac: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Windows: `%AppData%\Claude\claude_desktop_config.json`

2. Add the following configuration (update the path to point to your repository):
   ```json
   {
     "mcpServers": {
       "weather": {
         "command": "node",
         "args": [
           "/absolute/path/to/your/mcp-weather-server/build/index.js"
         ]
       }
     }
   }
   ```

3. Restart Claude Desktop

4. Look for the hammer icon in Claude Desktop, indicating that MCP tools are available

### Testing Your Implementation

Try asking Claude these questions:
- "What's the weather like in San Francisco right now?"
- "Are there any weather alerts in Texas today?"
- "What's the forecast for Chicago this weekend?"

## Project Structure

```
├── src/
│   ├── index.ts           # Main server entry point
│   ├── tools/             # Tool implementations
│   │   ├── get-forecast.ts
│   │   └── get-alerts.ts
│   └── utils/             # Helper functions and API client
│       └── nws-api.ts
├── build/                 # Compiled JavaScript files
├── examples/              # Example code and usage patterns
├── docs/                  # Additional documentation
├── package.json
└── tsconfig.json
```

## Building Your Own MCP Server

This repository can serve as a template for building your own MCP servers. Follow these steps:

1. Fork this repository or create a new one based on its structure
2. Replace the weather API implementation with your own service
3. Define your tools by adding new files in the `src/tools` directory
4. Register your tools in `src/index.ts`
5. Build and test your implementation

For detailed guidance, check out our [step-by-step tutorial](docs/TUTORIAL.md).

## API Information

This server uses the [National Weather Service API](https://www.weather.gov/documentation/services-web-api), which is free to use and doesn't require authentication. Other APIs you might consider integrating include:

- Dictionary/Language APIs
- News and Information APIs
- Public Data APIs
- Financial APIs

When selecting APIs for your MCP server, consider:
- Authentication requirements
- Rate limits
- Data format and parsing complexity
- Update frequency

## Troubleshooting

### Common Issues

- **Claude can't find your server**: Verify your configuration path and restart Claude Desktop
- **API requests failing**: Check your internet connection and API endpoint status
- **Unexpected responses**: Look at Claude Desktop logs at `~/Library/Logs/Claude/mcp*.log`

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Built with ❤️ using the [Model Context Protocol](https://modelcontextprotocol.io) <!-- Replace with actual link -->