---
title: "Editar conteúdo"
weight: "2"
---

## Visão geral
Num website com tema Amethyst, cada página designa-se também por **nota**.
Cada nota é controlada por um único ficheiro [Markdown](https://www.markdownguide.org/getting-started/). Para personalizar o seu website, pode adicionar, editar ou eliminar os ficheiros respetivos às notas que pretende.

> [!warning]- Não edite o código HTML
> 
> Amethyst opera através do sofware [Hugo](https://gohugo.io/), que remove a necessidade de saber desenvolver em HTML para criar websites de páginas estáticas.<br>
> Como tal, não é recomendado que edite estes ficheiros diretamente. OS ficheiros HTML são gerados pelo Hugo com base nos ficheiros Markwdown que escrever, pelo que alterações manuais no HTML podem ser perdidas.


<br>


## Visualizar o website

Antes de adicionar e editr conteúdo no seu website, é sensato executar o website para poder observar o seu estado inicial. Além disso, deixando o website aberto, pode ir verificando o resultado das suas alterações em tempo real. <br><br>
A forma de executar o website depende de se quiser [integrar Obsidian Vaults](./obsidian.md) no website ou não.

{{< tabs "preview" >}}
{{< tab "Amethyst Normal" >}} 
Se não necessita de integração com Obsidian Vaults, siga estes passos:
1. No seu computador, abra um terminal (como o CMD ou PowerShell)
2. Navegue até à pasta do seu website
3. Execute o seguinte comando:
```bash
# Indicar ao Hugo para criar um servidor para o website executar.
hugo server
```
1. Está agora a executar (_hosting_) o seu website localmente no seu computador. Pode ver aqui [o seu website em execução localmente](http://localhost:1313/), ou pode colar ```http://localhost:1313/``` no seu browser de internet.
{{< /tab >}}
{{< tab "Com Obsidian Vaults" >}} 
Se estiver a usar Obsidian Vaults, o processo é mais complexo, e involve instalar algumas dependências.

* Para garantir que utiliza a informação mais atualizada, recomendamos seguir as instruções oficiais da [documentação Amethyst](https://amethyst.bencuan.me/setup/preview-changes/) acerca de visualizar alterações no website.
{{< /tab >}}
{{< /tabs >}}


<br>


## Criar e editar notas

Agora que tem o website em execução, o passo seguinte será editar as suas notas.<br>
Como Markdown é apenas uma forma de criar texto formatado, pode utilizar o editor de texto ou de código que mais lhe agrade.

> [!note]- Não tem um editor? 
> 
>  Experimente [Visual Studio Code](https://code.visualstudio.com/), um editor leve que inclui também uma útil [extensão para escrever ficheiros Markdown](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one). 


### Estrutura de ficheiros e pastas

Todas as notas e imagens do seu website encontram-se na pasta ```/content```. <br> 
Aqui pode criar as subpastas que precisar para organizar o seu conteúdo, e o comainho de pastas que leve à sua nota será o que aparece no link dessa nota no browser.

Por exemplo, o link ```http://localhost:1313/setup/config/``` representa que o website está a apresentar a nota ```config.md``` localizada na pasta ```setup```, como representado nas imagens abaixo.


{{< columns >}} <!-- begin columns block -->
**Local da pasta ```/content```**
![Local da pasta /content](/images/content-folder.png)

<---> <!-- magic separator, between columns -->

**Caminho para obter ```config.md```**
![Caminho para obter config.md](/images/example-of-note.png)
{{< /columns >}}


### Definir a 'front matter'

A parte mais importante de uma nota em Amethyst (e em Hugo em geral) é a sua 'front matter' (cabeçalhos).
A 'front matter' é um conjunto de definições, separadas por```---```, que tem de definir no ínicio (topo) de cada nota, para que o Hugo considere o ficheiro uma página válida. No entanto, não tem de especificar todas as opeções disponíveis.
<br><br>
As definições mais úteis incluem o título e _tags_ da nota, se a nota deve aparecer na Tabela de Conteúdos (ToC) visível na area esquerda do website, e a _weight_ da página na ToC (a sua ordem em relação a outras notas).
```yaml
---
# Definir o título da nota
title: "Título Exemplo"

# Definir as tags da nota
tags:
- tag-exemplo

# Colocar 'true' para esconder a nota da Tabela de Conteúdos
bookHidden: false

# Definir a ordem desta nota em relação a outras na Tabela de Conteúdos (números maiores fazer a nota descer na lista)
weight: 2
---

Resto do conteúdo da página aqui...
```

> [!note]- Definições adicionais para a 'front matter'
>
> Estas são outras definições que também pode adicionar à secção de 'front matter', para configurar ainda mais a página de acordo com o necessite.
> ```yaml
> # Definir 'type' para 'docs' se quiser mostrar a página fora da secção configurada, ou se quiser mostrar outra secção sem ser 'docs'
> type: 'docs'
> 
> # (Opcional) Colocar 'true' para definir a página como uma secção plana no menu de árvore de ficheiros (se BookMenuBundle não estiver definido)
> bookFlatSection: false
> 
> # (Optional) Colocar 'true' para esconder secções _nested_ ou páginas a esse nível. Só funciona com o modo árvore de ficheiros ativado.
> bookCollapseSection: true
> 
> # (Optional) Colocar 'false' para esconder a ToC dessa página
> bookToC: true
> 
> # (Optional) Se BookComments estiver ativado, esta definição permite desativar para uma página em específico.
> bookComments: true
> 
> # (Optional) Colocar 'false' para excluir esta página do indíce de pesquisa.
> bookSearchExclude: true
> 
> # (Optional) Definir explícitamente o atributo 'href' para esta página num menu (se BookMenuBundle não estive definido)
> bookHref: ''
>
> ```


### Escrever o conteúdo

Com as definições da nota definidas, pode agora começar a escrever o conteúdo que necessite.<br><br>

Como as notas Amethyst são escritas em ficheiros Markdown, pode utilizar todas as [funcionalidades e sintaxe Markdown](https://www.markdownguide.org/cheat-sheet/), tal como listas, tabelas, e links para melhor organizar o conteúdo que escrever.<br><br>

Além disso, há também várias [funcionalidades exclusivas do Amethyst](https://amethyst.bencuan.me/features/buttons/), como butões, colunas, _tabs_ (tabulação), e _callouts_ (zonas destacadas) que pode explorar para customizar ainda masi a sua página.


<br>


## Próximos passos

Agora que já sabe como editar notas e visualizar o seu website, aqui estão alguns próximos passos que poderá seguir:

* [Aprender a customizar ainda mais o Amethyst](tecaa/customization.md), para melhorar a experiencia de utilização do seu website.

* [Aprender como publicar o website (_deploy_) na Web](tecaa/deployingwebsite.md), para começar a receber visitantes.



<br>
<br>
<br>
<br>




{{< expand "Como esta página foi desenvolvida">}}
#### Autor da página
Esta página foi criada por Rafael Martins (Nº 1180887), estudante do Mestrado de Engenharia Informática no ISEP, Porto, Portugal.
Este website é um projeto criado para a unidade curricular de TECAA.

#### Processo de desenvolvimento
Esta página ensina a editar e visualizar o conteúdo de um website Amethyst Hugo. Para tal, o conteúdo desta página foi escrito reorganizando e sumariando as páginas de [Editing Content](https://amethyst.bencuan.me/setup/editing/) e [Preview Changes](https://amethyst.bencuan.me/setup/preview-changes/) da documentação oficial do Amethyst.

Esta página foi desenvolvida seguido as instruções que ensina, ou seja:
1. Criou-se um novo ficheiro Markdown ```editingcontent.md``` dentro da pasta ```/content/tecaa/```.
2. Definiu-se as definições de 'front matter' (cabeçalhos): o título da página e a sua _weight_ (ordem) em relação às outras páginas da mesma pasta.
3. Adicionou-se o conteúdo necessário.
4. Organizou-se a página utilizando várias funcionalidades do Markdown e Amethyst, tendo atenção para que a página siga as [decisões de grupo definidas]().

Abaixo apresenta-se um resumo das decisões individuais efetuadas no desenvolvimento desta página, no que toca a cada funcionalidade.

{{< tabs "feature-summary" >}}
{{< tab "Texto, títulos e links" >}} 

#### Texto

_Não foram efetuadas decisões individuais._<br>
Seguindo as decisões de grupo: 

* Nenhuma alteração de estilo ou fonte foi feita ao texto, para que a página siga o tema base Amethyst.
* O conteúdo foi escrito tendo em conta as [Google Developer Documentation Style Guidelines' Highlights](https://developers.google.com/style/highlights). 

#### Títulos / Cabeçalhos

_Não foram efetuadas decisões individuais._<br>
Atenção especial foi dada para garantir que:

* Os níveis dos títulos sigam uma ordem hierárquica correta, como ditam as [WCAG accessibility guidelines](https://www.w3.org/TR/WCAG21/)
* O nome dos títulos estejam escritos com o estilo de capitalização 'Sentence Case', como ditam as [Google Developer Documentation Style Guidelines' Highlights](https://developers.google.com/style/highlights)

#### Links

**Decisão individual:** Não usar a funcionalidade de botões do Amethyst para links.<br>

* **Justificação:** Estes butões foram concebidos para serem uma forma mais apelativa de apresentar links aos utilizadores, No entanto, butões também podem ser utilizados para ativar várias ações em websites dinâmicos, em vez de servirem de links para outras páginas. Estas duas utilizações distintas de butões poderiam criar confusão no leitor, pelo que foi decidido que links para conteúdo e páginas relacionadas seriam apresentados apenas através do estilo simples de links Markdown.

Decisões de grupo relacionadas com links foram seguidas.

{{< /tab >}}
{{< tab "Zonas Destacadas" >}} 

#### Zonas destacadas (Callouts)

**Decisão individual:**  Zonas destacadas colapsáveis foram usadas para fornecer ao leitor avisos e recomendações adicionais quando necessário, uma vez que os seus estilos coloridos são uma forma eficaz de chamar a atenção dos utilizadores. Nesta página, todos as três zonas destacadas começam fechadas:

* A zona de aviso começa fechada para que o enfase seja no tiítulo do aviso. Se o utilizador pretender obter detalhes sobre o aviso, poderá então abrir a zona destacada.
* As duas zonas destacadas com conteúdo adicional começam fechadas por serem apenas informações opcionais. Estando fechadas, não impactam negativamente a organização da página, e o utilizador pode abrir e ler o conteúdo adicional apenas se estiver interessado.

{{< /tab >}}
{{< tab "Colunas" >}} 

#### Colunas
**Decisão individual:** A funcionalidade de colunas foi usada nesta página para apresentar ao utilizador duas imagens lado a lado.

* **Justificação:** As descrições de caminhos na secção **Estrutura de ficheiros e pastas** podem ser difíceis de entender para um utilizador menos experiente. Para mitigar este problema, o objetivo seria apresentar ao leitor duas imagens que, juntas, mostram a estrutura de um típico projeto Amethyst Hugo. Como tal, a funcionalidade de organizar o conteúdo em clunas permite ao utilizador visualizar ambas as imagens lado a lado e compará-las, pelo que foi considerada uma solução ideal.

{{< /tab >}}
{{< tab "Tabs" >}} 

#### Tabs

**Decisão individual:** A funcionalidade de _tabs_ foi usada para apresentar ao utilizador duas alternativas de conjuntos de passos a seguir para visualizar o seu website, dependendo da sua decisção de integrar o Amethyst com o Obsidian Vaults ou não.

* **Justificação:** Este é um caso típico de uso de _tabs_, uma vez que transmite ao utilizador que apenas têm de escolher e seguir um dos conjuntos de instruções, não ambos.
{{< /tab >}}

{{< tab "Área Expandível" >}} 

#### Área expandível

_Não foram efetuadas decisões individuais._<br>
Como definido nas decisões de grupo, a funcionalidade de área expandível foi usada para organizar esta própria secção de "Como esta página foi desenvolvida". A funcionalidade de área expandível cria uma área de texto colapsável, perfeita para esconder estes detalhes de implementação que não fazem parte do conteúdo principal da página.
{{< /tab >}}
{{< /tabs >}}

{{< /expand >}}