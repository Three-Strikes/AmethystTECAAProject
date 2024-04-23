---

title: "Personalização"
weight: "3"
---

## Personalize o seu website amethyst
O Amethyst oferece amplas opções de personalização para adaptar o seu website de acordo com as suas preferências. Você pode configurar vários aspectos do seu website para alcançar a aparência e funcionalidade desejadas. O objetivo desta página é permitir-lhe personalizar ainda mais o Amethyst e melhorar a experiência do seu website sem esforço.

## Configuração

**Personalize cada detalhe**: Com o Amethyst, é possível personalizar o seu website de forma simplificada. Desta forma, consegue ter um controlo total sobre o aspeto e o comportamento do seu website.

**Ficheiro de configuração**: A maioria das opções de personalização está convenientemente localizada dentro do ficheiro ```config.yaml```. Não se preocupe, navegar neste ficheiro é mais simples do que pode parecer inicialmente. Precisa de orientação? Consulte um exemplo com explicações detalhadas [aqui](https://github.com/64bitpandas/amethyst/blob/main/config.yaml).

### Adicionar títulos de bloco de código

Melhore a organização dos seus blocos de código atribuindo-lhes títulos. Essa prática funciona de forma semelhante ao fornecimento de etiquetas, aprimorando a clareza e a estrutura do seu conteúdo.

{{< tabs "Passos" >}}
{{< tab "Passo 1" >}}
1. **Ative os títulos**: Garanta que os títulos dos seus blocos de código estejam habilitados na configuração, definindo o parâmetro `enableCodeBlockTitle` como `true` no seu ficheiro `config.yaml`:

    ```yaml {title="data/config.yaml"}
    enableCodeBlockTitle: true
    ```
{{< /tab >}}
{{< tab "Passo 2" >}}
2. **Dê título aos seus blocos**: Adicione o atributo `title` a qualquer bloco de código ao qual deseja atribuir um título:

    ```markdown
       ```yaml {title="data/config.yaml"}
       enableCodeBlockTitle: true  # exemplo do passo 1
       ```
{{< /tab >}}
{{< /tabs >}}

> [!warning]- Siga estes passos com cuidado
>
> Certifique-se de seguir os passos fornecidos cuidadosamente para evitar quaisquer problemas potenciais e aproveitar totalmente os benefícios de adicionar títulos de blocos de código. Se **```{title=<my-title>}```** estiver incluído no seu bloco de código e os títulos de bloco de código não estiverem **habilitados**, nenhum erro ocorrerá e o atributo de título será ignorado.

### Personalize favicons HTML

Aumente o apelo visual do seu website personalizando os favicons. Veja como pode personalizá-los:

> [!info]- Definição de favicons
>
> Os Favicons, abreviatura de "ícones de favoritos", são pequenos ícones associados a um website que aparecem em vários locais, tais como separadores do browser, barras de favoritos e quando o website é guardado no ecrã inicial em dispositivos móveis. Servem como identificadores visuais para websites e melhoram a experiência do utilizador.

{{< tabs >}}
{{< tab "Configuração do Favicon" >}}

Para personalizar os favicons do seu website, pode modificá-los editando o ficheiro `data/config.yaml`. A configuração padrão do favicon, na ausência de qualquer chave de favicon especificada, é a seguinte:

```html {title="layouts/partials/head.html"}
<link rel="shortcut icon" href="icon.png" type="image/png">
```

No entanto, pode personalizar o favicon adicionando ou modificando a chave de favicon no seu ficheiro `data/config.yaml`. Aqui está um exemplo de formato YAML, usando uma `Lista[Dict]`, que espelha a configuração padrão:

```yaml {title="data/config.yaml"}
favicon:
      - { rel: "shortcut icon", href: "icon.png", type: "image/png" }
      #  - { ... } # Repita para cada favicon adicional que deseja adicionar
```
- O atributo `href` especifica o caminho para o ficheiro de imagem do favicon.
- Pode definir favicons adicionais usando o mesmo formato para cada um.

{{< /tab >}}

{{< tab "Múltiplos Favicons" >}}

Se desejar adicionar um ícone de toque da Apple, que aparece quando os utilizadores adicionam seu website à tela inicial dos seus dispositivos Apple, você pode anexá-lo à configuração de favicon existente em `data/config.yaml`. Aqui está um exemplo:

```yaml {title="data/config.yaml"}
favicon: |
  <link rel="shortcut icon" href="icon.png" type="image/png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
```
Neste exemplo, a primeira tag <link> especifica o favicon padrão para todos os dispositivos, enquanto a segunda tag <link> define especificamente o ícone de toque da Apple. O atributo ````rel="apple-touch-icon"``` indica que este link é destinado a dispositivos Apple, e o atributo ```sizes="180x180"``` especifica as dimensões do ícone.

{{< /tab >}}

{{< tab "Informações Adicionais" >}}

Tipos de ficheiros de favicon: Os ficheiros de favicon podem ter diferentes tipos, cada um correspondendo a um formato de imagem específico. Tipos comuns incluem:
- `image/x-icon`: Para ícones no formato ICO.
- `image/png`: Para ícones no formato PNG.
- `image/gif`: Para ícones no formato GIF.
- `image/jpeg` ou `image/jpg`: Para ícones no formato JPEG.
- `image/svg+xml`: Para ícones no formato SVG.

Estes são apenas alguns exemplos, e o tipo apropriado depende do formato do ficheiro de favicon que está a usar e dos requisitos de compatibilidade do seu website.

Se estiver interessado em mais informações sobre os padrões atuais e anteriores de favicons, você pode ler [este artigo](https://www.emergeinteractive.com/insights/detail/the-essentials-of-favicons/).

{{< /tab >}}

{{< /tabs >}}

> [!note] Nota importante
>
> Certifique-se de colocar os seus ficheiros de favicon no diretório correto e atualizar os caminhos de acordo no seu ficheiro de configuração para garantir a exibição adequada em todos os dispositivos e plataformas.

### Visualização do gráfico
Para personalizar a visualização de Gráfico Interativo de acordo com as suas preferências, navegue até ao ficheiro `data/graphConfig.yaml`. A configuração padrão, juntamente com descrições, está disponível [aqui](https://github.com/64bitpandas/amethyst/blob/main/data/graphConfig.yaml).

### Suporte de idiomas

O Amethyst oferece suporte integrado para idiomas como Chinês, Japonês e Coreano. Isso significa que pode começar a usar esses idiomas imediatamente, sem a necessidade de configurações adicionais. No entanto, se desejar adicionar suporte para idiomas que são lidos da direita para a esquerda, como Árabe, o Hugo (e consequentemente, Amethyst) fornece suporte nativo para isso.

Para habilitar o suporte para idiomas da direita para a esquerda (RTL), siga as instruções fornecidas pelo Hugo [aqui](https://gohugo.io/content-management/multilingual/#configure-languages) e modifique o seu ficheiro config.yaml conforme necessário.

Por exemplo, para configurar o idioma Árabe, você pode adicionar o seguinte código ao seu ficheiro config.yaml:

```yaml
defaultContentLanguage: ar
languages:
  ar:
    languagedirection: rtl
    title: مدونتي
    weight: 2
```
Esta configuração define o idioma padrão como Árabe (ar), especifica que o texto será lido da direita para a esquerda (languagedirection: rtl) e define o título do website em Árabe (title: مدونتي). O weight é usado para classificar os idiomas no menu de seleção de idiomas se tiver vários idiomas configurados.

## Estilos personalizados
Se deseja ter mais personalização, explore o estilo CSS em `assets/_custom.scss`. Para segmentar seções específicas do seu website, considere adicionar IDs e classes aos parciais HTML em `/layouts/partials`.

### Alterar o esquema de cores
Modifique os esquemas de cores padrão tanto para o modo claro quanto para o modo escuro ao aceder ao ficheiro `assets/_colors.scss`. Para além disso, tem a opção de substituir diretamente os valores das variáveis de cor existentes para facilitar edições contínuas ou criar novas variáveis para referenciar em `_custom.scss`.

Aqui está um exemplo de ajustes de esquema de cores no ficheiro `_colors.scss` à esquerda e o resultado correspondente à direita.
![Esquema de Cores de Exemplo](/images/example-color-scheme.png)

### Alterar as fontes
As configurações de fonte estão localizadas em `assets/_fonts.scss`. Nesse ficheiro encontrará exemplos tanto para fontes locais (especificadas usando `@font-face`) quanto para fontes da web (importadas com `@import` de distribuidores de fontes como o Google Fonts).
Para fontes locais, armazene-as no diretório `static/fonts`.

Defina fontes locais personalizadas usando `@font-face` em `assets/_fonts.scss`. Essas fontes são armazenadas localmente e são ideais para personalizar a tipografia do seu website.

Por exemplo:

```scss
@font-face {
  font-family: "PP Mori";
  font-style: normal;
  font-weight: normal;
  src: url('fonts/PPMori-SemiBold.woff2');
}
```

Importe fontes da web de fontes externas como o Google Fonts usando `@import` em `assets/_fonts.scss`. Essas fontes são obtidas dinamicamente na web e oferecem uma ampla gama de opções para personalização tipográfica.

Por exemplo:
```scss
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&family=IBM+Plex+Sans:wght@400;600&display=swap');
```

### Parciais
Os parciais definem a renderização de componentes específicos na sua página web. Pode modificar os layouts relevantes no diretório `/layouts`.
Por exemplo, para ajustar o layout da página inicial, navegue até `/layouts/index.html`. Para personalizar o rodapé, edite `/layouts/partials/footer.html`.

Para mais informações sobre parciais, visite o [website do Hugo](https://gohugo.io/templates/partials/).

Se encontrar dificuldades, explore o [FAQ e guia de resolução de problemas](setup/troubleshooting.md) para assistência.

## Pesquisa
O Amethyst oferece dois modos de pesquisa: Linguagem natural e Texto completo.

{{< columns >}}

### Pesquisa por linguagem natural
Com base no Operand, a pesquisa por linguagem natural compreende a linguagem como uma pessoa, apresentando resultados que correspondem melhor à intenção do utilizador. Oferece resultados de qualidade superior em comparação com a pesquisa de texto completo e funciona de forma semelhante à pesquisa do Google. Para configurar a pesquisa por linguagem natural:

Início de sessão ou registo: Crie uma conta Operand e verifique-a por e-mail.
> [!note] Observação
>
> Não é necessário cartão de crédito, e os primeiros $10 de utilização mensal são gratuitos.

Crie um índice: Defina o seu índice no painel Operand, anotando o ID de índice único.

Indexe o seu website: Adicione o URL do sitemap do seu website à configuração do índice.

Obtenha a chave da API: Faça a gestão das suas chaves de API no painel Operand ou crie uma nova, se necessário.

Atualize a configuração: Defina enableSemanticSearch como true em config.yaml, junto com os valores operandApiKey e operandIndexId.

```yaml {title="config.yaml"}
# a opção padrão
search:
  enableSemanticSearch: true
  operandApiKey: "jp9k5hudse2a828z98kxd6z3payi8u90rnjf"
  operandIndexId: "s0kf3bd6tldw"
```
Implementar as alterações: Envie as suas alterações de configuração e aguarde o website ser implementado.

<--->

### Pesquisa de texto completo
O modo de pesquisa padrão no Amethyst, pesquisa de texto completo, fornece resultados que correspondem precisamente à consulta de pesquisa. Este modo é fácil de configurar, mas pode fornecer correspondências de qualidade inferior.

```yaml {title="config.yaml"}
# Opção padrão
enableSemanticSearch: false
```

{{< /columns >}}

## Próximos Passos

Agora que já sabe como personalizar o seu website e configurar a funcionalidade de pesquisa, aqui estão alguns próximos passos que poderá seguir:

* [Aprender como publicar o website (_deploy_) na Web](tecaa/deployingwebsite.md), para começar a receber visitantes.

<br>
<br>
<br>
<br>

{{< expand "Como esta página foi desenvolvida">}}
## Autor da página
Esta página foi escrita por Márcia Carvalho (Nº 1190844), aluna do Mestrado em Engenharia Informática no ISEP, Porto, Portugal.
Este website foi desenvolvido como parte da unidade curricular TECAA.

## Processo de desenvolvimento
Esta página fornece orientações sobre como personalizar e configurar a funcionalidade de pesquisa no tema Hugo Amethyst. O conteúdo foi reorganizado e resumido a partir da documentação oficial do Amethyst sobre as páginas de [Personalização](https://amethyst.bencuan.me/setup/config/) e [Pesquisa](https://amethyst.bencuan.me/setup/search/).

O processo de desenvolvimento seguiu os seguintes passos:

1. Criação de um novo arquivo Markdown chamado ```customization.md``` dentro do diretório  ```/content/tecaa/```.
2. Configuração das definições do front matter, incluindo o título da página e o seu peso relativo (ordem) em relação às outras páginas dentro da mesma pasta.
3. Adicionou-se o conteúdo necessário e organizou-se a página utilizando vários recursos do Markdown e do Amethyst, de forma a garantir conformidade com as [decisões do grupo definidas]().

Abaixo está um resumo das decisões específicas tomadas na criação desta página, detalhando a utilização de vários recursos e elementos.

{{< tabs "feature-summary" >}}

{{< tab "Títulos" >}} 
### Títulos

Os títulos foram utilizados principalmente para organizar o conteúdo em seções facilmente compreensíveis, ajudando os utilizadores a navegar no tutorial. Cada título serve para distinguir diferentes etapas ou seções dentro do tutorial, fornecendo aos utilizadores uma sensação clara da progressão e o contexto.

_Não foram efetuadas decisões individuais._<br>

**Decisão do grupo:**
* Os níveis dos títulos seguem uma hierarquia correta de acordo com as [diretrizes de acessibilidade WCAG](https://www.w3.org/TR/WCAG21/). 
* Os nomes dos títulos são escritos em Maiúscula na primeira letra, alinhando-se com os [destaques das Diretrizes de Estilo de Documentação para Desenvolvedores do Google](https://developers.google.com/style/highlights).

{{< /tab >}}

{{< tab "Conteúdo" >}} 
### Conteúdo

**Decisão individual:** Na seção de conteúdo, o objetivo era fornecer explicações claras e concisas ao utilizador. 

* Foram incluídas definições contextuais para conceitos com os quais os leitores podem não estar familiarizados, como "favicons".

* Na seção "Personalizar favicons HTML", um guia adicional foi adicionado para fornecer informações sobre diferentes formatos de imagem para favicons. Isso foi feito para ajudar os utilizadores nos diversos tipos disponíveis e como poderiam utilizá-los efetivamente. Portanto, foi colocada numa seção adicional.

* Também foi descoberto que para a configuração do favicon, é possível editar diretamente o arquivo `html-head.html` modificando a linha `<link rel="icon" href="{{ "favicon.png" | relURL }}" type="image/x-icon">`. Embora este método também seja simples de modificar, não foi incluído no texto para evitar certas confusões para os utilizadores, já que modificar o arquivo config.yaml é uma abordagem mais simples e cobre a maioria das configurações.

**Decisão do grupo:**
* Não foi feita nenhuma mudança no estilo ou fonte de texto para garantir consistência com o tema base do Amethyst.
* O conteúdo foi escrito de acordo com os destaques das [Diretrizes de Estilo de Documentação para Desenvolvedores do Google](https://developers.google.com/style/highlights), incluindo o uso da segunda pessoa, voz ativa, etc.

{{< /tab >}}

{{< tab "Links" >}} 
### Links

**Decisão individual:** O utilização de links ao longo do tutorial tem um objetivo simples mas essencial: redirecionar os utilizadores para destinos externos ou internos. Quer se trate de navegar para recursos adicionais, explorar documentação relacionada ou aceder a websites externos.

{{< /tab >}}
{{< tab "Zonas Destacadas" >}} 

### Zonas destacadas (Callouts)

**Decisão individual:** Na elaboração desta página, foram utilizadas estrategicamente várias zonas para aumentar a compreensão e o envolvimento do utilizador. Cada zona tem um propósito distinto, cuidadosamente adaptado para orientar e informar o leitor.

**Zona de aviso:** Utilizado na secção relativa a títulos de blocos de código para realçar a importância de seguir os passos diligentemente. Serve para lembrar que, se os títulos de blocos de código não estiverem ativados, não aparecerão erros, mas a atribuição será ignorada. Esta zona de aviso começa fechado para chamar a atenção para o título de aviso inicialmente. Os utilizadores podem abri-lo mais tarde se pretenderem compreender o aviso em pormenor.

**Zona de informação:** Usado para explicar a definição de favicons. Foi definido como fechado, uma vez que é opcional para os utilizadores verem, evitando confusão desnecessária se já estiverem familiarizados com a definição.

**Zona de nota:** Implementada como chamadas abertas para notas adicionais no conteúdo. Permaneceram abertas para garantir uma fácil acessibilidade e compreensão, uma vez que continham informações suplementares importantes.

{{< /tab >}}

{{< tab "Colunas" >}} 

### Colunas
**Decisão individual:** Foram implementadas colunas na secção "Pesquisa" para ilustrar os dois modos diferentes de utilização da funcionalidade de pesquisa: Linguagem natural e texto completo. A decisão de utilizar colunas resultou da necessidade de apresentar aos utilizadores uma comparação visual clara entre os dois modos de pesquisa. Ao apresentá-los lado a lado, os utilizadores podem facilmente perceber as diferenças e escolher o modo que melhor se adapta às suas necessidades.

{{< /tab >}}

{{< tab "Tabs" >}} 

### Tabs

**Decisão individual:** Os separadores foram estrategicamente incorporados na página para melhorar a experiência do utilizador e simplificar a apresentação das informações. Cada separador tem uma finalidade específica, permitindo aos utilizadores navegarem pelo conteúdo sem problemas.

* Separadores de passos:** Utilizados na secção "Adicionar títulos de blocos de código" para dividir o processo em dois passos distintos, facilitando a compreensão e a progressão do utilizador. Os utilizadores podem seguir cada passo sequencialmente, garantindo clareza e facilidade de implementação.
* Separadores de informações:** Implementados na secção "Personalizar favicons HTML" para fornecer visualizações de informações alternativas. Os utilizadores podem optar por ver detalhes sobre a adição de um favicon, aprender a utilizar vários favicons ou aceder a informações adicionais de acordo com os seus requisitos. Esta abordagem oferece flexibilidade e personalização, satisfazendo as diversas necessidades dos utilizadores, e também foi utilizada nesta mesma secção "Como a página foi criada" para o mesmo fim.

{{< /tab >}}

{{< tab "Área Expandível" >}} 

### Área expandível

Área expandível cria uma área de texto dobrável, perfeita para ocultar estes detalhes opcionais que não fazem parte do conteúdo da página principal.

_Não foram efetuadas decisões individuais._<br>
**Decisão de grupo:** A função de área expandível  foi usada para escrever esta secção sobre "Como a página foi feita".
{{< /tab >}}

{{< tab "Imagens" >}} 
### Imagens

**Decisão individual:** Foi utilizada uma imagem na secção "Alterar o esquema de cores" para fornecer um exemplo prático de como as alterações de cor são aplicadas no tema. Cada imagem é acompanhada por uma legenda, que oferece informações contextuais sobre o ajuste do esquema de cores representado. Além disso, foi incorporado texto alternativo para descrever o conteúdo de cada imagem.

{{< /tab >}}

{{< /tabs >}}

{{< /expand >}}

