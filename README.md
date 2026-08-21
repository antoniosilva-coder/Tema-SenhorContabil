# Tema Senhor Contábil para Google Chrome

Extensão corporativa Manifest V3 que substitui a página de **Nova guia** do Google Chrome por uma página institucional da Senhor Contábil.

A versão atual do projeto é a **v1.2.1**, com suporte a configuração diferente por setor através de políticas gerenciadas do Chrome/Google Admin.

**ID estável da extensão:** `blebikojnakioblpeacdnnphclgeeaha`

---

## Estado atual — v1.2.1

A versão atual possui:

- wallpaper institucional carregado por URL;
- relógio;
- pesquisa do Google;
- atalhos corporativos abaixo da pesquisa;
- atalhos padrão para:
  - Sólides;
  - Minha Jornada;
  - Movidesk;
- acesso rápido ao Gmail no canto superior direito;
- menu de aplicativos no botão de nove pontos;
- menu padrão com:
  - Gmail;
  - Google Chat;
  - Drive;
  - Gemini;
  - Calendar;
  - Docs;
  - Sheets;
  - Meet;
- ícones externos com fallback quando uma imagem não carrega;
- identidade visual baseada nas cores da Senhor Contábil;
- configuração diferente por setor sem precisar gerar um novo CRX;
- gerenciamento por `chrome.storage.managed`;
- possibilidade de atualizar a política de uma OU/grupo pelo Google Admin;
- atualização automática da interface quando a política gerenciada muda;
- somente a permissão `storage` na versão atual;
- nenhuma leitura de Gmail, Agenda, Drive ou conteúdo de páginas.

Os aplicativos do menu são apenas **atalhos**.

---

# Histórico de alterações

## v1.1.0 — Versão-base

Versão inicial usada como base para as evoluções posteriores.

Principais recursos:

- nova guia personalizada;
- wallpaper institucional;
- relógio;
- pesquisa do Google;
- identidade visual da Senhor Contábil;
- ícones locais da extensão;
- `update_url` apontando para o GitHub Pages;
- ID estável da extensão através da mesma chave de empacotamento;
- estrutura para distribuição do CRX e `updates.xml`.

> A versão `1.1.1` não está entre os pacotes disponibilizados neste histórico.

---

## v1.1.2 — Atalhos corporativos e correções

Foi consolidada a página inicial com:

- correção da estrutura HTML/CSS da nova guia;
- correção de codificação UTF-8;
- manutenção do wallpaper, relógio e busca do Google;
- adição dos atalhos:
  - Sólides;
  - Minha Jornada;
  - Movidesk;
- atalhos exibidos em botões circulares;
- tentativa de obtenção do favicon através do recurso de favicon do próprio Chrome;
- inclusão temporária da permissão `favicon` no manifesto;
- versão do `manifest.json` e `updates.xml` atualizada para `1.1.2`.

---

## v1.1.3 — Menu Google no canto superior direito

Foi adicionada uma área inspirada na página inicial do Google.

Alterações:

- link **Gmail** no canto superior direito;
- botão de nove pontos para abrir o menu de aplicativos;
- menu flutuante com:
  - Gmail;
  - Google Chat;
  - Drive;
  - Gemini;
  - Agenda;
- suporte a abrir/fechar o menu ao clicar no botão;
- fechamento do menu ao clicar fora;
- fechamento através da tecla `Esc`;
- suporte a foco por teclado;
- favicons também passaram a ser usados nos aplicativos do menu;
- versão atualizada para `1.1.3`.

---

## v1.1.4 — Ícones carregados diretamente da internet

A estratégia de ícones foi alterada para evitar problemas com os favicons internos do Chrome.

Alterações:

- removida a permissão `favicon`;
- removido o carregamento através de `chrome://favicon` / `/_favicon/`;
- ícones do Google passaram a usar URLs públicas diretas;
- atalhos corporativos passaram a usar URLs externas para seus ícones/favicons;
- redução das permissões da extensão;
- versão atualizada para `1.1.4`.

---

## v1.1.5 — Melhor contraste no canto superior direito

A região de Gmail e do menu de aplicativos estava com pouco contraste sobre partes claras do wallpaper.

Alterações visuais:

- criação de fundo azul-escuro translúcido atrás do Gmail e do botão de aplicativos;
- borda discreta no componente;
- sombra para separar o menu do wallpaper;
- texto Gmail em branco mais forte;
- botão de nove pontos com fundo sutil;
- aumento da legibilidade sobre nuvens e áreas claras da imagem;
- versão atualizada para `1.1.5`.

---

## v1.1.6 — Correção e fallback dos ícones

Os ícones externos foram revisados para melhorar a consistência.

Alterações:

