<h1 align="center">Sass</h1>

- Sass: Pré-processadores são programas que permitem gerar CSS a partir de determinada sintaxe. A maioria deles permite adicionar funções que não são possíveis em CSS puro, como mixins, nesting, seletores, herança, etc. Essas funções facilitam a manutenção e aumentam a legibilidade do CSS.

## 📄 Informações interessantes
Nesse projeto utiliza o padrão de nomenclatura BEM

- BEM: Block Element Modifier(Bloco, Elemento, Modificador. Esses três pilares são a base dessa metodologia, e também as categorias em que os elementos são divididos)

<p align="center">
    <img alt="BEM" src="https://miro.medium.com/max/1400/1*5VGR1kwb_1KJOhhhCPeL-A.png">
</p>

#### Parent selector:
Entende-se &__content = main__content:
```css
.main {
    &__content {
  }
}
```

#### Variaveis
```css
    $light-grey: #eaeaeb
```

#### Placeholder Selector (%) e Extend:
Cria-se como se fosse uma classe:

```css
    %no-decoration {
        text-decoration: none;
    }
```
Utiliza-se dessa forma:

```css
    &__post-title {
        font-size: 14px;
        color    : $purple;
        @extend %no-decoration;

        &:hover {
             @extend %u-decoration;
        }
    }
```

#### Mixings normais:
```css
    @mixin reset-list {
        margin    : 0;
        padding   : 0;
        list-style: none;
    }
```

Utiliza-se dessa forma:
```css
   &__posts {
            @include reset-list;
        }
```

#### Mixings com variaveis:
```css
    @mixin flx($property, $jty-cnt) {
        display     : flex;
        #{$property}: $jty-cnt;
    }
```

Utiliza-se dessa forma:
```css
    &__posts {
        @include flx(justify-content, center);
    }
```

#### Mixing com media query:
```css
    @mixin for-phone-only {
        @media (max-width: 767.98px) {
            @content;
        }
    }
```

Utiliza-se dessa forma:
```css
    &__content {
        @include for-phone-only {
            width: 100%;
        }
        width  : 70%;
        padding: 40px 8px;
    }
```

#### Mixings vs Placeholders
```
A diferença entre os mixings e placeholders é: 
    - O código compilado pelos placeholders não são duplicados.
    - Se precisa de variáveis, utilize o mixin. Eles podem até mesmo possuírem argumentos que lhe permitem produzir uma ampla variedade de estilos com poucos mixins.
```

#### Function
```css
    @function calculateRem($size) {
        @return $size / 16px * 1rem;
    }
```

Utiliza-se dessa forma:
```css
    @mixin fontSize($size) {
        font-size: calculateRem($size);
    }
```

#### If/else

```css
@mixin theme-collection($half-post: true) {
    @include for-phone-only {
        width: $full-width;
    }
    @if $half-post {
        width: $half-width;
    } @else {
        width: $full-width;
    }
}
```
#### Imports
```
    @import 'header', 'footer', 'about', 'article', 'collection', 'contact';
```

# Instalação para utilizar comandos sass
```
npm install -g sass
```

## ✨ Tecnologias

Esse projeto foi desenvolvido com as seguintes tecnologias:
- [Node.js](https://nodejs.org/en/)

## 📄 Comandos interessantes
- Rode `sass --watch scss/*.scss:css/*.css`
