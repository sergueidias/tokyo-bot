# Tokyo Bot

Sistema de atendimento automático via WhatsApp.

## Stack

- Evolution API v2.3.7 (WhatsApp)
- n8n self-hosted (orquestração)
- Claude API (IA)
- Notion (log e memória)

## Infraestrutura

- VPS Hostinger KVM 1 — Ubuntu 24.04 LTS
- Nginx + SSL Let's Encrypt
- Docker (Evolution API, PostgreSQL, Redis, n8n)

## Arquitetura
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

## Documentação

Documentação técnica completa no Notion (repositório privado).

## Status

✅ Operacional — 17/04/2026
