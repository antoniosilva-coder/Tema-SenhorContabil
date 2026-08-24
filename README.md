# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para nova guia e políticas internas do Chrome.

**Versão:** `1.6.0`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa com pesquisa, Gemini e atalhos;
- configuração por `chrome.storage.managed`;
- wallpaper responsivo;
- bloqueio de sites por domínio com página **Oops!** personalizada;
- exceções de liberação por domínio/subdomínio;
- suporte ao bloqueio no Incógnito quando a extensão está autorizada nele;
- atualização automática via CRX/XML.

## Bloqueio de sites

O bloqueio usa `declarativeNetRequest`: as regras ficam no próprio Chrome e não existe JavaScript interceptando cada clique.

No Google Admin, em **Política para extensões**:

```json
{
  "sitesBloqueados": {
    "Value": [
      "discord.com",
      "web.whatsapp.com"
    ]
  },
  "sitesLiberados": {
    "Value": []
  },
  "mensagemBloqueio": {
    "Value": "Se você precisa deste acesso para o trabalho, entre em contato com o setor de TI."
  }
}
```

Aceita também entradas como `https://discord.com/`, `*.discord.com` e `*://discord.com/*`.

Uma entrada em `sitesLiberados` tem prioridade. Exemplo: bloquear `google.com` e liberar `drive.google.com`.

## Incógnito

O manifesto usa `"incognito": "split"` para que a página **Oops!** possa abrir dentro de uma janela anônima. A extensão ainda precisa estar autorizada a funcionar no Incógnito pela política/gerenciamento do Chrome.

## Publicar

1. mantenha a mesma chave privada `.pem`;
2. gere o CRX da pasta `extension`;
3. publique o CRX e `deployment/updates.xml`;
4. nunca publique a chave `.pem`.
