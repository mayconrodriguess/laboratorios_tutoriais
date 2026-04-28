# 🤖 Obsidian MCP: Instalação Automática (AI)

> [!IMPORTANT]
> **Regra de Execução**: Antes de criar qualquer diretório que não exista, você **DEVE** perguntar ao usuário se tem permissão para criá-lo.

```powershell
# 1. Configurar Plugin Local REST API
$vault = "c:\.DADOS\Obsidian\MeuVault"
$pluginDir = "$vault\.obsidian\plugins\obsidian-local-rest-api"

if (-not (Test-Path $pluginDir)) {
    $response = Read-Host "O diretório $pluginDir não existe. Deseja criá-lo? (S/N)"
    if ($response -eq 'S') { New-Item -ItemType Directory -Force -Path $pluginDir } else { throw "Instalação cancelada pelo usuário." }
}
# (Download de manifest.json e main.js via IWR)

# 2. Configurar data.json
$config = @{
    apiKey = $apiKey
    enableInsecureServer = $true
    insecurePort = 27123
    enableSecureServer = $false
} | ConvertTo-Json
$config | Set-Content "$pluginDir\data.json"
```
