# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para nova guia, configuração por setor e bloqueio de sites via políticas gerenciadas.

**Versão:** `1.3.8`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa com pesquisa, Gemini e atalhos;
- configuração por `chrome.storage.managed`;
- wallpaper 16:9 responsivo;
- bloqueio de sites com exceções;
- tela personalizada **Oops!**;
- atualização automática por CRX/XML.

## JSON no Google Admin

No campo **Política para extensões**, use `Value`:

```json
{
  "setor": { "Value": "Fiscal" },
  "sitesBloqueados": {
    "Value": ["web.whatsapp.com", "discord.com"]
  },
  "sitesLiberados": { "Value": [] }
}
```

Dentro da extensão e no `schema.json`, os valores continuam sem `Value`.

## Validar

Após salvar a política:

1. abra `chrome://policy` e recarregue as políticas;
2. abra uma nova guia;
3. no console da extensão, execute:

```javascript
chrome.storage.managed.get(null, console.log)
```

Versão instalada:

```javascript
chrome.runtime.getManifest().version
```

## Publicar atualização

1. aumente a versão no `manifest.json`;
2. gere o CRX com a **mesma chave privada**;
3. atualize `deployment/updates.xml`;
4. publique CRX e XML.

Nunca publique a chave `.pem`.

## v1.3.8

- remove renderizações e timers desnecessários na nova guia;
- relógio atualiza por minuto e pausa quando a guia não está visível;
- elimina carregamento duplicado do wallpaper e mantém fallback local;
- reduz operações DOM ao montar atalhos e menu;
- evita ressincronizar regras de bloqueio quando outras políticas mudam;
- não regrava regras DNR quando elas já estão corretas;
- reduz exceções redundantes nas regras de bloqueio;
- evita sincronizações concorrentes do service worker;
- recomprime o wallpaper local sem perda de qualidade;
- preserva o visual e o comportamento da v1.3.7.
