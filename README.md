# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para personalização da nova guia por política gerenciada do Chrome.

**Versão:** `1.5.1`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa com pesquisa, Gemini e atalhos;
- configuração por `chrome.storage.managed`;
- wallpaper responsivo;
- atualização automática via CRX/XML.

> A extensão não realiza bloqueio personalizado de sites.

## Desempenho

A v1.5.1 reduz trabalho e rede na abertura da nova guia:

- wallpaper padrão local em WebP;
- wallpaper remoto carregado em baixa prioridade;
- evita renderização duplicada quando a política é igual ao padrão;
- ícones externos usam prioridade baixa;
- remove blur contínuo dos elementos sempre visíveis.

Para o melhor desempenho, quando usar o wallpaper padrão no Google Admin, use:

```json
{
  "wallpaperUrl": { "Value": "assets/wallpaper-senhor-contabil.webp" }
}
```

Use URL HTTPS apenas quando um setor realmente precisar de wallpaper remoto.

## Publicar

1. mantenha a mesma chave privada `.pem`;
2. gere o CRX da pasta `extension`;
3. publique o CRX e `deployment/updates.xml`;
4. nunca publique a chave `.pem`.
