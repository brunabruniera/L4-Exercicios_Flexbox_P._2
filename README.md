# Respostas – Flexbox

## 1. Revisão da parte 1

### 1. Qual é a diferença entre contêiner e item?

O contêiner é o elemento que guarda e organiza os outros elementos. Já os itens são aqueles que ficam dentro dele. Para transformar um elemento em contêiner flexível, utilizamos `display: flex;`.

### 2. Qual é o eixo principal padrão?

Por padrão, o eixo principal é horizontal, seguindo da esquerda para a direita. Isso acontece porque o `flex-direction` vem configurado como `row`.

## 2. Crescer: flex-grow

### 3. O que é a sobra de espaço?

É a parte do espaço que continua livre depois que os itens ocupam seus tamanhos iniciais. Se todos estiverem com `flex-grow: 0`, esse espaço não será dividido entre eles.

### 4. Qual é o valor padrão de flex-grow?

O valor inicial é `0`. Isso faz com que os itens mantenham seu tamanho, sem aumentar para preencher o espaço que sobrou.

### 5. Analogia da pizza

- **Mesa:** representa o espaço total do contêiner.
- **Prato:** corresponde ao espaço inicial de cada item.
- **Sobra:** é o espaço que ainda está livre.
- **Peso do flex-grow:** indica quanto da sobra cada item vai receber.

### 6. Como fazer a marca ocupar a sobra?

Basta adicionar `flex-grow: 1;` no elemento da marca para que ele aumente e aproveite o espaço disponível.

### 7. Três itens com base 0, faixa de 600px e pesos 2, 3 e 1.

**Primeiro, somamos os valores de grow:**

2 + 3 + 1 = 6

**Depois, dividimos o espaço pela soma:**

600 / 6 = 100px

**Agora calculamos o tamanho de cada item:**

- Item 1: 2 × 100 = 200px
- Item 2: 3 × 100 = 300px
- Item 3: 1 × 100 = 100px

**Resposta:** os itens terão 200px, 300px e 100px, respectivamente.

### 8. Três itens com base de 100px, faixa de 600px e pesos 0, 1 e 2.

**Primeiro, calculamos o espaço ocupado inicialmente:**

100 + 100 + 100 = 300px

**Encontramos o espaço que restou:**

600 - 300 = 300px

**Somamos os valores de grow:**

0 + 1 + 2 = 3

**Dividimos a sobra pelos pesos:**

300 / 3 = 100px

**Por último, calculamos o tamanho de cada item:**

- Item 1: 100 + (0 × 100) = 100px
- Item 2: 100 + (1 × 100) = 200px
- Item 3: 100 + (2 × 100) = 300px

**Resposta:** a sobra é de 300px e os tamanhos finais ficam em 100px, 200px e 300px.

## 3. Encolher: flex-shrink

### 9. Quando flex-shrink entra em ação?

Essa propriedade é utilizada quando os itens não cabem no espaço disponível e precisam diminuir de tamanho. Seu valor padrão é `1`.

### 10. Dois itens de 400px em uma faixa de 600px.

**Calculando o tamanho total:**

400 + 400 = 800px

**Descobrindo quanto ultrapassa o espaço:**

800 - 600 = 200px

**Dividindo a redução entre os dois itens:**

200 / 2 = 100px

**Calculando o tamanho final:**

400 - 100 = 300px

**Resposta:** cada item ficará com 300px.

### 11. Primeiro item com flex-shrink: 0.

Como o primeiro item está com `flex-shrink: 0`, ele não terá seu tamanho reduzido e continuará com 400px.

O espaço restante será:

600 - 400 = 200px

**Resposta:** o primeiro item fica com 400px e o segundo diminui para 200px.

### 12. Exemplo de flex-shrink: 0.

Podemos aplicar essa propriedade em um ícone para evitar que ele diminua de tamanho ou fique deformado quando o espaço da página for menor.

## 4. Tamanho de partida e atalho flex

### 13. O que é flex-basis?

É a propriedade responsável por estabelecer o tamanho inicial de um item antes da distribuição dos espaços. Mesmo que exista um `width` definido, o `flex-basis` pode determinar o tamanho utilizado como referência.

### 14. Por que usar flex-basis: 0?

Porque todos os itens começam sem um tamanho-base definido em pixels, permitindo que o espaço disponível seja dividido conforme os valores de `flex-grow`.

### 15. Tabela dos atalhos flex

| Atalho | Grow | Shrink | Basis |
|---|---:|---:|---|
| `flex: initial` | 0 | 1 | auto |
| `flex: 1` | 1 | 1 | 0% |
| `flex: auto` | 1 | 1 | auto |
| `flex: none` | 0 | 0 | auto |

### 16. Itens de 100px e 300px em uma faixa de 600px.

**Utilizando `flex: 1`:**

Os dois elementos passam a ter base zero e recebem a mesma quantidade de espaço.

600 / 2 = 300px

**Resultado:** cada item terá 300px.

**Utilizando `flex: auto`:**

Nesse caso, os tamanhos iniciais são considerados.

**Somando os tamanhos:**

100 + 300 = 400px

**Calculando o espaço livre:**

600 - 400 = 200px

**Dividindo o espaço restante:**

200 / 2 = 100px

