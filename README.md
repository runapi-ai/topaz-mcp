# @runapi.ai/topaz-mcp

RunAPI MCP server for the **Topaz** model line. Create tasks,
poll their status, and check pricing through a single RunAPI API key.

## Tools

- `upscale_image` — create a Topaz task (upscale image) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `topaz-upscale-image`, `topaz-upscale-video`.
- `upscale_video` — create a Topaz task (upscale video) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `topaz-upscale-image`, `topaz-upscale-video`.
- `get_task` — fetch the current status and latest payload for a task.
- `check_pricing` — look up pricing for a model in this line.

## Configuration

Set a RunAPI API key via the `RUNAPI_API_KEY` environment variable, or write
it to `~/.config/runapi/config.json`:

```bash
mkdir -p ~/.config/runapi
echo '{"api_key":"YOUR_KEY"}' > ~/.config/runapi/config.json
```

Get an API key at https://runapi.ai. Pricing is listed at
https://runapi.ai/pricing.

## Usage

Run the server over stdio:

```bash
npx -y @runapi.ai/topaz-mcp
```

Add it to an MCP client (see `examples/` for per-client configs):

```json
{
  "mcpServers": {
    "topaz": {
      "command": "npx",
      "args": ["-y", "@runapi.ai/topaz-mcp"],
      "env": { "RUNAPI_API_KEY": "${RUNAPI_API_KEY}" }
    }
  }
}
```

## License

Apache-2.0
