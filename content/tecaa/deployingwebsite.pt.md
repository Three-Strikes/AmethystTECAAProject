---
title: Dar host ao Ametista na Internet
weight: '"4"'
---
## Implementar?

Implementar um site significa torná-lo disponível para o mundo, utilizando a Internet. Isto significa que qualquer pessoa que conheça o endereço do site (ou URL) pode ver as notas publicadas no website, **e isto inclui o seu conteúdo**.

È uma prática útil se pretender compartilhar os conteúdos escritos com os teus amigos ou colegas. Este tema foi projetado para ser facilmente implementado, principalmente nas páginas do GitHub.

Alternativamente, podes implementar as tuas notas em um **domínio personalizado**, se tiveres um disponível. Isto significa que, em vez de teres a URL do teu site fornecida pelo GitHub:

```<NOME-DE-UTILIZADOR-DO-GITHUB>.github.io```

Terás um domínio personalizado, com uma estrutura e nome diferentes, que podes partilhar facilmente.

## Implementar nas páginas do GitHub

Se seguiste os passos na página de [Configuração](tecaa/setup.pt.md), estás pronto para implementar o teu site nas páginas do GitHub.

### Preparando a implementação

Existem algumas etapas que precisas de seguir para permitir que teu repositório seja publicado como um site. Segue os passos abaixo para concluíres a configuração do teu repositório.

Primeiro, vai ao repositório que usaste para fazer o fork do tema Amethyst.
Depois, clica na aba "Ações" do repositório, para poderes configurar as ações do repositório.

![A aba de ações, localizada no teu repositório do GitHub, está no canto superior esquerdo, sendo a quarta opção da esquerda para a direita.](/images/github-repo.png)
*A aba de ações, localizada no teu repositório do GitHub*

Após entrares na aba Ações, uma página aparecerá a avisar que, devido ao teres dado fork ao repositório, as ações do GitHub estão desativadas. Clica no botão que diz:

```Entendo os meus fluxos de trabalho, vá em frente e ative-os.```

![Dentro da aba de ações, há um botão verde em qual deves clicar para que o teu site seja implementado quando fizeres alterações.](/images/github-actions.png)
*Dentro da página de ações do GitHub, após fazer um fork de um repositório*

Isto ativará as ações do GitHub para o teu repositório, que implantará automaticamente o teu site sempre que enviares alterações para este repositório, mantendo-o atualizado automaticamente!
### Ativando as páginas do GitHub

Depois de ativares as ações do GitHub, podes ir para a aba Configurações do teu repositório. Na aba de configurações, há outra aba chamada "Páginas". Clica na aba para continuar.

![Na aba de páginas, podes encontrar configurações como definir a origem dos teus arquivos e usar um domínio personalizado.](/images/github-pages.png)
*A aba Páginas do GitHub*

Nesta aba, deves alterar o diretório de implantação do projeto para o branch "master" do teu repositório e selecionar a pasta raiz.

#### (Opcional) Configurar um domínio personalizado

Neste ecrã, podes também configurar um domínio personalizado ao escrever o URL na caixa de texto e ao clicar no botão Salvar.

Para que o site seja hospedado no domínio, precisas de seguir uma etapa adicional.

Dirige-te ao teu provedor de DNS e cria um registro CNAME que aponte o teu domínio para `<NOME-DE-UTILIZADOR-DO-GITHUB.github.io.`
O ponto final **é necessário**!

>[!info] Pode demorar um pouco.
>
>As alterações de rede podem levar de 30 minutos a uma hora para serem concluídas. Após esse período, o teu domínio está pronto para hospedar o site.

Com todas as preparações feitas, estás pronto para enviar conteúdo que será exibido na internet.

### Enviar alterações

Precisas de enviar as alterações que fizeres para que elas sejam vistas na internet. Atualizar o repositório é feito da mesma forma que qualquer outro repositório:

