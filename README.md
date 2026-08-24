# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para nova guia, políticas por setor e bloqueio de sites.

**Versão:** `1.4.2`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa com pesquisa, Gemini e atalhos;
- configuração por `chrome.storage.managed`;
- bloqueio de sites com tela **Oops!**;
- wallpaper responsivo;
- página de versão e diagnóstico;
- atualização automática via CRX/XML.

## Página de versão

Na pesquisa da nova guia:

```text
sr://version
```

Na barra do Chrome, sem instalar protocolo:

```text
sr + Espaço + version
```

Para usar **`sr://version` diretamente na barra de endereços do Windows**, execute uma vez:

```powershell
.\deployment\Instalar-Protocolo-SR.ps1 -Test
```

O instalador registra `sr://` para o usuário atual. Use `-Machine` em PowerShell Administrador para registrar para a máquina.

## JSON no Google Admin

```json
{
  "setor": { "Value": "Fiscal" },
  "sitesBloqueados": { "Value": ["web.whatsapp.com", "discord.com"] },
  "sitesLiberados": { "Value": [] }
}
```

## v1.4.2

- corrige regressão que fazia as regras de bloqueio não serem recriadas de forma confiável;
- simplifica a sincronização do `declarativeNetRequest`;
- preserva regras existentes enquanto a política cloud ainda está carregando;
- sincroniza novamente após início, atualização e mudança de política;
- aceita domínios, URLs completas, `*.dominio.com` e `*://dominio.com/*`;
- mantém a página personalizada **Oops!** e a página de versão.

## Publicar

1. mantenha a mesma chave privada `.pem`;
2. gere o CRX da pasta `extension`;
3. publique o CRX e `deployment/updates.xml`.

Nunca publique a chave `.pem`.