**Adicionando o valor recebido aos tamanhos iniciais:**

- Primeiro item: 100 + 100 = 200px
- Segundo item: 300 + 100 = 400px

**Resultado:** o primeiro fica com 200px e o segundo com 400px.

A diferença acontece porque `flex: 1` considera a base zero, enquanto `flex: auto` utiliza os tamanhos iniciais dos elementos.

### 17. flex: 1 e flex: auto sempre dão o mesmo resultado?

**Falso.** Os dois atalhos possuem bases diferentes. O `flex: 1` utiliza base zero, enquanto o `flex: auto` considera o tamanho inicial do conteúdo, podendo gerar resultados diferentes.

## 5. O mínimo que trava o encolhimento

### 18. Qual propriedade segura o item?

A propriedade `min-width: auto` pode fazer com que um elemento não diminua além do tamanho mínimo necessário para mostrar seu conteúdo. Para permitir que ele encolha, podemos utilizar `min-width: 0;`.

### 19. Quando esse problema acontece?

Um exemplo é quando uma página possui um menu lateral e uma área de texto. Se existir uma palavra muito comprida, ela pode ultrapassar o espaço disponível e desorganizar o layout.

## 6. order e align-self

### 20. Observe o código.

HTML:

```html
<div class="barra">
  <span>A</span>
  <span>B</span>
  <span class="primeiro">C</span>
</div>
```

CSS:

```css
.barra {
  display: flex;
}

.primeiro {
  order: -1;
}
```

**a) Qual é a ordem visual?**

C, A, B.

**b) Qual é a ordem de foco ao apertar Tab?**

A, B, C, pois a navegação segue a sequência dos elementos no HTML.

**c) Por que isso importa para quem usa leitor de tela?**

Porque a sequência em que os elementos aparecem na tela pode não ser a mesma utilizada na navegação, o que pode causar confusão para o usuário.

### 21. Qual é o valor padrão de order?

O valor padrão é `0`. Assim, um elemento com `order: -1` será exibido antes de outro que tenha `order: 2`.

### 22. O pai tem align-items: stretch.

- `align-self: flex-end;`: posiciona o elemento no final do eixo transversal.
- `align-self: auto;`: utiliza o alinhamento configurado no elemento pai. Nesse caso, o item continua esticado.

### 23. Quando usar align-self e align-items?

O `align-items` serve para configurar o alinhamento de todos os elementos dentro do contêiner. Já o `align-self` é usado quando queremos modificar somente o alinhamento de um item.

## 7. A página com miolo

### 24. Quais são os itens de cada contêiner?

HTML:

```html
<div class="pagina">
  <header>topo</header>
  <div class="miolo">
    <aside>menu</aside>
    <main>texto</main>
  </div>
  <footer>rodape</footer>
</div>
```

- **Dentro de `.pagina`:** estão o `header`, o `.miolo` e o `footer`.
- **Dentro de `.miolo`:** ficam o `aside` e o `main`.

### 25. Por que .miolo precisa de display: flex?

Porque essa propriedade permite organizar os elementos que estão dentro de `.miolo` lado a lado, deixando o menu em uma coluna e o conteúdo principal em outra.

### 26. Explique cada declaração.

CSS:

```css
.pagina {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.miolo {
  display: flex;
  flex: 1;
}

aside {
  flex: 0 0 10rem;
}

main {
  flex: 1;
  min-width: 0;
}
```

- `display: flex;`: ativa o Flexbox na página.
- `flex-direction: column;`: faz com que os elementos sejam organizados em coluna.
- `min-height: 100vh;`: faz a página ter pelo menos a altura total da janela.
- `.miolo { display: flex; }`: organiza o menu e o conteúdo principal na horizontal.
- `flex: 1;` em `.miolo`: faz essa parte ocupar o espaço que estiver disponível.
- `flex: 0 0 10rem;` em `aside`: mantém o menu com tamanho inicial de 10rem, sem crescer ou diminuir.
- `flex: 1;` em `main`: permite que o conteúdo principal utilize o espaço restante.
- `min-width: 0;`: deixa o conteúdo diminuir de largura quando necessário.

## 8. Erros comuns e síntese

### 27. Por que flex-grow: 1 não funciona no contêiner?

Porque essa propriedade é aplicada aos itens e não ao contêiner pai. Para funcionar, devemos colocar `flex-grow: 1;` no elemento que precisa aumentar de tamanho.

### 28. Duas formas de resolver um item que ultrapassa a faixa.

- `min-width: 0;`: permite diminuir a largura do elemento, evitando que conteúdos muito grandes ultrapassem o espaço.
- `flex-shrink: 0;`: faz com que o item mantenha seu tamanho original, sendo indicado para elementos como ícones e botões. Porém, é preciso cuidar para que não ultrapassem os limites do contêiner.

### 29. Resumo das propriedades.

- **flex-basis:** estabelece o tamanho inicial de um item.
- **flex-grow:** controla o quanto um elemento pode aumentar para aproveitar o espaço livre.
- **flex-shrink:** determina a redução do tamanho quando não existe espaço suficiente.
- **order:** modifica a posição visual dos elementos.
- **align-self:** altera o alinhamento de um item individualmente no eixo transversal.
