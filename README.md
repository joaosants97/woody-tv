# Woody TV — endereço fixo

Página independente que apresenta a Woody TV dentro de um iframe a ocupar toda a janela. O endereço visível mantém-se em `https://joaosants97.github.io/woody-tv/`; a aplicação e o vídeo continuam no respetivo alojamento. Este repositório público não contém a aplicação, dados de utilizadores nem credenciais.

- Repositório: `joaosants97/woody-tv`.
- Endereço fixo: `https://joaosants97.github.io/woody-tv/`.
- Alojamento atual: `https://woody-tv-jtaps.alwaysdata.net/`.
- Publicação: GitHub Pages, ramo `main`, pasta `/ (root)`.

## Funcionamento

O iframe abre diretamente o alojamento configurado em `src`, sem redirecionar a janela principal. A página de entrada não usa cookies, armazenamento local ou bibliotecas externas. Sem JavaScript, o iframe continua a abrir o endereço base; a aplicação incorporada pode necessitar de JavaScript para funcionar.

Quando há JavaScript, os parâmetros e o fragmento do endereço de entrada são copiados para o endereço do iframe. O parâmetro reservado `woody-path` permite abrir apenas estas páginas internas: `/`, `/watch.html`, `/users.html`, `/sala.html`, `/filmes.html`, `/programas.html`, `/resumos.html`, `/login.html` e `/device-limit.html`. Esse parâmetro é removido antes de abrir a aplicação. Valores inválidos ou repetidos mantêm o caminho base; nunca podem substituir o domínio ou o protocolo configurados em `src`. Não se encaminham caminhos adicionais depois de `/woody-tv/` nem se sincroniza a navegação interna com a barra de endereço.

A aplicação abre os seus novos separadores através desta máscara, por exemplo `?woody-path=%2Fusers.html`, para conservar o contexto da sessão e manter o PC central aberto. A navegação normal continua dentro do iframe. Um pedido `postMessage` sem dados de conta permite à aplicação confirmar o endereço da máscara; a resposta exige simultaneamente a origem exata do alojamento e a janela do próprio iframe. Na aplicação, a origem e a janela do pai também são validadas. Os links externos, os downloads e a página técnica de autorização do navegador não passam por este encaminhamento.

As permissões delegadas ao iframe são ecrã inteiro, reprodução automática, conteúdo protegido, imagem na imagem, manutenção do ecrã ligado e pedido de acesso ao armazenamento para navegadores que o exijam. O navegador pode continuar a exigir uma ação da pessoa para algumas destas funções. Não se delega acesso à câmara ou ao microfone. O iframe contém a aplicação de confiança e não usa `sandbox`.

## Requisitos do alojamento

O servidor da aplicação tem de permitir a incorporação pelo endereço exato do GitHub. A política HTTP `Content-Security-Policy` deve incluir `frame-ancestors 'self' https://joaosants97.github.io`, sem uma origem universal, e não pode existir um cabeçalho `X-Frame-Options` incompatível. A origem não inclui o caminho `/woody-tv/`.

A sessão incorporada deve usar cookies HTTPS com `Secure`, `HttpOnly`, `SameSite=None` e `Partitioned` (CHIPS), mantendo a validação de sessão e a proteção CSRF no servidor. A sessão fica associada ao contexto de incorporação: não se deve assumir que um início de sessão feito diretamente no alojamento também existe dentro desta página. Navegadores sem suporte para estes cookies ou com restrições adicionais podem impedir a sessão incorporada.

A aplicação deve manter a navegação normal dentro do iframe e não usar redirecionamentos para `window.top` nem links com `target="_top"`. Os novos separadores internos têm de usar a máscara, através de `embedded-navigation.mjs`, incluindo os atalhos do PC central; abrir diretamente o alojamento escolheria outra sessão. A página de entrada não consegue controlar a navegação interna de uma aplicação noutro domínio. As regras de autenticação, vídeo e segurança pertencem ao alojamento da aplicação.

## Mudar o alojamento no futuro

1. Preparar o novo alojamento HTTPS com a aplicação e os requisitos de incorporação e sessão descritos acima.
2. Abrir o repositório `joaosants97/woody-tv` no GitHub.
3. Abrir `index.html` e escolher o lápis para editar.
4. Localizar o iframe com `id="woody-app"`.
5. Substituir apenas o endereço no atributo `src` pelo novo endereço HTTPS. Esse atributo é a configuração única usada pela página, incluindo o código que acrescenta parâmetros e fragmentos.
6. Guardar a alteração com **Commit changes**.
7. Esperar pela conclusão da publicação em **Actions**.
8. Abrir `https://joaosants97.github.io/woody-tv/` e confirmar que o endereço permanece na barra, que o início de sessão funciona após atualizar a página e que o vídeo abre em ecrã inteiro.
9. Atualizar o endereço documentado neste `README.md`.

As pessoas continuam a usar o mesmo endereço fixo. Não alterar o nome da conta GitHub nem o nome do repositório, pois fazem parte do endereço. Esta página não é um proxy e não transfere sessões ou dados entre fornecedores; a migração desses elementos pertence à aplicação. A disponibilidade depende do GitHub e do alojamento atual.

## Publicação

Publicar apenas `index.html`, `.nojekyll`, este `README.md`, `manifest.webmanifest` e os seis ícones (`favicon.ico`, `apple-touch-icon.png`, `woody-16.png`, `woody-32.png`, `woody-192.png` e `woody-512.png`) no repositório público dedicado. Não publicar a pasta da aplicação Woody TV. Em **Settings → Pages**, escolher **Deploy from a branch**, ramo `main` e pasta `/ (root)`, depois **Save**. Após cada publicação, verificar o endereço fixo, o início de sessão e o leitor incorporado.

Os ícones são cópias exatas dos ícones originais da aplicação. A declaração `apple-touch-icon` fica na página principal, para o iPhone usar o ícone do Woody ao adicionar o endereço fixo ao ecrã principal. Os caminhos são relativos a `/woody-tv/`, incluindo o início e âmbito do manifesto, para continuar a abrir a máscara. Os ícones ficam no GitHub e não dependem do fornecedor da aplicação. Um atalho já instalado no iPhone pode ter de ser removido e adicionado novamente para atualizar o ícone.
