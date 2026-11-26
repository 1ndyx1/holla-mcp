# Holla MCP server

<img src="logo.png" alt="Holla" width="120" align="right">

Holla's remote MCP server lets AI assistants look up Singapore vouchers, travel eSIM plans, parking
rates, EV chargers and Singapore–Johor checkpoint traffic from [Holla](https://useholla.com)'s live
listings and data.

- **URL:** `https://useholla.com/mcp` (Streamable HTTP)
- **Authentication:** none. Every tool is read-only and returns public information.
- **Documentation:** <https://useholla.com/ai-connector>

This repository holds only the connection details and manifests. The server itself is hosted by
Holla; there is nothing to install or run.

## Tools

| Tool | What it does |
|---|---|
| `search_vouchers` | Searches Singapore gift cards and vouchers by brand, service or item, with face value, price in SGD and a link to the Holla page |
| `find_esim_plans` | Lists travel eSIM plans for a country or region, with data, validity, activation rules and price |
| `find_parking` | Lists up to 20 car parks near a Singapore destination, nearest or cheapest within a walk, with the estimated charge for a stay and available lots |
| `find_ev_chargers` | Lists EV charging sites with plugs, power, price per kWh and live status; with car details, the cost of a 20% to 80% charge plus parking |
| `get_checkpoint_traffic` | Current and usual driving times across the Woodlands and Tuas checkpoints |

## Connect

**Claude:** Settings → Connectors → Add custom connector, with the URL above.

**Claude Code**

```bash
claude mcp add --transport http holla https://useholla.com/mcp
```

**Gemini CLI**

```bash
gemini extensions install https://github.com/1ndyx1/holla-mcp
```

or, without the extension:

```bash
gemini mcp add --transport http holla https://useholla.com/mcp
```

**Cursor** (`~/.cursor/mcp.json`)

```json
{ "mcpServers": { "holla": { "url": "https://useholla.com/mcp" } } }
```

**Cline** (`cline_mcp_settings.json`)

```json
{ "mcpServers": { "holla": { "type": "streamableHttp", "url": "https://useholla.com/mcp" } } }
```

**Other MCP clients:** add a remote server with the URL above, Streamable HTTP and no authentication.

## Example questions

- "Cheapest parking near ION Orchard for 3 hours on Saturday?"
- "Cheapest place near Suntec to charge my BYD Atto 3 from 20% to 80%, parking included?"
- "Which Japan eSIM gives me 10 GB for a week?"
- "How long is the drive to JB through Woodlands now?"

## Privacy and support

The server receives only each lookup the assistant makes, never the conversation. See the
[privacy policy](https://useholla.com/privacy-policy) and [customer terms](https://useholla.com/customer-terms).
Support: <https://useholla.com/contact>.

Registry name: `com.useholla/holla` on the [official MCP Registry](https://registry.modelcontextprotocol.io).
