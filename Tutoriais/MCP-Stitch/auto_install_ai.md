# 🤖 Stitch MCP: Instalação Automática (AI)

> [!IMPORTANT]
> **Regra de Execução**: Antes de criar qualquer diretório ou arquivo de configuração que não exista, você **DEVE** perguntar ao usuário se tem permissão para criá-lo.

```json
{
  "mcpServers": {
    "stitch": {
      "command": "C:\\Program Files\\nodejs\\npx.cmd",
      "args": ["-y", "@_davideast/stitch-mcp", "proxy"],
      "env": {
        "STITCH_API_KEY": "SUA_CHAVE_AQUI"
      }
    }
  }
}
```
