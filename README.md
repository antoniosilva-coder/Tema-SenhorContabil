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

Atualmente o `schema.json` permite controlar:

| Propriedade | Função |
|---|---|
| `setor` | Nome administrativo do setor |
| `tituloPagina` | Título exibido na aba |
| `wallpaperUrl` | Wallpaper usado pelo setor |
| `faviconUrl` | Ícone da nova guia |
| `corPrimaria` | Cor principal da interface |
| `corDestaque` | Cor usada nos destaques |
| `mostrarRelogio` | Exibe ou oculta o relógio |
| `placeholderPesquisa` | Texto exibido dentro da busca |
| `mostrarGmail` | Exibe ou oculta o Gmail no canto direito |
| `gmailUrl` | URL usada pelo atalho do Gmail |
| `mostrarMenuGoogle` | Exibe ou oculta o botão de nove pontos |
| `tituloMenuGoogle` | Título interno do menu |
| `atalhos` | Lista de atalhos centrais |
| `appsGoogle` | Lista de aplicativos do menu |

---

# Exemplo de política para um setor

```json
{
  "setor": "Fiscal",
  "tituloPagina": "Senhor Contábil - Fiscal",
  "wallpaperUrl": "https://exemplo.com/wallpaper-fiscal.png",
  "mostrarRelogio": true,
  "atalhos": [
    {
      "nome": "Sistema Fiscal",
      "url": "https://sistema.exemplo/",
      "icone": "https://sistema.exemplo/icone.png",
      "fallback": "F",
      "iconeLargo": false
    },
    {
      "nome": "Minha Jornada",
      "url": "https://minhajornada-sso.senhorcontabil.com.br/",
      "icone": "https://antoniosilva-coder.github.io/Tema-SenhorContabil/Logo-Contabil.png",
      "fallback": "J",
      "iconeLargo": false
    }
  ]
}
```

---

# Como funciona a configuração por setor

Fluxo:

```text
config-default.js
       ↓
configuração padrão da empresa
       ↓
Google Admin envia a política da OU/grupo
       ↓
chrome.storage.managed
       ↓
newtab.js mescla as configurações
       ↓
nova guia é renderizada
```

Exemplo:

```text
Mesma extensão
      │
      ├── OU Fiscal    → configuração Fiscal
      ├── OU RH        → configuração RH
      ├── OU Contábil  → configuração Contábil
      └── OU TI        → configuração TI
```

Não é necessário gerar um CRX diferente para cada setor.

---

# Como configurar no Google Admin

1. Acesse o Google Admin.
2. Vá em **Dispositivos > Chrome > Apps e extensões > Usuários e navegadores**.
3. Selecione a OU ou grupo desejado.
4. Abra a extensão **Tema Senhor Contábil**.
5. Localize **Política para extensões**.
6. Informe o JSON correspondente ao setor.
7. Salve a política.
8. No computador de teste, abra:

```text
chrome://policy
```

9. Atualize as políticas.
10. Abra uma nova guia.

---

# Configuração padrão

O arquivo:

```text
extension/config-default.js
```

é usado quando nenhuma política específica é entregue ao navegador.

Ele funciona como o padrão global da empresa.

Exemplo conceitual:

```javascript
window.SENHOR_CONTABIL_DEFAULT_CONFIG = {
  setor: "Geral",
  tituloPagina: "Senhor Contábil",
  wallpaperUrl: "https://.../wallpaper.png",
  mostrarRelogio: true,
  mostrarGmail: true,
  mostrarMenuGoogle: true,
  atalhos: [],
  appsGoogle: []
};
```

---

# Como alterar sem gerar um novo CRX

Não é necessário atualizar a extensão quando a alteração puder ser realizada através de uma propriedade já existente no `schema.json`.

Exemplos:

- trocar wallpaper de um setor;
- adicionar/remover atalhos;
- trocar URL de um sistema;
- trocar ícone de um atalho;
- esconder Gmail;
- esconder o menu de aplicativos;
- alterar os aplicativos do menu;
- mudar cores;
- mudar título;
- esconder o relógio.

Nesse caso basta alterar a política da OU/grupo no Google Admin.

---

# Quando é obrigatório gerar um novo CRX

É necessário publicar uma nova versão quando houver alteração em código ou estrutura da extensão, como:

- `manifest.json`;
- `schema.json`;
- `config-default.js`;
- `newtab.html`;
- `newtab.js`;
- `styles.css`;
- arquivos locais dentro de `assets/`;
- inclusão de uma nova permissão;
- criação de uma nova funcionalidade;
- criação de uma nova propriedade que ainda não exista no `schema.json`.

Fluxo de atualização:

```text
1. alterar o código
2. aumentar a versão no manifest.json
3. gerar novamente o CRX usando a MESMA chave privada
4. alterar a versão no updates.xml
5. substituir o CRX publicado
6. publicar o novo updates.xml
```

Exemplo:

```text
1.2.1 → 1.2.2
```

A versão declarada no `manifest.json` e no `updates.xml` deve ser a mesma.

---

# Atualização do wallpaper sem atualizar a extensão

Se `wallpaperUrl` apontar para uma imagem externa e o arquivo remoto for substituído mantendo exatamente o mesmo caminho e nome, a extensão poderá receber a nova imagem sem gerar outro CRX.

Exemplo:

```text
https://antoniosilva-coder.github.io/Tema-SenhorContabil/wallpaper-senhor-contabil.png
```

Mantendo essa URL e substituindo apenas o conteúdo de `wallpaper-senhor-contabil.png`, a nova imagem será carregada quando o cache for renovado.

Pode existir atraso causado pelo cache do navegador/CDN.

---

