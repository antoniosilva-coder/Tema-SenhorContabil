# Tema Senhor Contábil — v1.7.6.2 (arquitetura robusta)

Esta versão preserva a nova guia original. A alteração principal é a arquitetura de políticas e o mecanismo de bloqueio.

## O que mudou

- Precedência determinística: obrigatório > bloqueio específico > liberação do perfil > bloqueio geral.
- A lista empacotada passa a ser tratada como bloqueio obrigatório.
- Allowlists em arquivos gerais/remotos são ignoradas por segurança.
- Grupos do Google Admin são usados para exceções por perfil de acesso.
- Tentativas de grupos comuns desligarem a proteção ou trocarem URLs de infraestrutura são ignoradas por padrão.
- Cache fail-closed: falha remota preserva última configuração válida.
- Até 4.500 bloqueios exibem a página corporativa; excedentes continuam bloqueados diretamente.
- Página local de diagnóstico e teste de domínio.
- Cache da configuração geral compartilhado por 30 s, reduzindo requisições desnecessárias ao abrir novas guias.

## Arquivos importantes

- `ARQUITETURA-GRUPOS-E-POLITICAS.md` — desenho recomendado de grupos.
- `CONFIGURAR-POR-SETOR.md` — exemplos rápidos.
- `DIAGNOSTICO-E-PROBLEMAS.md` — sintomas e correções.
- `deployment/configs-grupos/` — JSONs prontos para os perfis.
- `config-geral.json` — configuração geral publicada no GitHub Pages.
- `extension/config-geral-default.json` — cópia empacotada para primeira execução/falha remota.

## ID da extensão

A chave do manifesto foi preservada, portanto o ID continua sendo:

`blebikojnakioblpeacdnnphclgeeaha`

Ao publicar uma atualização CRX, use a mesma chave privada PEM da versão atual.
