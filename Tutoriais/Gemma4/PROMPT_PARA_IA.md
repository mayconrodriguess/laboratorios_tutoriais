
# 🧠 Prompt de Execução para Agente de IA

**Objetivo**: Instalar e configurar o Ollama com modelos Gemma 4 e integrar ao Cursor via extensão Continue.

**Instruções para o Agente:**

1.  **Preparar Ambiente**: 
    *   Criar diretório `c:\.DADOS\tools` se não existir.
    *   Baixar `OllamaSetup.exe` e instalar via `Start-Process -Wait /silent`.
    *   Configurar variáveis de ambiente do usuário: `OLLAMA_ORIGINS="*"` e `OLLAMA_HOST="0.0.0.0"`.

2.  **Gerenciar Modelos**:
    *   Executar `ollama pull gemma4:31b` (Atenção: 19GB).
    *   Executar `ollama pull gemma2:latest` para autocomplete leve.

3.  **Configurar Cursor/Continue**:
    *   Instalar extensão via CLI: `cursor --install-extension continue.continue`.
    *   Localizar o arquivo de configuração YAML em `%USERPROFILE%\.continue\config.yaml`.
    *   Injetar a seguinte estrutura na lista de `models`:
    ```yaml
    - name: Gemma 4 31B
      provider: ollama
      model: gemma4:31b
      apiBase: http://localhost:11434
      roles: [chat, edit, apply]
    ```

4.  **Verificação**:
    *   Confirmar se `http://localhost:11434/api/tags` retorna os modelos.
    *   Abrir o arquivo de configuração no editor do usuário para confirmação visual.

**Finalização**: Informar ao usuário que o modelo de 31B requer tempo de carregamento inicial (cold start) de ~20s.
