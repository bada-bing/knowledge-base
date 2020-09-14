## Markdown
- [slides](https://github.com/mike-works/vscode-fundamentals/blob/master/docs/1_using/markdown.md)
- you can use img tags (like in html) and give them a lot of options
  `<img src="vscode_icon.png" height=50 align=right vspace=20 />`
- align attribute can be used on variety of HTML tags
- `<p align=right>hello</p>`
### details
```markdown
<details>
  <summary>Click me for something crazy</summary>

  The content which is hidden
  ```ts
  let Hello: string = "World";
  ```
</details>
```
### description lists
```markdown
<dl>
  <dt>Images</dt>
  <dd>.jpg, .gif, .png</dd>
  <dt>Styles</dt>
  <dd>.css</dd>
</dl>
```

## Emmet
|              Tip & What is about               |                                                                 Section                                                                 |
| :--------------------------------------------: | :-------------------------------------------------------------------------------------------------------------------------------------: |
|      Find the process using specific port      |                                                           VS Code can do that                                                           |
|                Emmet Shortcuts                 | [Creating HTML with Emmet](https://burkeholland.gitbook.io/vs-code-can-do-that/exercise-2-productivity-tricks/creating-html-with-emmet) |
|          Code/HTML Folding By Region           |                                                        \\#region & \\#endregion                                                         |
| Debugging Applications within Docker Container |                [Debugging Docker Containers](https://burkeholland.gitbook.io/vs-code-can-do-that/exercise-5-docker/debugging-docker-containers)                |

|                  Action                   |     Shortcut     |
| :---------------------------------------: | :--------------: |
| Check Build Tasks for the associated File | Ctrl + Shift + B |

Emmet is aware of the context you are in
- by default it will give you `div`, but if you are inside of `ul` it will give you `li` by default

some emmet abbreviations
! (and TAB) gives you basic HTML page template

sometimes if you write long expressions, emmet can get lost - in that cases you should press SPACE + ENTER to bring emmet back

⭐ Emmet has functionality `balance inward` & `balance outward`
  - it balances your selection (of code) to the closing tags (this is like in intellij IDEA when you press multiple times CTRL + W) - it expands your selection in a smart way
⭐ `Wrap with abbreviation` - this will wrap the selection with `emmet abbreviation` (e.g., `div`)
⭐ `Update Tag` - can be used to replace opening and closing tags, e.g., from div to selection
⭐ `Update Image Size` - you should always specify image size (so that browser knows how much space to reserve)
- emmet can do this for you

- think of it as using CSS Selectors for DOM generation
- emmet is a nice feature, aim to use it! (and don't be obsessed with productivity) like in regex... better to use many small emmet patterns than one which is big
  - also, vs code usually places cursors in right spots, so that helps as well
- 🌟if I understood correctly when typing abreviations, you should not use spaces anywhere!
- "+" sibling selector `.navbar + .content + .footer`
- ">" direct descendant selector `ul > .list-items*5{Item $}`
  - it will create 5 li items with content "Item 1", ... $ represents index
  - it already knows that inside of ul children should be of type `li`

- Emmet is inteligent enough to read data aobut the size of the image and to populate attributes width and height automatically
		- it is important to set this attributes in advance so that browser knows immediately how much space to reserve for the image
    - By using updateImageSize in command in VS Code, emmet can find the source of the image and automatically populate these attributes
