# Tema Senhor Contábil para Google Chrome

Extensão Manifest V3 que substitui a página de nova guia por uma versão corporativa com:

- wallpaper institucional fixo;
- relógio e pesquisa do Google;
- atalhos corporativos Sólides, Minha Jornada e Movidesk;
- acesso rápido no canto superior direito com Gmail e menu de apps (Gmail, Google Chat, Drive, Gemini, Google Calendar, Google Docs, Google Sheets e Google Meet);
- identidade visual nas cores da Senhor Contábil;
- nenhuma opção de troca de wallpaper dentro da nova guia;
- não solicita acesso à agenda, e-mail ou conteúdo das páginas; os itens do menu são apenas atalhos.

ID estável da versão auto-hospedada: `blebikojnakioblpeacdnnphclgeeaha`.

## Testar no computador

1. Extraia o pacote.
2. Abra `chrome://extensions`.
3. Ative **Modo do desenvolvedor**.
4. Clique em **Carregar sem compactação**.
5. Selecione a pasta `extension`.
6. Abra uma nova guia.

Esse modo serve somente para teste. Nele, o usuário ainda consegue remover a extensão.

## Bloquear a troca do wallpaper de verdade

O bloqueio depende do Chrome Enterprise. A configuração recomendada é:

1. Publique a extensão de forma privada na Chrome Web Store ou hospede o `.crx` e o `updates.xml` em um endereço HTTPS da empresa.
2. No Google Admin, acesse **Dispositivos > Chrome > Apps e extensões > Usuários e navegadores**.
3. Adicione a extensão e defina **Política de instalação: Forçar instalação**.
4. Em **Dispositivos > Chrome > Configurações > Usuários e navegadores > Geral**, defina **Cor personalizada do tema** como `#142882`. Essa política impede que o usuário altere a cor do navegador.
5. Para garantir que o wallpaper não seja contornado, desative o modo anônimo e o modo visitante. Extensões não substituem a nova guia anônima.
6. Se necessário, bloqueie outras extensões por padrão e libere somente as aprovadas. Isso impede que outra extensão de nova guia assuma o lugar desta.

Após aplicar, reinicie o Chrome e valide em `chrome://policy`. A extensão deve aparecer como instalada por política e não permitir **Remover** ou **Desativar**.

## Opções de política incluídas

- `deployment/policy-template.json`: mantém outras extensões permitidas.
- `deployment/policy-strict-template.json`: bloqueia extensões não autorizadas.
- `deployment/Aplicar-Politica-Windows.ps1`: aplica as políticas diretamente no Windows usando um `UpdateUrl` HTTPS.

Exemplo de execução no PowerShell como administrador:

```powershell
.\Aplicar-Politica-Windows.ps1 -UpdateUrl 'https://intranet.senhorcontabil.com.br/tema/updates.xml' -ModoEstrito
```

O modo estrito também desativa navegação anônima e modo visitante para evitar sessões fora da identidade visual corporativa.

## Empacotar para auto-hospedagem

1. Abra `chrome://extensions` e ative o modo de desenvolvedor.
2. Clique em **Compactar extensão**.
3. Em **Diretório raiz da extensão**, selecione `extension`.
4. Na primeira compactação, use `publisher/PRIVATE-KEY-KEEP-SECRET.pem` como arquivo de chave privada.
5. Hospede o `.crx` gerado e uma cópia de `deployment/updates.xml.example` ajustada em um servidor HTTPS.

Não compartilhe nem coloque a chave privada em servidor público. Ela é necessária para publicar atualizações com o mesmo ID.

Em computadores Windows, extensões auto-hospedadas fora da Chrome Web Store podem exigir que a máquina esteja vinculada a um domínio Active Directory. Para ambientes gerenciados apenas pela nuvem, a publicação privada na Chrome Web Store costuma ser a opção mais simples.

Se a extensão for enviada à Chrome Web Store e receber outro ID, use o ID exibido no painel da loja nos modelos de política.

## Atualizações

Ao alterar a extensão:

1. aumente a versão em `extension/manifest.json`;
2. compacte novamente usando a mesma chave privada;
3. atualize o atributo `version` do `updates.xml`;
4. substitua o `.crx` no servidor sem alterar as URLs.

## Referências oficiais

- https://developer.chrome.com/docs/extensions/develop/ui/override-chrome-pages
- https://chromeenterprise.google/policies/extension-install-forcelist/
- https://chromeenterprise.google/policies/browser-theme-color/
- https://support.google.com/chrome/a/answer/7532015
- https://support.google.com/chrome/a/answer/9302896

## v1.1.8
- Ícones oficiais adicionados para Calendar, Docs, Sheets e Meet no menu de aplicativos.
- Os ícones são carregados diretamente dos assets públicos do Google (`gstatic.com`).

## v1.2.1 - Página diferente por setor

A mesma extensão agora aceita configuração gerenciada via `chrome.storage.managed`.

É possível definir no Google Admin, por OU/grupo, sem gerar CRX novo:
- wallpaper;
- título da página;
- cores principais;
- relógio;
- texto da pesquisa;
- atalhos centrais;
- Gmail e menu de nove pontos;
- lista de aplicativos do menu.

Veja `CONFIGURAR-POR-SETOR.md` e os exemplos em `deployment/configs-setores/`.
