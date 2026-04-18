# Arquitetura

## Fluxo principal
Evolution API (WhatsApp)
↓  MESSAGES_UPSERT
[Nó 1] Webhook
↓
[Nó 2] Code JS — EXTRAIR NÚMERO
↓
[Nó 3] Filter (valido = true)
↓ TRUE              ↓ FALSE
[Nó 4] Claude     [Nó ERR] Code JS: preparar log
↓                  ↓
[Nó 5] Code JS    [Nó ERR-2] Notion: Log de Erros
(parser Claude)
↓
[Nó 6] Notion: Tokyo Monitor

## Componentes

- **Evolution API** — recebe e envia mensagens WhatsApp
- **n8n** — orquestra o fluxo entre os serviços
- **Claude API** — processa e responde as mensagens
- **Notion** — registra logs no Tokyo Monitor
