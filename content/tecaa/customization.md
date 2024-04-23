---
title: "Customization"
weight: "3"
---

## Personalize your amethyst site
Amethyst offers extensive customization options to tailor your website according to your preferences. You can configure various aspects of your site to achieve the desired look and functionality.
The purpose of this page is to enable you to further customize Amethyst and enhance your website's experience effortlessly.

## Configuration

**Customize every detail**: With Amethyst, it's possible to customize your website in a simplified manner. You have full control over how your site looks and behaves.

**Configuration file**:The majority of customization options are conveniently located within the ```config.yaml``` file. Rest assured, navigating this file is simpler than it may initially seem. Need guidance? Refer to an example with detailed explanations [here](https://github.com/64bitpandas/amethyst/blob/main/config.yaml).

### Adding code block titles

Improve the organization of your code blocks by assigning titles to them. This practice functions similarly to providing name tags, enhancing the clarity and structure of your content.

{{< tabs "Steps" >}}
{{< tab "Step 1" >}}
1. **Activate titles**: Ensure your code block titles are enabled in the configuration by setting the `enableCodeBlockTitle` parameter to `true` in your `config.yaml` file:

    ```yaml {title="data/config.yaml"}
    enableCodeBlockTitle: true
    ```
{{< /tab >}}
{{< tab "Step 2" >}}
2. **Title your blocks**: Add the `title` attribute to any code block you wish to title:

    ```markdown
       ```yaml {title="data/config.yaml"}
       enableCodeBlockTitle: true  # example from step 1
       ```
{{< /tab >}}
{{< /tabs >}}

> [!warning]- Follow these steps carefully
>
> Ensure to follow the provided steps carefully to avoid any potential issues and to fully leverage the benefits of adding code block titles. If **```{title=<my-title>}```** is included in your code block and code block titles are not **enabled**, no errors will occur, and the title attribute will be ignored.

### Customize HTML favicons

Elevate the visual appeal of your website by customizing the favicons. Here's how you can customize them:

> [!info]- Definition of favicons
>
> Favicons, short for "favorites icons," are small icons associated with a website that appear in various locations, such as browser tabs, bookmark bars, and when the website is saved to the home screen on mobile devices. They serve as visual identifiers for websites and enhance user experience.

{{< tabs >}}
{{< tab "Favicon configuration" >}}

To personalize your website's favicons, you can modify them by editing the `data/config.yaml` file. The default favicon setup, in the absence of any specified favicon key, is as follows:

```html {title="layouts/partials/head.html"}
<link rel="shortcut icon" href="icon.png" type="image/png">
```

However, you can customize the favicon by adding or modifying the favicon key in your `data/config.yaml` file. Here's an example YAML format, using a `List[Dictionary]`, which mirrors the default configuration:

```yaml {title="data/config.yaml"}
favicon:
      - { rel: "shortcut icon", href: "icon.png", type: "image/png" }
      #  - { ... } # Repeat for each additional favicon you want to add
```
- The `href` attribute specifies the path to the favicon image file.
- You can define additional favicons using the same format for each one.

{{< /tab >}}

{{< tab "Multiple Favicons" >}}

If you wish to add an Apple touch icon, which appears when users add your site to the home screen of their Apple devices, you can append it to the existing favicon configuration in `data/config.yaml`. Here is an example:

```yaml {title="data/config.yaml"}
favicon: |
  <link rel="shortcut icon" href="icon.png" type="image/png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
```
In this example, the first <link> tag specifies the default favicon for all devices, while the second <link> tag specifically defines the Apple touch icon. The ```rel="apple-touch-icon"``` attribute indicates that this link is intended for Apple devices, and the ```sizes="180x180"``` attribute specifies the dimensions of the icon.

{{< /tab >}}

{{< tab "Additional Information" >}}

Types of favicon files: Favicon files can have different types, each corresponding to a specific image format. Common types include:
- `image/x-icon`: For icons in ICO format.
- `image/png`: For icons in PNG format.
- `image/gif`: For icons in GIF format.
- `image/jpeg` or `image/jpg`: For icons in JPEG format.
- `image/svg+xml`: For icons in SVG format.

These are just a few examples, and the appropriate type depends on the format of the favicon file you're using and the compatibility requirements of your website.

If you are interested in more information about the current and past standards of favicons, you can read [this article](https://www.emergeinteractive.com/insights/detail/the-essentials-of-favicons/).

{{< /tab >}}

{{< /tabs >}}

> [!note] Important note
>
> Ensure to place your favicon files in the correct directory and update the paths accordingly in your configuration file to ensure proper display across all devices and platforms.

### Graph view
To tailor the Interactive Graph view to your preferences, navigate to the  `data/graphConfig.yaml` file. The default configuration, along with descriptions, is available [here](https://github.com/64bitpandas/amethyst/blob/main/data/graphConfig.yaml).

### Language support

Amethyst offers built-in support for languages such as Chinese, Japanese, and Korean. This means you can start using these languages immediately without the need for additional configurations. However, if you wish to add support for languages that read from right to left, such as Arabic, Hugo (and consequently, Amethyst) provides native support for this.

To enable support for right-to-left (RTL) languages, follow the instructions provided by Hugo [here](https://gohugo.io/content-management/multilingual/#configure-languages) and modify your config.yaml file as needed.

For example, to configure the Arabic language, you can add the following snippet to your config.yaml file:

```yaml
defaultContentLanguage: ar
languages:
  ar:
    languagedirection: rtl
    title: مدونتي
    weight: 2
```
This configuration sets the default language to Arabic (ar), specifies that text will be read from right to left (languagedirection: rtl), and sets the site title in Arabic (title: مدونتي). The weight is used to sort languages in the language selection menu if you have multiple languages configured.

## Custom styles
If you desire more customization, explore the CSS style in a`assets/_custom.scss`. To target specific sections of your site, consider adding IDs and classes to the HTML partials in `/layouts/partials`.

### Changing the color scheme
Modify the default color schemes for both light mode and dark mode by accessing `assets/_colors.scss`. You have the option to directly replace the values for existing color variables to facilitate seamless edits or create new variables to reference in `_custom.scss`.

Here's an example of color scheme adjustments in the ```_colors.scss``` file on the left, and the corresponding outcome on the right.
![Example Color Scheme](/images/example-color-scheme.png)

### Changing the fonts
Font configurations are located in `assets/_fonts.scss`. You'll find examples for both local fonts (specified using `@font-face`) and web fonts (imported with `@import` from font distributors like Google Fonts).
For local fonts, store them in the `static/fonts` directory.

Define custom local fonts using `@font-face` in `assets/_fonts.scss`. These fonts are stored locally and are ideal for customizing the typography of your website.

For example:

```scss
@font-face {
  font-family: "PP Mori";
  font-style: normal;
  font-weight: normal;
  src: url('fonts/PPMori-SemiBold.woff2');
}
```

Import web fonts from external sources like Google Fonts using `@import` in `assets/_fonts.scss`. These fonts are fetched dynamically from the web and provide a wide range of options for typography customization.

For example:
```scss
@import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;700&family=IBM+Plex+Sans:wght@400;600&display=swap');
```

### Partials
Partials define the rendering of specific components on your webpage. You can modify the relevant layouts in the `/layouts` directory.
For instance, to adjust the layout of the home page, navigate to `/layouts/index.html`. To customize the footer, edit `/layouts/partials/footer.html`.

For further information on partials, visit [Hugo's website](https://gohugo.io/templates/partials/).

If you encounter difficulties, explore the [FAQ and troubleshooting guide](setup/troubleshooting.md) for assistance.

## Search
Amethyst offers two search modes: Natural language and Full-text.

{{< columns >}}

### Natural language search
Powered by Operand, Natural Language search understands language like a person does, delivering results that best match user intent. It offers higher quality results compared to Full-text search and operates similarly to Google Search. To set up Natural Language search:

Login or Register: Create an Operand account and verify it via email. 
> [!note] Note
>
> No credit card is required, and the first $10 of usage each month is free.

Create an Index: Define your index on the Operand dashboard, noting down the unique index ID.

Index Your Site: Add your site's sitemap URL to the index configuration.

Get API Key: Manage your API keys on the Operand dashboard or create a new one if needed.

Update Configuration: Set enableSemanticSearch to true in config.yaml, along with operandApiKey and operandIndexId values.

```yaml {title="config.yaml"}
# the default option
search:
  enableSemanticSearch: true
  operandApiKey: "jp9k5hudse2a828z98kxd6z3payi8u90rnjf"
  operandIndexId: "s0kf3bd6tldw"
```
Deploy Changes: Push your configuration changes and wait for the site to deploy.

<--->

### Full-text search
The default search mode in Amethyst, Full-text search, provides results that precisely match the search query. This mode is straightforward to set up but may yield lower quality matches.

```yaml {title="config.yaml"}
# Default option
enableSemanticSearch: false
```

{{< /columns >}}

## Next steps

Now that you know how to customize your site and set up search functionality, you can follow these next steps:

* [Understand how to deploy your Amethyst website to the Web](tecaa/deployingwebsite.md), to publish it and start getting visitors.


<br>
<br>
<br>
<br>


{{< expand "How this page was made">}}
## Page author
This page was authored by Márcia Carvalho (Nº 1190844), a Master's student in Informatics Engineering at ISEP, Porto, Portugal.
This website was developed as part of the TECAA course unit.

## Development process
This page provides guidance on customizing and setting up search functionality in the Amethyst Hugo theme. The content was reorganized and summarized from the official Amethyst documentation on [Customization](https://amethyst.bencuan.me/setup/config/) and [Search](https://amethyst.bencuan.me/setup/search/) pages.

The development process involved the following steps:

1. Creation of a new Markdown file named ```customization.md``` within the  ```/content/tecaa/``` directory.
2. Configuration of front matter settings, including the title of the page and its weight relative to other pages within the same directory.
3. Added the necessary content and organized the page using various Markdown and Amethyst features, ensuring compliance with the [defined group decisions]().

Below is a summary of the specific decisions made in creating this page, detailing the utilization of various features and elements.

{{< tabs "feature-summary" >}}

{{< tab "Headings" >}} 
### Headings

Headings have been used primarily to organize the content into easily understandable sections, helping users to navigate through the tutorial. Each title serves to distinguish different steps or sections within the tutorial, providing users with a clear sense of progression and context.

_No individual decisions were made._<br>

**Group decision:**
* Headings level follow a correct hierarchy according to [WCAG accessibility guidelines](https://www.w3.org/TR/WCAG21/). 
* Heading titles are written in Sentence Case, aligning with the [Google Developer Documentation Style Guidelines' Highlights](https://developers.google.com/style/highlights).

{{< /tab >}}

{{< tab "Content" >}} 
### Content

**Individual decision:** In the content section, the aim was to provide clear and concise explanations to the user. 

* Contextual definitions were included for terms that readers may not be familiar with, such as "favicons".

* In the "Customize HTML favicons section", an additional tab was added to provide information on different image formats for favicons. This was done to help users on the various types available and how they could utilize them effectively. Hence, it was placed in an additional section.

* It was also discovered that for favicon configuration, it's possible to directly edit the ```html-head.html``` file by modifying the line ```<link rel="icon" href="{{ "favicon.png" | relURL }}" type="image/x-icon">```. Although this method is simple to modify as well, it wasn't included in the text to avoid confusion for users, as modifying the config.yaml file is a simpler approach and covers most configuration settings.

**Group decision:**
* No changes were made to the style or font of the text to ensure consistency with the Amethyst base theme.
* The content was written in accordance with the Highlights of the [Google Developer Documentation Style Guidelines' Highlights](https://developers.google.com/style/highlights), including the use of the second person, active voice, etc.

{{< /tab >}}

{{< tab "Links" >}} 
### Links

**Individual decision:** The usage of links throughout the tutorial serves a simple yet essential purpose: to seamlessly redirect users to external or internal destinations. Whether it's navigating to additional resources, exploring related documentation, or accessing external websites.

{{< /tab >}}
{{< tab "Callouts" >}} 

### Callouts

**Individual decision:** In crafting this page, various callouts were strategically employed to augment user comprehension and engagement. Each callout serves a distinct purpose, carefully tailored to guide and inform the reader.

* **Warning callout:** Employed in the section regarding code block titles to emphasize the importance of following the steps diligently. It serves as a cautionary reminder that if code block titles aren't enabled, errors won't appear, but the assignment will be disregarded. This callout starts closed to draw attention to the warning title initially. Users can open it later if they wish to understand the warning in detail.

* **Info callout:** Used to explain the definition of favicons. It was set as closed since it's optional for users to view, avoiding unnecessary clutter if they're already familiar with the definition.

* **Note callout:** Deployed as open callouts for additional notes within the content. They remained open to ensure easy accessibility and comprehension, as they contained important supplementary information.

{{< /tab >}}
{{< tab "Columns" >}} 

### Columns
**Individual Decision:** Columns were implemented in the "Search" section to illustrate the two different modes of using the search feature: Natural Language and Full-text. The decision to use columns stemmed from the need to present users with a clear visual comparison between the two search modes. By displaying them side by side, users can easily discern the differences and choose the mode that best suits their needs.
{{< /tab >}}
{{< tab "Tabs" >}} 

### Tabs

**Individual decision:** Tabs were strategically incorporated into the page to enhance user experience and streamline information presentation. Each tab serves a specific purpose, allowing users to navigate through content seamlessly.

* **Steps tabs:** Utilized in the "Adding code block titles" section to break down the process into two distinct steps, facilitating user understanding and progression. Users can follow each step sequentially, ensuring clarity and ease of implementation.
* **Information tabs:** Implemented in the "Customize HTML favicons" section to provide alternative information views. Users can choose to view details on adding a favicon, learn about using multiple favicons, or access additional information as per their requirements. This approach offers flexibility and customization, meeting the diverse needs of users, and was also used in this same section on "How the page was made" for the same purpose.

{{< /tab >}}

{{< tab "Expand" >}} 

### Expand

Expand creates a collapsible area of text, perfect to hide these optional details that are not part of the main page's content.

_No individual decisions were made._<br>
**Group decision:** The Expand feature was used to write this very section on "How the page was made". 
{{< /tab >}}

{{< tab "Images" >}} 

### Images

**Individual decision:** An image has been used in the "Changing the color scheme" section to provide a practical example of how color changes are applied in the theme. Each image is accompanied by a caption, offering contextual information about the depicted color scheme adjustment. Additionally, alt text was incorporated to describe the content of each image.

{{< /tab >}}

{{< /tabs >}}

{{< /expand >}}