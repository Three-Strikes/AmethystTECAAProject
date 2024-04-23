---
title: "Setup"
weight: "1"
---
## Introduction
Welcome to the guide on setting up your technical documentation site using Hugo, a fast and flexible static site generator, and the clean and modern Amethyst theme. This comprehensive guide will guide you through the entire process, from installation to content editing, customization, and ultimately deploying your website to the web.
{{< columns >}}
### About Hugo
[Hugo](https://gohugo.io/) is a popular static site generator written in Go. It boasts lightning-fast build times, minimal dependencies, and a large ecosystem of themes and plugins. 
<--->
### About Amethyst Theme
[Amethyst](https://themes.gohugo.io/themes/amethyst/) is a feature-rich Hugo theme designed specifically for technical documentation. It offers a clean and responsive layout, customizable color schemes, syntax highlighting for code blocks, and support for multilingual content. With its focus on readability and usability, Amethyst is the perfect companion for your documentation project.
<--->
> [!info]- Technology Behind Amethyst
>
>The Amethyst theme is crafted with [Obsidian](https://obsidian.md/), a powerful framework for building Hugo themes. Obsidian provides a solid foundation for the theme, ensuring robustness, flexibility, and maintainability. 
{{< /columns >}}

## Getting Started

### Installing Hugo
1. First, you will need to ensure that your system meets the requirements for running Hugo projects. You can install Hugo using one of the following methods:
{{< tabs "preview" >}}
{{< tab "Installing via Package Manager" >}} 
- [macOS (Homebrew)](https://gohugo.io/installation/macos/):
  ```bash
  brew install hugo 
  ```
- [Windows (Chocolatey](https://gohugo.io/installation/windows/):
  ```bash
  choco install hugo -confirm
  ```
- [Linux (apt-get)](https://gohugo.io/installation/linux/):
  ```bash
  sudo apt-get install hugo
  ```
{{< /tab >}}
{{< tab "Installing from Binary" >}} 
Alternatively, you can download the appropriate binary for your operating system from the [Hugo releases page](https://github.com/gohugoio/hugo/releases) and add it to your system's PATH. <br>
> Please consult your operating system documentation if you need help setting file permissions or modifying your PATH environment variable.
{{< /tab >}}
{{< /tabs >}}

2. Once installed, verify the installation by running:
```bash
hugo version
```
### Setting up a new Hugo Site with the Amethyst theme
Setting up an Amethyst project requires a basic understanding of `git`. If you are unfamiliar, [this resource](https://resources.nwplus.io/2-beginner/how-to-git-github.html) is a great place to start!

#### 1. Forking
> A fork is a copy of a repository. Forking a repository allows you to freely experiment with changes without affecting the original project.

Navigate to the GitHub repository for the Amethyst project:

[Amethyst Repository](https://github.com/64bitpandas/amethyst)

Then, Fork the repository into your own GitHub account. If you don't have an account, you can make on for free [here](https://github.com/join). More details about forking a repo can be found on [GitHub's documentation](https://docs.github.com/en/get-started/quickstart/fork-a-repo).

#### 2. Cloning
> Cloning a repository involves creating a local copy of an online repository onto your own machine. This process allows you to work with the repository's files and history directly on your local system. Cloning is particularly useful for collaborating on projects, as it enables contributors to make changes, experiment, and contribute back to the original project without altering the master copy.

After you've made a fork of the repository, you need to download the files locally onto your machine. Ensure you have `git`, then type the following command replacing `YOUR-USERNAME` with your GitHub username.

```shell
git clone https://github.com/YOUR-USERNAME/amethyst
```

## Next steps
Great! Now you have everything you need to start editing. If you're ready to start writing content already, check out the recommended flow for editing notes:

   - [Editing content](tecaa/editingcontent.md)

Having problems? Checkout our [FAQ and Troubleshooting guide](setup/troubleshooting.md).

<br><br><br>
{{< expand "How this page was made">}}
#### Page author
This page was created by Pedro Paulo (Nº 1220496), a Master Student in Informatics Engineering at ISEP, Porto, Portugal.
This website was a project created for the TECAA course unit.

#### Development process
This page aims to guide users through the setup process of a Hugo website featuring the Amethyst theme. The content has been curated by summarizing the essential steps outlined in the [Editing Content](https://amethyst.bencuan.me/setup/setup/) pages of the official Amethyst documentation, supplemented with additional relevant information to serve the intended purpose effectively.

Below is a summary of the individual decisions used in this page, regarding each feature.

{{< tabs "feature-summary" >}}
{{< tab "Text, headings and links" >}} 

#### Text

_No individual decisions needed to be made in relation to the text._
<br>
Following group decisions: 

* No style or font changes were made to the text, so that the page follows the base Amethyst theme.
* The content was written following the [Google Developer Documentation Style Guidelines' Highlights](https://developers.google.com/style/highlights). 

#### Headings

_No individual decisions were made._
<br>
Special attention was given so that:

* Headings level follow a correct hierarchy, as per the [WCAG accessibility guidelines](https://www.w3.org/TR/WCAG21/)
* Heading titles are written with Sentence Case, as per the [Google Developer Documentation Style Guidelines' Highlights](https://developers.google.com/style/highlights)

#### Links

**Individual decision:** Do not use the styled buttons provided by Amethyst to provide links.<br>

* **Reason:** These buttons are designed to be a more appelative way to show links to the user. However, buttons can also be used to trigger various actions in dynamic websites, instead of being links to other pages. These two distinct usages of buttons may create confusion to the reader, so it was decided that links to other pages are conveyed solely by using the simple Markdown links.

Group decisions regarding links were followed.

{{< /tab >}}
{{< tab "Callouts" >}} 

#### Callouts

**Individual decision:** Foldable Callouts were used to give the reader additional warnings or recommendations whenever necessary, as their colorful styles are a very effective way to pull the user's attention. All three callouts start out closed:

* The warning callout starts closed so that all emphasis is given to the warning title. Afterwards, if the user wants to understand the warning, they can open the callout.
* The two additional content callouts start closed due to their optional nature. Being closed, they do not clutter the page's content, and the user can still open them and read the contents if interested.

{{< /tab >}}
{{< tab "Columns" >}} 

#### Columns
**Individual decision:** The Columns feature, provided by the Amethyst theme, was used in this page to display to the reader two images side by side. 

* **Reason:** The paths descriptions in the **Folder Structure** instructions section may be difficult to understand at first for a less experinced user. To mitigate this, the objective was to present the reader with two images that together show the structure of an Amethyst Hugo project. As such, the Columns feature that allows the user to visualize both images side by side and compare both was considered to be an ideal solution.
{{< /tab >}}
{{< tab "Tabs" >}} 

#### Tabs

**Individual decision:** The Tabs feature was used to show two sets of alternative steps that the user can follow to preview their changes, depending on their decision to integrate Amethyst with Obsidian Vaults or not. 

* **Reason:** This is a typical use case for tabs, since it conveys to the user that they just have to choose one of the options, not follow both.
{{< /tab >}}

{{< tab "Expand" >}} 

#### Expand

_No individual decisions were made._<br>
As defined in the group decisions, The Expand feature was used to write this very section on "How the page was made". Expand creates a collapsible area of text, perfect to hide these implementation details that are not part of the main page's content.
{{< /tab >}}
{{< /tabs >}}

{{< /expand >}}