```shell
# Navegue até a pasta Amethyst
cd <caminho-para-amethyst>

# Confirme todas as alterações
git add .
git commit -m "mensagem descrevendo as alterações"

# Envie para o GitHub para atualizar o site
git push origin main

```

Estes comandos enviam para o branch principal. Isso é intencional, pois as ações do GitHub que preparamos anteriormente replicam o mesmo commit no branch de implantação.

### Configurar o site

Neste capítulo, colocamos o site em funcionamento!

### Alterar o arquivo de configuração do Hugo

A primeira coisa que  precisas de fazer é abrir o ficheiro *config.yaml* que se encontra na raiz do repositório com o teu editor de texto favorito e localizar a propriedade baseURL. Altera esta propriedade para o domínio que vais usar para hospedar o teu site.

>[!warning] Cuidado!
>
>Precisas de colocar uma **barra inclinada final "/"** para que o site funcione após a implementação e substituir os domínios conforme necessário!


Podes encontrar um exemplo do ficheiro no [repositório](https://github.com/64bitpandas/amethyst/blob/main/config.yaml) do tema.
{{< columns >}} 
#### Páginas do GitHub

Se estiveres a usar o domínio nas páginas do GitHub, podes usar o seguinte exemplo.

```yaml
baseURL: "https://<NOME-DE-UTILIZADOR-DO-GITHUB>.github.io/amethyst/"
```
<---> 
#### Domínio Personalizado

Se estiveres a usar um domínio personalizado, deves usar a seguinte estrutura:


```yaml
baseURL: "https://<O-TEU-DOMÍNIO>/"
```

{{< /columns >}}


### Alterar o arquivo de implantação das ações do GitHub


O último passo envolve dizer às ações do GitHub como construir e executar o teu site ao usar o ficheiro *deploy.yaml*, localizado em `/.github/workflows/` no teu repositório. Neste fichieiro, precisas de alterar a propriedade *"cname"* para o domínio da tua página.

>[!warning] Tenha cuidado!
>
>Aqui não precisas da **barra inclinada final (/)**!

Podes encontrar um exemplo do ficheiro no [repositório](https://github.com/64bitpandas/amethyst/blob/main/.github/workflows/deploy.yaml) do tema.

```yaml
- name: Implementar  
  uses: peaceiris/actions-gh-pages@v3  
  with:  
	github_token: ${{ secrets.GITHUB_TOKEN }} # isto pode ficar como está, o GitHub preenche isto por nós!
	publish_dir: ./public  
	publish_branch: deploy
	cname: <O-TEU-DOMÍNIO>

```

## Como foi construída esta página?

{{< expand >}}

Esta página foi adaptada da página já existente "implementando amethyst na web" que está presente no [tutorial do tema](https://amethyst.bencuan.me/setup/hosting/). Esta página tentou tornar o conteúdo mais fácil de entender, seguindo as [diretrizes de estilo do Google para documentação técnica](https://developers.google.com/style/highlights) o mais próximo possível. Foi dada atenção especial aos destaques presentes no guia de estilo, para tornar a experiência de leitura fluida e agradável.

### Autor

Esta página foi criada por Rafael Cardoso (Nº 1190982), um estudante de Mestrado em Engenharia Informática no ISEP, Porto, Portugal.
Este website foi um projeto criado para a unidade curricular TECAA.

O processo de desenvolvimento seguiu os seguintes passos:

1. Criado um novo ficheiro de markdown de nome `deployingwebsite.md` no diretório `/content/tecaa/`.
2. Configuração das propriedades da página, como o peso no explorador de páginas e do nome que aparece.
3. Foi adicionado o conteúdo necessário, e foi organizada a página usando várias funcionalidades do Markdown e do Amethyst, assegurando que as linhas definidas pelo grupo foram cumpridas.

### Funcionalidades do Amethyst

O tema Amethyst apresenta [opções exclusivas](https://amethyst.bencuan.me/features/buttons/) de renderização de markdown que nem mesmo o programa Obsidian possui. As seguintes seções destacam as funcionalidades usadas nesta página.

{{< tabs "Funcionalidades do Amethyst" >}}
{{< tab "Expandir" >}} 

A funcionalidade Expandir foi usada para escrever esta própria seção sobre como a página foi escrita.

Expandir cria uma área expansível de texto, perfeita para esconder detalhes opcionais que não fazem parte do conteúdo principal da página.

{{< /tab >}}
{{< tab "Guias" >}} 

A funcionalidade de Guias foi usada nesta seção para resumir de forma mais sucinta os estilos de markdown usados na página.

Isto evita a necessidade de o leitor ter de deslocar a página e ler conteúdo entre os cabeçalhos.

{{< /tab >}}
{{< tab "Colunas" >}} 

A funcionalidade de colunas foi usada na seção em que o leitor precisa de escolher um domínio personalizado ou o domínio das páginas do GitHub enquanto edita o ficheiro do tema.

A funcionalidade organiza o conteúdo de forma a que o leitor possa identificar facilmente o seu caso de uso.

{{< /tab >}}
{{< /tabs >}}
### Markdown do Obsidian

O markdown usado na construção da página foi adaptado para ser renderizado corretamente no website. O site usa principalmente [Markdown do Obsidian](https://help.obsidian.md/Editing+and+formatting/Obsidian+Flavored+Markdown), porque foi feito com o software Obsidian em mente, que permite aos utilizadores construir uma rede de notas e criar uma base de conhecimento.

Portanto, este markdown pode não seguir a mesma sintaxe que outros tipos de markdown, podendo falhar ao ser interpretado noutros sites.

{{< tabs "Markdown Flavored do Obsidian" >}}
{{< tab "Cabeçalhos" >}} 

Os cabeçalhos foram criados apenas para dividir as informações em blocos fáceis de ler, para que o leitor possa inferir em que etapa está no tutorial que a página está a tentar apresentar.

Os cabeçalhos presentes no original foram adaptados como seções aqui.

Algumas seções foram adicionadas, em vez de serem escondidas em páginas menores com pouco conteúdo, como a seção "Configurando um domínio personalizado", que estava escondida numa página pequena.

Como tem a ver com a implementação, foi movida para aqui para aqueles que precisam.

{{< /tab >}}
{{< tab "Conteúdo" >}} 

O conteúdo em cada seção tenta ser o mais informativo possível, ao mesmo tempo que fornece contexto ao leitor do que está a acontecer.

Por exemplo, o leitor pode não estar familiarizado com "implementar" um site, e então, é explicado muito claramente o que hospedar um site significa e que é isso que este tutorial irá ensiná-lo a fazer.

Contexto é dado para tudo, dentro do razoável.

{{< /tab >}}
{{< tab "Links" >}} 

De acordo com o guia de estilo, os links são intercalados no conteúdo de forma que alguém possa remover o link, e a frase ainda faria sentido.

Isto ajuda na legibilidade, e cabe ao leitor clicar no link se precisar das informações que o link está tentando fornecer.

{{< /tab >}}
{{< tab "Imagens" >}} 

As imagens fornecem uma maneira para o leitor ver o que deve fazer no tutorial. Juntamente com estas imagens, que incluem legendas, bem como **texto alternativo** que descreve o conteúdo da imagem.

Este texto alternativo é usado para que a imagem possa ser descrita a um leitor cego por leitores de ecrã.

{{< /tab >}}
{{< tab "Destaque" >}} 

Os destaques foram usados para chamar a atenção do leitor em momentos críticos e são usados para chamar a atenção sem interromper o fluxo de texto.

O seu conteúdo resume-se a avisos e informações sobre coisas às quais o leitor realmente deve prestar atenção.

{{< /tab >}}
{{< /tabs >}}

{{< /expand >}}