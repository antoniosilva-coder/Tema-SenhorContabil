# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para nova guia, políticas por setor e bloqueio de sites.

**Versão:** `1.4.0`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa com pesquisa, Gemini e atalhos;
- configuração por `chrome.storage.managed`;
- wallpaper responsivo;
- bloqueio de sites e tela **Oops!**;
- página interna de versão;
- atualização automática por CRX/XML.

## Página de versão

Na pesquisa da própria nova guia, digite:

```text
sr://version
```

Na barra de endereços, o modo nativo da extensão é:

```text
sr + Espaço + version
```

Para aceitar **`sr://version` diretamente na barra de endereços no Windows**, execute:

```text
deployment/Instalar-Protocolo-SR.ps1
```

O script registra o protocolo `sr://` no Windows e abre:

```text
chrome-extension://blebikojnakioblpeacdnnphclgeeaha/version.html
```

A primeira chamada pode exibir uma confirmação de protocolo externo, dependendo das políticas do Chrome.

## JSON no Google Admin

No campo **Política para extensões**, use `Value`:

```json
{
  "setor": { "Value": "Fiscal" },
  "sitesBloqueados": { "Value": ["web.whatsapp.com", "discord.com"] },
  "sitesLiberados": { "Value": [] }
}
```

## Publicar atualização

1. mantenha a mesma chave privada da extensão;
2. gere o CRX da pasta `extension`;
3. publique o CRX e o `deployment/updates.xml`.

Nunca publique a chave `.pem`.

## v1.4.0

- adiciona `version.html` com versão, ID, setor e Manifest;
- adiciona comando `sr://version` na pesquisa da nova guia;
- adiciona atalho de Omnibox `sr` + `version`;
- inclui instalador opcional do protocolo `sr://` para Windows.
