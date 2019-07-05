PUG-SE
======

## Requirements

- [Python 2 ou 3](https://www.python.org);
- [Cookiecutter](https://github.com/audreyr/cookiecutter);
- [Pelican](https://github.com/getpelican/pelican);
- Tema [Malt](https://github.com/pug-se/malt);

## Preparando o ambiente de desenvolvimento

Primeiramente, [crie um fork](https://help.github.com/articles/fork-a-repo/) deste repositório e em seguida clone o fork localmente:

    $ git clone --recursive https://github.com/<SEU-USUÁRIO>/pug-se.github.io.git -b develop

O parâmetro `--recursivo` é importante para fazer o clone também dos submódulos do projeto. Já o parâmetro `-b develop` indica que o clone vai ser feito da branch `develop` em que se encontra o projeto pelican.

> Nota: a branch principal `master` é onde se encontra o site auto-gerado (arquivos estáticos como html, css, js) pois é lá onde o github pages espera encontrar o conteúdo para publicação do site. Para maiores informações de como funciona o github pages para usuários, organizações e projetos, acesse [aqui](https://help.github.com/articles/user-organization-and-project-pages/).

Será criada a cópia local na qual iremos trabalhar:

    $ cd pug-se.github.io

Para facilitar o desenvolvimento, é recomendável criar um ambiente virtual utilizando o [virtualenvwrapper](http://virtualenvwrapper.readthedocs.org/en/latest/). No exemplo a seguir, criamos um ambiente chamado `pug-se`:

    $ mkvirtualenv --python=python --no-site-packages pug-se

Uma vez criado o ambiente virtual com o comando acima, ele deve estar automaticamente ativado. Caso não esteja, e sempre que se quiser ativá-lo, fazemos:

    $ workon pug-se

> #### Utilizando o [Pyenv](https://github.com/pyenv/pyenv) + [Virtualenv](https://github.com/pyenv/pyenv-virtualenv)
> 
> Outra maneira de preparar o ambiente é utilizando o pyenv. Ele facilita bastante o gerenciamento de versões do python em uma única máquina e mais ainda quando a raiz do projeto tem um arquivo `.python-version` com o nome do ambiente virtual que criamos, pois o Pyenv automaticamente ativa esse ambiente quando estramos na pasta.

A instalação das dependências é feita utilizando o [pip](http://www.pip-installer.org/en/latest/):

    (pug-se)$ pip install -r requirements.txt

Após este passo, os módulos Pelican, Markdown e demais dependências necessárias estarão instalados no ambiente virtual criado previamente com o virtualenvwrapper.

## Testando a instalação e visualizando o site

O Pelican vem com um pequeno servidor de desenvolvimento para facilitar a atualização dos arquivos HTML estáticos gerados. Para iniciar o servidor, é recomendado utililzar o [Makefile](https://github.com/pug-se/pug-se.github.io/blob/develop/Makefile) que acompanha o código. Entre outras coisas, o Makefile disponibiliza regras como o `html` (que gera nosso site) e o `serve` (que inicia um servidor local para servir o site):

    (pug-se)$ make html serve

Neste ponto, a geração dos arquivos estáticos do site foi realizada (ver conteúdo no diretório pug-se.github.io) e o servidor deve estar rodando em background, aceitando requisições em [http://localhost:8000](http://localhost:8000).

## Criando e modificando conteúdo

A [documentação do Pelican](http://docs.getpelican.com/en/stable/content.html) é bastante completa nesse ponto. Em caso de dúvidas, pedimos que poste sua pergunta nas [issues](https://github.com/pug-se/pug-se.github.io/issues) do projeto, de preferência marcando-a com o label *question*.

## Publicando o site

Para publicar o conteúdo gerado podemos utilizar a regra `github`, também definida no [Makefile](https://github.com/pug-se/pug-se.github.io/blob/develop/Makefile#L98). Ela irá automaticamente criar um commit com o conteúdo gerado na pasta `pug-se.github.io` e publicá-lo na branch `master`.

## Submetendo suas alterações

Finalmente, podemos submeter uma *pull request* da branch `develop` que alteramos. Para informações sobre como submeter uma pull request, acesse este [artigo detalhado do github](https://help.github.com/articles/creating-a-pull-request/).

Caso suas alterações tenham impacto no site gerado, opcionalmente você também pode submeter uma *pull request* da branch `master`. Caso você não submeta, não se preocupe, pois eventualmente a branch master do repositório de origem será atualizada com as alterações.
