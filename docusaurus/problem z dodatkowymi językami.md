nie podświetlał syntaktyki c#, więc

- docusaurus.config
```json
   ],*/
      copyright: `Copyright © ${new Date().getFullYear()} My Project, Inc. Built with Docusaurus.`,
    },
    prism: {
      theme: prismThemes.github,
      darkTheme: prismThemes.dracula,
      additionalLanguages: ['csharp', 'python', 'kotlin'],
    },
  } satisfies Preset.ThemeConfig,
};
```

potem dodatkowa paczka
`npm run swizzle @docusaurus/theme-classic prism-include-languages --typescript`

a w mdx używasz słowa `csharp`