# Estrutura de exceções por grupo

O Google Admin pode ser usado com OUs para regras padrão e grupos para exceções.

Exemplo conceitual:

```text
OU Fiscal
└── bloqueio de WhatsApp = true

Grupo EXC - WhatsApp
└── bloqueio de WhatsApp = false
```

Assim, um usuário pode continuar pertencendo ao setor Fiscal e receber somente a exceção necessária através do grupo.

## Atenção

A propriedade `bloquearWhatsapp` **não existe na v1.2.1 atual**.

O código atual gerencia a aparência e os atalhos da nova guia. Para transformar esse exemplo em uma função real da extensão seria necessário adicionar uma nova implementação, por exemplo:

1. adicionar `bloquearWhatsapp` ao `schema.json`;
2. adicionar a lógica de bloqueio/redirecionamento;
3. solicitar as permissões necessárias no `manifest.json`;
4. aumentar a versão;
5. gerar e publicar um novo CRX.

Depois que a propriedade existir, a OU pode definir o padrão e um grupo de exceção pode sobrescrever somente esse valor.

### Recomendação de organização

```text
OUs
├── Fiscal
├── Contábil
├── RH
├── Financeiro
└── TI

Grupos de exceção
├── EXC - WhatsApp
├── EXC - Gemini
├── EXC - Redes Sociais
└── EXC - Sistemas TI
```

Evite criar várias OUs apenas por causa de exceções individuais.

---

# Como criar uma extensão desse modelo do zero

## 1. Estrutura mínima

```text
extension/
├── manifest.json
├── schema.json
├── config-default.js
├── newtab.html
├── newtab.js
├── styles.css
└── assets/
```

## 2. Manifesto

Exemplo mínimo:

```json
{
  "manifest_version": 3,
  "name": "Nova Guia Corporativa",
  "version": "1.0.0",
  "permissions": [
    "storage"
  ],
  "storage": {
    "managed_schema": "schema.json"
  },
  "chrome_url_overrides": {
    "newtab": "newtab.html"
  }
}
```

## 3. Schema de políticas

Exemplo:

```json
{
  "type": "object",
  "properties": {
    "setor": {
      "type": "string"
    },
    "wallpaperUrl": {
      "type": "string"
    },
    "mostrarRelogio": {
      "type": "boolean"
    }
  }
}
```

## 4. Configuração padrão

```javascript
window.DEFAULT_CONFIG = {
  setor: "Geral",
  wallpaperUrl: "https://exemplo.com/wallpaper.png",
  mostrarRelogio: true
};
```

## 5. Leitura da política

```javascript
chrome.storage.managed.get(null, (policy) => {
  const config = {
    ...window.DEFAULT_CONFIG,
    ...policy
  };

  console.log(config);
});
```

A partir daí, os valores de `config` são usados para montar a página.

---

# Empacotamento e chave privada

Para manter o mesmo ID da extensão, todas as atualizações devem ser empacotadas usando a **mesma chave privada `.pem`**.

A chave privada:

- não deve ser enviada para o GitHub;
- não deve ser compartilhada;
- não deve ficar dentro do pacote público da extensão;
- deve possuir backup seguro.

Se uma nova chave for usada, o Chrome gera outro ID e passa a considerar o pacote como outra extensão.

---

# Arquivo `updates.xml`

A extensão auto-hospedada utiliza o `updates.xml` para informar ao Chrome onde está o CRX e qual é a versão disponível.

Em cada atualização:

```text
manifest.json = nova versão
updates.xml   = mesma nova versão
```

Exemplo:

```xml
<updatecheck
  codebase="https://antoniosilva-coder.github.io/Tema-SenhorContabil/tema-senhor-contabil.crx"
  version="1.2.2" />
```

---

# Testes antes da publicação

Para testar uma versão local:

1. abra `chrome://extensions`;
2. habilite **Modo do desenvolvedor**;
3. clique em **Carregar sem compactação**;
4. selecione a pasta `extension`;
5. faça as alterações;
6. use **Recarregar** na extensão;
7. abra novamente a nova guia.

Se a extensão de produção estiver instalada à força por política com o mesmo ID, o Chrome pode impedir o carregamento da cópia local.

Nesse cenário, utilize:

- uma OU de testes sem a instalação forçada; ou
- uma versão DEV com outro ID.

---

# Distribuição corporativa

Para uso empresarial, recomenda-se:

- instalar a extensão através do Google Admin;
- utilizar instalação forçada;
- manter a mesma URL de atualização;
- manter o mesmo ID;
- armazenar a chave `.pem` somente em local seguro;
- validar políticas em `chrome://policy`;
- testar atualizações primeiro em uma OU/grupo de TI;
- somente depois liberar para toda a empresa.

---

# Resumo da evolução

```text
v1.1.0
Nova guia corporativa básica
        ↓
v1.1.2
Atalhos Sólides / Minha Jornada / Movidesk
        ↓
v1.1.3
Gmail + menu de nove pontos
        ↓
v1.1.4
Ícones externos e remoção da permissão favicon
        ↓
v1.1.5
Melhoria de contraste do menu superior
        ↓
v1.1.6
Ícones corrigidos + fallback automático
        ↓
v1.1.7
Calendar + Docs + Sheets + Meet
        ↓
v1.1.8
Padronização visual/nomenclatura dos apps
        ↓
v1.2.0
Experimento de integração com Google Calendar API
        ↓
v1.2.1
Remoção do OAuth da Agenda + configuração dinâmica por setor
```

---

## Versão atual recomendada

**v1.2.1 — configuração por setor via `chrome.storage.managed`.**

Essa é a base recomendada para as próximas evoluções do projeto.
