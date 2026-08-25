# Tema Senhor Contábil — Chrome

**Versão:** `1.7.5`  

## Correção v1.7.5

- Corrigido o redirecionamento das regras DNR da blocklist padrão para `blocked.html`.
- O parâmetro do site bloqueado agora usa uma URL interna completa, sem query dentro de `extensionPath`.
- Adicionado modo de segurança *fail-closed*: se um redirecionamento for rejeitado pelo Chrome, as regras são reaplicadas como bloqueio direto.
- Cache de sincronização elevado para V5 para forçar uma reconciliação limpa após a atualização.
- A blocklist local é aplicada antes da consulta remota; a lista remota possui timeout e não pode mais atrasar o bloqueio padrão.

**ID:** `blebikojnakioblpeacdnnphclgeeaha`

Extensão corporativa Manifest V3 para nova guia, configuração por setor e bloqueio de sites.

## Bloqueio

O bloqueio final é formado por:

1. `extension/blocklist-default.txt` — fallback local do CRX;
2. `blocklist.txt` remoto — atualizado sem republicar o CRX;
3. `sitesBloqueados` — regras adicionais do setor;
4. `sitesLiberados` — exceções, com prioridade sobre bloqueios.

URL remota padrão:

`https://antoniosilva-coder.github.io/Tema-SenhorContabil/blocklist.txt`

O Chrome aplica as regras pelo `declarativeNetRequest`; não há JavaScript verificando cada clique.

## TXT

Uma entrada por linha:

```text
discord.com
*.facebook.com
203.0.113.10
https://exemplo.com/caminho
0.0.0.0 ads.exemplo.com
||tracker.exemplo.com^
```

Também aceita liberações opcionais:

```text
[ALLOW]
drive.google.com

[BLOCK]
google.com
```

ou:

```text
@@||drive.google.com^
```

Comentários iniciados por `#`, `;`, `!` ou `//` são ignorados. CIDR (`10.0.0.0/24`) não é suportado; use IPs individuais.

## Sincronização

- alteração do JSON gerenciado: imediata;
- reconciliação de segurança: a cada 30 s;
- TXT remoto: verificado a cada 30 s por padrão;
- falha de rede: mantém a última lista remota válida;
- regras antigas de versões anteriores são limpas automaticamente.

## Exemplo Google Admin

```json
{
  "setor": { "Value": "Fiscal" },
  "bloqueioAtivo": { "Value": true },
  "usarListaBloqueioPadrao": { "Value": true },
  "intervaloAtualizacaoListaSegundos": { "Value": 30 },
  "sitesBloqueados": {
    "Value": ["discord.com"]
  },
  "sitesLiberados": {
    "Value": []
  }
}
```

## Diagnóstico

No console da extensão:

```javascript
chrome.runtime.sendMessage({type: "senhor-contabil:get-blocking-status"}).then(console.log)
```

Para ver as regras carregadas:

```javascript
chrome.declarativeNetRequest.getDynamicRules().then(r => console.log(r.length, r.slice(0, 5)))
```

## Wallpaper

É carregado do GitHub Pages, não do CRX:

`https://antoniosilva-coder.github.io/Tema-SenhorContabil/wallpaper-senhor-contabil.png`

## Publicar

1. gere o CRX da pasta `extension` usando a mesma `.pem`;
2. publique `tema-senhor-contabil.crx` e `deployment/updates.xml`;
3. nunca publique a chave `.pem`.
