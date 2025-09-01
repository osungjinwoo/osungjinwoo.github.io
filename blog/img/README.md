# Pasta de Imagens do Blog

Esta pasta contém as imagens utilizadas nos artigos do blog.

## Estrutura Recomendada

```
blog/img/
├── artigo1/           # Imagens específicas do artigo 1
│   ├── main.jpg       # Imagem principal
│   ├── screenshot1.png
│   └── diagram.png
├── artigo2/           # Imagens específicas do artigo 2
│   ├── main.jpg       # Imagem principal
│   ├── code-example.png
│   └── workflow.png
└── shared/            # Imagens compartilhadas
    ├── logo.png
    └── icons/
```

## Como Usar Imagens nos Artigos

### 1. No Front Matter do Artigo

```yaml
---
title: "Título do Artigo"
date: "2024-01-25"
categories: ["Categoria"]
tags: ["tag1", "tag2"]
excerpt: "Descrição do artigo"
image: "img/artigo1/main.jpg" # Imagem principal para preview
---
```

### 2. No Conteúdo Markdown

```markdown
# Título do Artigo

![Descrição da imagem](img/artigo1/screenshot1.png)

## Seção

Texto do artigo...

![Diagrama do fluxo](img/artigo1/diagram.png)
```

## Formatos Suportados

- **JPG/JPEG**: Para fotografias e imagens com muitas cores
- **PNG**: Para screenshots, diagramas e imagens com transparência
- **GIF**: Para animações simples
- **WebP**: Para melhor compressão (suporte moderno)

## Tamanhos Recomendados

- **Imagem principal**: 800x400px
- **Screenshots**: 1200x800px
- **Diagramas**: 800x600px
- **Ícones**: 64x64px

## Otimização

1. **Comprima as imagens** antes de fazer upload
2. **Use nomes descritivos** para os arquivos
3. **Mantenha a estrutura organizada** por artigo
4. **Considere usar WebP** para melhor performance

## Exemplo de Uso

```markdown
---
title: "Como Fazer Hacking Ético"
date: "2024-01-25"
categories: ["Segurança", "Hacking"]
tags: ["pentest", "cybersecurity"]
excerpt: "Guia completo sobre hacking ético"
image: "img/hacking-etico/main.jpg"
---

# Como Fazer Hacking Ético

![Hacking Ético](img/hacking-etico/main.jpg)

O hacking ético é uma disciplina fundamental...

## Metodologia

![Fluxo de Pentest](img/hacking-etico/workflow.png)

### 1. Reconhecimento

![Ferramentas de Reconhecimento](img/hacking-etico/tools.png)

Texto sobre reconhecimento...
```
