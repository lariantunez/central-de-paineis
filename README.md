# Central de Painéis

Portal que reúne todos os painéis da empresa numa única página de cartões. A lista é mantida por uma área administrativa: cadastrar, editar ou remover um painel não exige mexer no código.

**[Ler o estudo de caso](https://lariantunez.github.io/central-de-paineis/)** · **[Abrir a central](https://lariantunez.github.io/central-de-paineis/app/)**

![Central de Painéis com dados fictícios](assets/central-home.jpg)

> **Versão de portfólio.** A central original roda em produção, com login na área administrativa. Esta versão é estática: a administração fica aberta e as edições são salvas só no navegador de quem testa.

## O problema

Cada painel nascia como um projeto separado, com o próprio endereço. Os links ficavam espalhados entre mensagens, favoritos e e-mails, e quem precisava de um número não sabia por onde começar.

## O que eu construí

- **Home que não sabe quais painéis existem:** ela lê uma lista e desenha um cartão para cada item.
- **Área administrativa** com duas abas: painéis (cadastrar, editar, remover) e administradores (criar, alterar, excluir, com o usuário principal protegido).
- **Deploy automático** em 4 passos pelo GitHub Actions, no projeto original. Esta versão é publicada direto do branch `main`.

## Decisões técnicas

- **Dados fora da tela:** os painéis vivem em `app/data/paineis.json`, não no HTML.
- **A página nunca fica vazia:** a home procura a lista no navegador, depois no JSON publicado e, por último, numa lista de reserva escrita no próprio código.
- **Campos mínimos, o resto deduzido:** sem inicial, usa a primeira letra do nome; sem URL, aponta para o painel demonstrativo.
- Links externos abrem em nova aba com `noopener noreferrer`.

## Stack

HTML, CSS e JavaScript puro, sem framework e sem etapa de build · JSON · localStorage · GitHub Pages

## Estrutura

| Caminho | Conteúdo |
|---|---|
| `index.html` e `assets/` | Estudo de caso do projeto |
| `app/` | A central: `index.html`, `admin.html`, `painel-demo.html`, `reset-senha.html` e `data/paineis.json` |
| `404.html` | Redireciona endereços antigos para `app/` |

## Rodar localmente

```bash
npx serve .
```

---

**🇺🇸 English:** a portal that gathers all of the company's dashboards on a single page of cards. The home page simply reads a list and draws one card per item, and an admin area adds, edits and removes dashboards without touching the code. A three-level fallback (browser storage, published JSON, built-in list) keeps the page from ever being empty. Plain HTML, CSS and JavaScript with no build step; the original deploys through GitHub Actions. Portfolio version; the original runs in production behind a login.
