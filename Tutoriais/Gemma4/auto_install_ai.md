# 🤖 Gemma 4: Instalação Automática (AI)

> [!IMPORTANT]
> **Regra de Execução**: Antes de criar qualquer diretório que não exista, você **DEVE** perguntar ao usuário se tem permissão para criá-lo.

```powershell
# 1. Instalar Ollama
$toolsDir = "c:\.DADOS\tools"
if (-not (Test-Path $toolsDir)) {
    $response = Read-Host "O diretório $toolsDir não existe. Deseja criá-lo? (S/N)"
    if ($response -eq 'S') { New-Item -ItemType Directory -Force -Path $toolsDir } else { throw "Instalação cancelada pelo usuário." }
}

Invoke-WebRequest "https://ollama.com/download/OllamaSetup.exe" -OutFile "$toolsDir\OllamaSetup.exe"
Start-Process -Wait "$toolsDir\OllamaSetup.exe" -ArgumentList "/silent"

# 2. Configurar Variáveis de Ambiente
[System.Environment]::SetEnvironmentVariable("OLLAMA_ORIGINS", "*", "User")
[System.Environment]::SetEnvironmentVariable("OLLAMA_HOST", "0.0.0.0", "User")

# 3. Pull de Modelos
ollama pull gemma4:31b
ollama pull gemma2:latest

# 4. Configurar Cursor (Continue)
cursor --install-extension continue.continue
# Nota: Injetar config no %USERPROFILE%\.continue\config.json
```
