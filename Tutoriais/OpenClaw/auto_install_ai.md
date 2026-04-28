# 🤖 OpenClaw: Instalação Automática (AI)

> [!IMPORTANT]
> **Regra de Execução**: Antes de criar qualquer diretório que não exista, você **DEVE** perguntar ao usuário se tem permissão para criá-lo.

```powershell
# 1. Preparar pasta
$clawBase = "C:\.DADOS\.OPENCLOW"
if (-not (Test-Path $clawBase)) {
    $response = Read-Host "O diretório $clawBase não existe. Deseja criá-lo? (S/N)"
    if ($response -eq 'S') { New-Item -ItemType Directory -Force -Path $clawBase } else { throw "Instalação cancelada pelo usuário." }
}
cd $clawBase

# 2. Configuração via openclaw.json
$clawConfig = @"
{
  "models": [
    {
      "name": "gemma4:26b",
      "provider": "ollama",
      "baseUrl": "http://127.0.0.1:11434"
    }
  ]
}
"@
$clawConfig | Set-Content "$env:USERPROFILE\.openclaw\openclaw.json"

# 3. Iniciar gateway
node openclaw.mjs gateway
```
