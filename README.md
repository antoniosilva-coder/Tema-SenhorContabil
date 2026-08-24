# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para personalização da nova guia por política gerenciada do Chrome.

**Versão:** `1.5.0`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa com pesquisa, Gemini e atalhos;
- configuração por `chrome.storage.managed`;
- wallpaper responsivo;
- página de versão;
- atualização automática via CRX/XML.

> A partir da v1.5.0, a extensão não realiza bloqueio personalizado de sites.

## Página de versão

Na pesquisa da nova guia:

```text
sr://version
```

Na barra do Chrome:

```text
sr + Espaço + version
```

Para habilitar `sr://version` diretamente no Windows:

```powershell
.\deployment\Instalar-Protocolo-SR.ps1 -Test
```

## Google Admin

Exemplo de política:

```json
{
  "setor": { "Value": "Fiscal" },
  "tituloPagina": { "Value": "Senhor Contábil - Fiscal" },
  "mostrarRelogio": { "Value": true }
}
```

## Publicar

1. mantenha a mesma chave privada `.pem`;
2. gere o CRX da pasta `extension`;
3. publique o CRX e `deployment/updates.xml`;
4. nunca publique a chave `.pem`.

## v1.5.0

- remove o bloqueio personalizado de sites;
- remove a página `Oops!` e regras dinâmicas de bloqueio;
- remove `sitesBloqueados`, `sitesLiberados` e `mensagemBloqueio` do schema;
- mantém nova guia, políticas por setor, Gemini, wallpaper e página de versão.
