# Woody TV — endereço de entrada

Página independente para encaminhar visitantes para o alojamento atual da Woody TV. Não contém a aplicação, dados de utilizadores nem credenciais.

- Repositório: `joaosants97/woody-tv`, público.
- Endereço de entrada: `https://joaosants97.github.io/woody-tv/`.
- Destino atual: `https://woody-tv-jtaps.alwaysdata.net/`.
- Publicação: GitHub Pages, ramo `main`, pasta `/ (root)`.

## Funcionamento

O navegador abre o alojamento atual com `location.replace`, conservando os parâmetros e o fragmento do endereço de entrada. Se o JavaScript estiver desativado, fica disponível um link para continuar. A página não carrega bibliotecas externas, não usa cookies e não guarda dados.

O endereço GitHub funciona como entrada estável, mas o navegador passa a mostrar o endereço do alojamento depois do encaminhamento. Não é um proxy, não mantém o endereço GitHub na barra do navegador e não transfere sessões entre alojamentos. Não se pretende encaminhar caminhos adicionais depois de `/woody-tv/`.

## Mudar o alojamento no futuro

1. Abrir o repositório `joaosants97/woody-tv` no GitHub.
2. Abrir `index.html` e escolher o lápis para editar.
3. Localizar o link com `id="destination"`.
4. Substituir apenas o endereço no atributo `href` pelo novo endereço HTTPS.
5. Guardar a alteração com **Commit changes**.
6. Esperar pela conclusão da publicação em **Actions**.
7. Abrir `https://joaosants97.github.io/woody-tv/` numa janela privada e confirmar o novo destino.

As pessoas continuam a usar o mesmo endereço de entrada. Convém guardar esse endereço nos favoritos, porque o URL visível depois do encaminhamento é o do alojamento atual. Não alterar o nome da conta GitHub nem o nome do repositório, pois fazem parte do endereço. A continuidade do serviço depende da conta e das condições do GitHub; não existe garantia de disponibilidade eterna.

## Publicação inicial

Publicar apenas `index.html`, `.nojekyll` e este `README.md` num repositório público dedicado. Não publicar a pasta da aplicação Woody TV. Em **Settings → Pages**, escolher **Deploy from a branch**, ramo `main` e pasta `/ (root)`, depois **Save**. Verificar que o endereço público abre o destino correto.

## Documentação oficial

- [Disponibilidade gratuita, funcionamento e formato dos endereços do GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages)
- [Configuração da publicação a partir de um ramo](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [Limites e condições de utilização](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits)

Verificado em 3 de novembro de 2026: o GitHub Pages está incluído no GitHub Free para repositórios públicos e tem um limite flexível de tráfego de 100 GB por mês. Esta página de encaminhamento tem apenas alguns KB; o site e o vídeo continuam no respetivo alojamento.
