## Publicação no GitPages

- Dê push nas modificações.

- No repositório, aguarde o workflow action terminar.

- Ao termino haverá uma nova branch chamada `gh-pages`.

- No repositório, vá em `Settings -> Pages`, em 'Source' deixe "Deploy from a branch" e em 'Branch' selecione a branch `gh-pages` e aperte em Save.


## Acessando a Página

1. Aguarde um pouco e recarregue a página 'Pages', o link da documentação publicada estará no inicio da página.

2. Na etapa `Run mkdocs gh-deploy --force` do Job de deploy do workflow, o link da documentação publicada estará logo ao fim da etapa.

3. No menu lateral direito do repositório, vá na engrenagem de configuração de 'About', em 'Website' selecione "Use your GitHub Pages website", e clique em Save Changes, o link para a documentação publicada ficará disponível no menu lateral. 