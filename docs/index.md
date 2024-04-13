## Documentação

Documentação completa em: [mkdocs.org](https://www.mkdocs.org)

## Instalação

- Clone o repositório.

- Mude para a branch correta.

- No terminal execute os seguintes comandos:
``` bash
python -m venv venv
```
seguido de:
``` bash
source venv/bin/activate
```
seguido de:
``` bash
pip install mkdocs-material
```
seguido de:
``` bash
mkdocs new .
```
por fim: 
``` bash
mkdocs serve
```

- Na IDE de preferência, edite o arquivo `mkdocs.yml` com as informações do projeto, as funcionalidades do mkdocs, etc:
``` yml
# Copyright (c) 2016-2023 Martin Donath <martin.donath@squidfunk.com>

# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to
# deal in the Software without restriction, including without limitation the
# rights to use, copy, modify, merge, publish, distribute, sublicense, and/or
# sell copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
# IN THE SOFTWARE.

# Project information:
site_name: Passo a Passo MkDocs
site_url: https://github.com/FabricioDeQueiroz/mkdocs-modo-facil

# Repository:
repo_name: mkdocs-modo-facil
repo_url: https://github.com/FabricioDeQueiroz/mkdocs-modo-facil

# Configuration:
theme:
  name: material
  features:
    - navigation.tabs
    - navigation.sections
    - toc.integrate
    - navigation.top
    - search.suggest
    - search.highlight
    - content.tabs.link
    - content.code.annotation
    - content.code.copy
    - announce.dismiss
    - content.tooltips
    - navigation.footer
    - navigation.indexes
    - navigation.tracking
    - search.share
    - toc.follow
  language: pt
  palette:
    - scheme: default
      toggle:
        icon: material/toggle-switch-off-outline 
        name: Switch to dark mode
      primary: teal
      accent: purple 
    - scheme: slate 
      toggle:
        icon: material/toggle-switch
        name: Switch to light mode    
      primary: teal
      accent: lime
  font:
    text: Roboto
    code: Roboto Mono

markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.inlinehilite
  - pymdownx.snippets
  - admonition
  - pymdownx.arithmatex:
      generic: true
  - footnotes
  - pymdownx.details
  - pymdownx.superfences
  - pymdownx.mark
  - attr_list

# extra:
#   social:
#     - icon: fontawesome/brands/github-alt
#       link: https://github.com/user
#     - icon: fontawesome/brands/twitter
#       link: https://twitter.com/user
#     - icon: fontawesome/brands/linkedin
#       link: https://www.linkedin.com/in/user

# copyright: |
  # &copy; 2023 <a href="https://github.com/user"  target="_blank" rel="noopener">Name</a>

# Page tree:
nav:
  - Instalação: index.md
  - Publicação: publishing.md
```

- No diretório `/docs`, se encontrará os diretórios e arquivos para criação das páginas da documentação.

- Crie um diretório `/.github/workflows` com o arquivo `ci.yml`, com o seguinte conteúdo (Mude conforme necessidade):
``` yml
name: ci 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configure Git Credentials
        run: |
          git config user.name github-actions[bot]
          git config user.email 41898282+github-actions[bot]@users.noreply.github.com
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v4
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: .cache
          restore-keys: |
            mkdocs-material-
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```

## Layout

- A disposição base dos arquivos é a seguinte:
```
mkdocs.yml    # Arquivo de configuração.
docs/
  index.md  # Homepage da documentação.
  ...       # Outros diretórios, arquivos markdown, assets, etc.
```