- Sólides passou a usar logo externo específico;
- Minha Jornada passou a usar a identidade da Senhor Contábil;
- Movidesk passou a usar favicon externo do domínio relacionado;
- ícones do Google receberam URL alternativa de fallback;
- Gemini passou a usar outro asset externo;
- criado tratamento de erro para imagem externa:
  1. tenta o ícone principal;
  2. tenta uma segunda URL;
  3. se ambas falharem, exibe uma letra de fallback;
- suporte a ícone largo para logos que não funcionam bem em formato quadrado;
- aumento do tamanho visual dos ícones;
- versão atualizada para `1.1.6`.

---

## v1.1.7 — Novos aplicativos Google

O menu de nove pontos foi expandido.

Alterações:

- **Agenda** passou a ser apresentada como **Google Calendar**;
- adicionados:
  - Google Docs;
  - Google Sheets;
  - Google Meet;
- mantidos:
  - Gmail;
  - Google Chat;
  - Drive;
  - Gemini;
- cada novo aplicativo recebeu URL e ícone correspondente;
- versão atualizada para `1.1.7`.

---

## v1.1.8 — Padronização final dos aplicativos

O menu foi refinado para ficar mais compacto.

Alterações:

- nomes reduzidos no menu:
  - `Google Calendar` → `Calendar`;
  - `Google Docs` → `Docs`;
  - `Google Sheets` → `Sheets`;
  - `Google Meet` → `Meet`;
- padronização dos ícones dos novos aplicativos com assets públicos do Google;
- versão atualizada para `1.1.8`.

---

## v1.2.0 — Experimento com Google Agenda

Esta versão introduziu uma integração real com a API do Google Calendar.

Alterações:

- permissão `identity` adicionada;
- `host_permissions` para `https://www.googleapis.com/*`;
- configuração OAuth no `manifest.json`;
- escopo somente leitura:

```text
https://www.googleapis.com/auth/calendar.readonly
```

- botão para conectar a conta Google;
- obtenção de token via `chrome.identity.getAuthToken()`;
- consulta da agenda principal do usuário;
- busca de compromissos dos próximos 7 dias;
- exibição de até 3 compromissos na nova guia;
- tratamento para eventos de dia inteiro;
- tratamento de token expirado/401;
- mensagem de configuração quando o OAuth Client ID ainda não estivesse definido;
- fallback local do wallpaper caso a imagem remota falhasse;
- arquivo `CONFIGURAR-AGENDA.md` incluído no pacote.

### Importante

A integração de Agenda da v1.2.0 foi **removida da linha atual na v1.2.1**.

A versão atual não solicita acesso ao Google Calendar. O item `Calendar` é apenas um link.

---

## v1.2.1 — Configuração por setor

Esta é a arquitetura atual do projeto.

A extensão passou a usar:

```javascript
chrome.storage.managed
```

Com isso, o mesmo CRX pode ser instalado em toda a empresa e receber uma configuração diferente para cada OU ou grupo.

### Novos arquivos

```text
extension/
├── config-default.js
├── manifest.json
├── newtab.html
├── newtab.js
├── schema.json
├── styles.css
└── assets/
```

Também foram adicionados exemplos de configuração:

```text
deployment/configs-setores/
├── GERAL.json
├── EXEMPLO-RH.json
├── EXEMPLO-TI.json
└── MODELO-COMPLETO.json
```

### Mudanças técnicas

- removida a integração OAuth da Agenda;
- removida a permissão `identity`;
- removido acesso à Google Calendar API;
- adicionada permissão `storage`;
- adicionado:

```json
"storage": {
  "managed_schema": "schema.json"
}
```

- `schema.json` passou a declarar quais propriedades podem ser administradas;
- `config-default.js` passou a concentrar a configuração padrão da empresa;
- `newtab.js` passou a:
  - carregar a configuração padrão;
  - consultar `chrome.storage.managed`;
  - mesclar a política recebida com o padrão;
  - renderizar os atalhos dinamicamente;
  - renderizar o menu Google dinamicamente;
  - trocar wallpaper, título, cores e opções de interface;
  - ouvir alterações em `chrome.storage.onChanged`;
  - reaplicar a configuração sem depender de uma nova compilação.

---

# Configurações disponíveis por setor

O `schema.json` declara as propriedades aceitas pela extensão. **Ele não usa `Value`.**

No **Google Admin > Política para extensões**, cada propriedade deve ser enviada no formato:

```json
{
  "nomeDaPolitica": {
    "Value": "valor"
  }
}
```

Depois da validação pelo Chrome, `chrome.storage.managed` entrega à extensão somente o valor:

```javascript
{
  nomeDaPolitica: "valor"
}
```

Atualmente são aceitas: `setor`, `tituloPagina`, `wallpaperUrl`, `faviconUrl`, `corPrimaria`, `corDestaque`, `mostrarRelogio`, `placeholderPesquisa`, `mostrarGmail`, `gmailUrl`, `mostrarMenuGoogle`, `tituloMenuGoogle`, `atalhos` e `appsGoogle`.

