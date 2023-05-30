---
id: my-doc
title: 看看你的文檔
sidebar_label: 我的分享
---

# **Docusaurus**

Docusaurus 是一款靜態網站生成器，它提供開箱即用的文檔，也可以用於搭建各種網站（像是個人網站、產品、部落格…之類的）

## **步驟 1：安裝 Docusaurus**

執行以下命令來安裝：

```bash
npx create-docusaurus@latest my-docusaurus-project
cd my-docusaurus-project
```

## **步驟 2：編輯網站內容**

Docusaurus 使用 Markdown 文件來編寫網站內容。在 **`docs`** 資料夾裡有預設的文檔目錄結構，可以在這裡創建、編輯或刪除文件。

### **添加文檔**

你可以隨手寫一些東西：

```markdown
---
id: my-doc
title: 看看你的文檔
sidebar_label: YO
---

### 哈囉

搭拉拉康

這裡可以放你的程式碼教學之類的
```

**`id`**、**`title`** 和 **`sidebar_label`**，可以使用這些元信息來定義文檔的唯一標識符、標題和在側邊欄中顯示的標籤。

### **自定義側邊欄**

可以通過配置文件進行自定義。

我們試試在 **`sidebars.js`** 文件中，定義側邊欄的結構和內容：

```jsx
module.exports = {
  docs: [
    {
      type: 'category',
      label: '入門',
      items: ['yo'],
    },
    {
      type: 'category',
      label: '教程',
      items: ['battle'],
    },
  ],
};
```

## **步驟 3：自定義佈局和主題**

Docusaurus 允許自定義網站的佈局和主題。在 **`docusaurus.config.js`** 可以找到許多配置選項，包括網站的標題、描述、語言、佈局跟主題。

### **自定義佈局**

在 **`docusaurus.config.js`** 可以設置網站的標題、描述和其他元信息：

```jsx
const config={
  title: '我的 Docusaurus 網站',
  tagline: '這是一個示例網站',
  url: 'https://example.com',
  baseUrl: '/',
  onBrokenLinks: 'throw',
  onBrokenMarkdownLinks: 'warn',
  favicon: 'img/favicon.ico',
  organizationName: 'my-organization',
  projectName: 'my-project',
};
module.exports = config;
```

### **自定義主題**

Docusaurus 提供了多個預設主題，可以在 **`docusaurus.config.js`** 的 **`themeConfig`** 配置：

```
  themeConfig: 
	/** @type {import('@docusaurus/preset-classic').ThemeConfig} */	
	({
      // Replace with your project's social card
      image: 'img/docusaurus-social-card.jpg',
      navbar: {
        title: 'My Site',
        logo: {
          alt: 'My Site Logo',
          src: 'img/logo.svg',
        },
        items: [
          {
            type: 'docSidebar',
            sidebarId: 'tutorialSidebar',
            position: 'left',
            label: 'Tutorial',
          },
          {to: '/blog', label: 'Blog', position: 'left'},
          {
            href: 'https://github.com/facebook/docusaurus',
            label: 'GitHub',
            position: 'right',
          },
        ],
      },
      footer: {
        style: 'dark',
        links: [
          {
            title: 'Docs',
            items: [
              {
                label: 'Tutorial',
                to: '/docs/intro',
              },
            ],
          },
          {
            title: '連結',
            items: [
              {
                label: 'Stack Overflow',
                href: 'https://stackoverflow.com/questions/tagged/docusaurus',
              },
              {
                label: 'Discord',
                href: 'https://discordapp.com/invite/docusaurus',
              },
              {
                label: 'Twitter',
                href: 'https://twitter.com/docusaurus',
              },
            ],
          },
          {
            title: 'More',
            items: [
              {
                label: 'Blog',
                to: '/blog',
              },
              {
                label: 'GitHub',
                href: 'https://github.com/itou02/Docusaurus',
              },
            ],
          },
        ],
        copyright: `Copyright © ${new Date().getFullYear()} My Project, Inc. Built with Docusaurus.`,
      },
      prism: {
        theme: lightCodeTheme,
        darkTheme: darkCodeTheme,
      },
    }),
```

## **步驟 4：使用插件擴展功能**

可以在 **`docusaurus.config.js`** 的 **`plugins`** 啟用和配置插件。

使用 **`@docusaurus/plugin-content-docs`** 插件：

```
module.exports = {
  plugins: [
    [
      '@docusaurus/plugin-content-docs',
      {
        id: 'my-docs',
        path: 'docs',
        routeBasePath: 'docs',
        sidebarPath: require.resolve('./sidebars.js'),
      },
    ],
    // ...其他插件
  ],
};

```

他會讀取 **`docs`** 資料夾中的 Markdown 文件然後生成相應的文檔頁面。

---

完成編輯和配置後，把他build上去就可以部屬啦：