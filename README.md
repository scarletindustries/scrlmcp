<img width="128" src="https://github.com/scarletindustries.png" />

### scrlmcp

An MCP server framework for Scarlet, extracted from heddle.

[Documentation](https://scarlet.industries) • [MCP spec](https://modelcontextprotocol.io)

---

A server is a value you build up: hand it tools (closures over whatever they need), a bearer token, optionally a status route, then serve it or mount `server.handle` inside your own http handler. Transport is Streamable HTTP with the streaming left out: one POST, one JSON-RPC message, one JSON reply.

```scarlet
import ./vendor/scrlmcp/src/server
import ./vendor/scrlmcp/src/schema

s = server.authenticate(server.tools(server.new('myapp', '0.1.0'), my_tools()), token)
server.serve(s, '0.0.0.0', 7823)
```

Ships its own json module (`src/json.scrl`): parse-to-values with `text_at`/`int_at` accessors. Vendored via git submodule for now.
