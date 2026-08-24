# Tema Senhor Contábil — Chrome

Extensão corporativa Manifest V3 para nova guia e políticas internas do Chrome.

**Versão:** `1.7.1`  
**ID:** `blebikojnakioblpeacdnnphclgeeaha`

## Recursos

- nova guia corporativa com pesquisa, Gemini e atalhos;
- configuração por `chrome.storage.managed`;
- bloqueio de sites com página **Oops!** personalizada;
- lista manual pelo JSON + lista TXT padrão + lista TXT remota;
- exceções por `sitesLiberados`;
- atualização automática da lista TXT remota sem republicar o CRX.

## Lista TXT

A forma recomendada para uma lista grande é hospedar um `.txt` por HTTPS (por exemplo no GitHub Pages) e informar a URL na **Política para extensões**.

```json
{
  "listaBloqueioUrl": {
    "Value": "https://antoniosilva-coder.github.io/Tema-SenhorContabil/blocklist.txt"
  },
  "intervaloAtualizacaoListaSegundos": {
    "Value": 30
  }
}
```

O TXT aceita uma entrada por linha:

```text
discord.com
*.facebook.com
203.0.113.10
https://exemplo.com/caminho
0.0.0.0 exemplo.com
||outroexemplo.com^
```

Linhas iniciadas por `#`, `;`, `!` ou `//` são ignoradas.

`sitesLiberados` sempre tem prioridade sobre a lista padrão, a lista remota e `sitesBloqueados`.

## Atualização rápida

- mudanças em `chrome.storage.managed` são aplicadas imediatamente pelo evento do Chrome;
- a extensão relê o JSON a cada **30 segundos** como segurança;
- o TXT remoto é verificado a cada **30 segundos** por padrão;
- o TXT é solicitado com cache desativado e um parâmetro anti-cache;
- se o conteúdo não mudou, as regras DNR não são recriadas;
- abrir uma Nova Guia dispara uma reconciliação adicional sem atrasar a interface.

Para alterar o intervalo do TXT:

```json
{
  "intervaloAtualizacaoListaSegundos": { "Value": 30 }
}
```

O mínimo confiável é `30`. A chave antiga `intervaloAtualizacaoListaMinutos` continua aceita por compatibilidade.

## Lista padrão embutida

O arquivo `extension/blocklist-default.txt` faz parte da extensão. Edite-o antes de gerar o CRX para definir bloqueios que devem existir mesmo sem internet.

Para desativá-lo em um grupo:

```json
{
  "usarListaBloqueioPadrao": { "Value": false }
}
```

## Exemplo completo

```json
{
  "setor": { "Value": "Fiscal" },
  "bloqueioAtivo": { "Value": true },
  "usarListaBloqueioPadrao": { "Value": true },
  "listaBloqueioUrl": {
    "Value": "https://antoniosilva-coder.github.io/Tema-SenhorContabil/blocklist.txt"
  },
  "intervaloAtualizacaoListaSegundos": { "Value": 30 },
  "sitesBloqueados": {
    "Value": ["discord.com"]
  },
  "sitesLiberados": {
    "Value": ["discord.com.br"]
  },
  "mensagemBloqueio": {
    "Value": "Se você precisa deste acesso para o trabalho, solicite ao seu gestor que abra uma solicitação para o setor de TI."
  }
}
```

## Publicar

1. mantenha a mesma chave privada `.pem`;
2. gere o CRX da pasta `extension`;
3. publique o CRX e `deployment/updates.xml`;
4. nunca publique a chave `.pem`.
