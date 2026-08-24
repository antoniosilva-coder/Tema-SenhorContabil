# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para nova guia, políticas por setor e bloqueio de sites.

**Versão:** `1.4.1`  
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

## v1.4.1

- corrige a sincronização dos bloqueios após atualização/reinício;
- mantém cache da última política válida durante atraso da política cloud;
- restaura sincronização ao iniciar o service worker;
- adiciona tentativas automáticas após instalação/inicialização;
- corrige `sr://version` no Windows usando uma ponte HTTPS + redirecionamento interno;
- página de versão mostra sites configurados e regras de bloqueio ativas.

## Publicar

1. mantenha a mesma chave privada `.pem`;
2. gere o CRX da pasta `extension`;
3. publique o CRX e `deployment/updates.xml`.

Nunca publique a chave `.pem`.
