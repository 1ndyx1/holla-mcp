# Installing the Holla MCP server

Holla is a hosted remote MCP server. There is nothing to download, build or run, and no API key.

1. Add this server to the MCP settings file (for Cline, `cline_mcp_settings.json`):

   ```json
   {
     "mcpServers": {
       "holla": {
         "type": "streamableHttp",
         "url": "https://useholla.com/mcp"
       }
     }
   }
   ```

2. Leave authentication empty. Every tool is read-only and public.

3. Check the connection by calling `get_checkpoint_traffic` with no arguments. It returns the current
   driving times across the Woodlands and Tuas checkpoints between Singapore and Johor Bahru.

The other tools are `search_vouchers`, `find_esim_plans`, `find_parking` and `find_ev_chargers`.
Parking and EV charging cover Singapore only. See README.md for details.
