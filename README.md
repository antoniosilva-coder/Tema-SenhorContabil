# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para personalizar a nova guia do Chrome e aplicar configurações por política gerenciada.

**Versão:** `1.3.0`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa;
- botão principal do Gemini ao lado da pesquisa;
- wallpaper, cores, atalhos e menu Google configuráveis;
- configuração por setor/grupo usando `chrome.storage.managed`;
- bloqueio de sites por política;
- exceções de liberação;
- página personalizada **“Oops!”** para sites bloqueados.

## JSON no Google Admin

No campo **Política para extensões**, use o formato com `Value`:

```json
{
  "setor": {
    "Value": "Fiscal"
  },
  "sitesBloqueados": {
    "Value": [
      "web.whatsapp.com",
      "discord.com"
    ]
  },
  "sitesLiberados": {
    "Value": []
  },
  "mensagemBloqueio": {
    "Value": "Este site foi bloqueado pela Senhor Contábil devido às políticas internas."
  }
}
```

No `schema.json` e dentro da extensão, os valores continuam **sem `Value`**.

O botão do Gemini vem ativo por padrão. Para ocultar ou trocar o endereço:

```json
{
  "mostrarGemini": { "Value": true },
  "geminiUrl": { "Value": "https://gemini.google.com/" }
}
```

## Bloqueio de sites

Use somente domínios, por exemplo:

```text
web.whatsapp.com
discord.com
instagram.com
```

`sitesLiberados` tem prioridade sobre `sitesBloqueados`.

Exemplo:

```json
{
  "sitesBloqueados": {
    "Value": ["discord.com", "web.whatsapp.com"]
  },
  "sitesLiberados": {
    "Value": ["web.whatsapp.com"]
  }
}
```

Resultado: Discord é bloqueado e WhatsApp é liberado.

> Para exibir a página personalizada da extensão, não bloqueie o mesmo endereço também pelo `URLBlocklist` do Chrome.

## Aplicar e validar

Após salvar a política:

1. abra `chrome://policy`;
2. clique em **Recarregar políticas**;
3. reinicie o Chrome se necessário;
4. na nova guia, confira:

```javascript
chrome.storage.managed.get(null, console.log)
```

Para confirmar a versão:

```javascript
chrome.runtime.getManifest().version
```

Deve retornar:

```text
1.3.0
```

## Atualização do CRX

Ao publicar uma nova versão:

1. aumente `version` no `manifest.json`;
2. gere o CRX usando a **mesma chave privada** das versões anteriores;
3. atualize a versão em `deployment/updates.xml`;
4. publique o CRX e o XML no endereço configurado.

Nunca publique ou compartilhe a chave `.pem`.

## Estrutura principal

```text
extension/
├── manifest.json
├── schema.json
├── service-worker.js
├── blocked.html
├── blocked.css
├── blocked.js
├── newtab.html
├── newtab.js
└── config-default.js
```

Configurações de exemplo ficam em `deployment/configs-setores/`.