# Exemplo correto para o Google Admin

```json
{
  "setor": {
    "Value": "Fiscal"
  },
  "tituloPagina": {
    "Value": "Senhor Contábil - Fiscal"
  },
  "mostrarRelogio": {
    "Value": false
  },
  "atalhos": {
    "Value": [
      {
        "nome": "Sistema Fiscal",
        "url": "https://sistema.exemplo/",
        "icone": "https://sistema.exemplo/icone.png",
        "fallback": "F",
        "iconeLargo": false
      }
    ]
  }
}
```

# Fluxo da política

```text
schema.json (tipos permitidos, sem Value)
        ↓
Google Admin > Política para extensões
{ chave: { Value: valor } }
        ↓
Chrome valida a política
        ↓
chrome.storage.managed
{ chave: valor }
        ↓
newtab.js aplica a configuração
```

# Como configurar no Google Admin

1. Acesse **Dispositivos > Chrome > Apps e extensões**.
2. Selecione a OU ou grupo desejado.
3. Abra **Tema Senhor Contábil**.
4. Localize **Política para extensões**.
5. Cole/importa o JSON no formato com `Value`.
6. Salve.
7. Abra `chrome://policy` no computador e clique em **Recarregar políticas**.
8. Feche e abra uma nova guia.
9. No Console da nova guia, valide:

```javascript
chrome.storage.managed.get(null, config => {
  console.log("POLÍTICA:", config);
  console.log("ERRO:", chrome.runtime.lastError?.message || "nenhum");
});
```

Um teste mínimo recomendado no Admin é:

```json
{
  "tituloPagina": {
    "Value": "TESTE VIA GOOGLE ADMIN"
  },
  "mostrarRelogio": {
    "Value": false
  },
  "placeholderPesquisa": {
    "Value": "POLÍTICA APLICADA"
  }
}
```

# Teste local definitivo no Windows

Para separar problema da extensão de problema do Admin, injete uma política temporária pelo Registro:

```powershell
$P = "HKLM:\SOFTWARE\Policies\Google\Chrome\3rdparty\extensions\blebikojnakioblpeacdnnphclgeeaha\policy"
New-Item -Path $P -Force
New-ItemProperty -Path $P -Name "tituloPagina" -PropertyType String -Value "TESTE LOCAL FUNCIONOU" -Force
New-ItemProperty -Path $P -Name "mostrarRelogio" -PropertyType DWord -Value 0 -Force
```

Reinicie o Chrome e consulte:

```javascript
chrome.storage.managed.get(null, console.log)
```

Se aparecerem os valores, `manifest.json`, `schema.json` e `chrome.storage.managed` estão funcionando.

Remova o teste depois:

```powershell
Remove-Item "HKLM:\SOFTWARE\Policies\Google\Chrome\3rdparty\extensions\blebikojnakioblpeacdnnphclgeeaha\policy" -Recurse -Force
```

# Diagnóstico

| Resultado | Problema provável |
|---|---|
| Registro não funciona | extensão/schema |
| Registro funciona, Admin não aparece em `chrome://policy` | aplicação/escopo no Admin |
| Admin aparece com erro | JSON/tipo incompatível com schema |
| `storage.managed` tem valores | política entregue corretamente |
| valores chegam mas tela não muda | `newtab.js` / aplicação visual |

# Configuração padrão

`extension/config-default.js` continua sendo o fallback usado quando nenhuma política é entregue ao navegador.

# Alterações que não exigem novo CRX

Não é necessário gerar outro CRX para mudar valores de propriedades já existentes no `schema.json`, como wallpaper, atalhos, links, cores, visibilidade do relógio/Gmail/menu e título.

# Quando é obrigatório gerar novo CRX

Gere nova versão quando alterar código, estrutura, permissões, `schema.json`, `config-default.js`, HTML/CSS/JS ou assets locais. Use a mesma chave `.pem` para manter o ID estável e atualize a versão também no `updates.xml`.

# Atualização do wallpaper

Se `wallpaperUrl` aponta para uma imagem externa, o arquivo pode ser substituído mantendo o mesmo caminho sem gerar novo CRX. Pode haver atraso por cache/CDN.

# Observação sobre exceções

Se futuramente forem criadas políticas como `bloquearWhatsapp`, primeiro essa propriedade precisa existir no `schema.json` e a extensão precisa implementar a funcionalidade. Só então ela poderá ser enviada pelo Admin no mesmo formato:

```json
{
  "bloquearWhatsapp": {
    "Value": false
  }
}
```

# Referências oficiais

- Chrome managed storage: https://developer.chrome.com/docs/extensions/reference/manifest/storage
- Chrome Enterprise — Apps e extensões: https://support.google.com/chrome/a/answer/6177447
- Chromium — Configuring Apps and Extensions by Policy: https://www.chromium.org/administrators/configuring-policy-for-extensions/
