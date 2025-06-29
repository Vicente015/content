---
title: "Mi biblioteca 📚"
obsidianUIMode: preview
---

## Por leer

### Ficción

%% run start
```ts
const formatBook = (book) => `**[[${book.file.path}|${book.title}]]** por ${new Intl.ListFormat("es").format(book.author)}`

return dv.markdownList(
	dv.pages('#book')
		.where(p => p.tags?.includes("unread") && p.genre?.includes("fiction"))
		.map(formatBook)
)
``` 
%%
- **[[books/El PRINCIPITO.md|El Principito]]** por Antoine de Saint-Exupéry
- **[[books/El Alquimista.md|El Alquimista]]** por Paulo Coelho

%% run end %%

### No ficción

%% run start
```ts
const formatBook = (book) => `**[[${book.file.path}|${book.title}]]** por ${new Intl.ListFormat("es").format(book.author)}`

return dv.markdownList(
	dv.pages('#book')
		.where(p => p.tags?.includes("unread") && p.genre?.includes("non-fiction"))
		.map(formatBook)
)
``` 
%%
- **[[books/Una ética de la Tierra.md|Una ética de la Tierra]]** por Aldo Leopold
- **[[books/Código sostenible.md|Código sostenible]]** por Carlos Blé Jurado
- **[[books/Comunicación no violenta.md|Comunicación no violenta]]** por Marshall Rosenberg
- **[[books/Al oeste con la noche.md|Al oeste con la noche]]** por Beryl Markham

%% run end %%

## Leyendo

%% run start
```ts
const formatBook = (book) => `**[[${book.file.path}|${book.title}]]** por ${new Intl.ListFormat("es").format(book.author)}`

return dv.markdownList(
	dv.pages('#book')
		.where(p => p.tags.includes("reading"))
		.map(formatBook)
)
``` 
%%
- **[[books/Comer para no morir.md|Comer para no morir]]** por Gene Stone y Michael Greger

%% run end %%

## Leídos

%% run start
```ts
const formatBook = (book) => `**[[${book.file.path}|${book.title}]]** por ${new Intl.ListFormat("es").format(book.author)}`

return dv.pages("#book")
.where(p => p.tags.includes("read"))
.groupBy(p => dv.date(p.last).year)
.sort(g => g.key, "desc")
.map((group) =>
	`### ${group.key}\n` +
	dv.markdownList(group.rows.map(formatBook))
)
.join("\n")
``` 
%%
### 2025
- **[[books/Fahrenheit 451.md|Fahrenheit 451]]** por Ray Bradbury

### 2024
- **[[books/Un Mundo Feliz.md|Un Mundo Feliz]]** por Aldous Huxley
- **[[books/The Boy Who Could Change the World.md|The Boy Who Could Change the World]]** por Aaron Swartz
- **[[books/El marciano.md|El marciano]]** por Andy Weir
- **[[books/El accidente de Lauren Marsh.md|El accidente de Lauren Marsh]]** por Guillem Morales
- **[[books/Busy Doing Nothing.md|Busy Doing Nothing]]** por Rekka Bellum y Devine Lu Linvega

### 2022
- **[[books/1984.md|1984]]** por George Orwell

%% run end %%
