# Computação Gráfica - Trabalhos Práticos

Repositório dedicado aos trabalhos práticos desenvolvidos para a disciplina de **Computação Gráfica** do **Unipac Barbacena**, ministrada pelo **Prof. Rodrigo Fernandes dos Santos**.

O projeto utiliza um framework gráfico construído sobre **Pygame**, **PyOpenGL** e **NumPy**, com base nas aulas e no livro *Developing Graphics Frameworks with Python and OpenGL* (Stemkoski e Pascale, CRC Press, 2022).

---

## Integrantes da Dupla
- **Pedro Henrique Ramos de Carvalho**

---

## Visão Geral das Atividades

A entrega contempla as três atividades avaliativas práticas desenvolvidas ao longo das aulas:

| # | Atividade | Localização do Código | Captura de Tela |
|---|---|---|---|
| **1** | Mini Sistema Solar | `Aula_Transformacoes/alunos/atividade_sistema_solar.py` | `Aula_Transformacoes/alunos/capturas/resultado.png` |
| **2** | Braço Robótico | `Aula_GrafoCena/alunos/atividade_braco.py` | `Aula_GrafoCena/alunos/capturas/resultado.png` |
| **3** | Cubo com Satélite Texturizado | `Aula_Texturas/alunos/atividade_cubo.py` | `Aula_Texturas/alunos/capturas/resultado.png` |

---

## Detalhamento das Atividades e Respostas Conceituais

### 1. Atividade 1 – Mini Sistema Solar
* **Descrição da Solução:** Implementação de um sistema solar hierárquico utilizando transformações geométricas matriciais combinadas via operador `@`. O Sol rotaciona em torno do próprio eixo, um planeta orbita o Sol com raio de 0.6 unidades e rotação própria independente, e uma Lua orbita o planeta com raio de 0.2 unidades acompanhando seu movimento. As setas do teclado ($\uparrow$ e $\downarrow$) ajustam a velocidade da órbita.
* **Resposta da Questão Conceitual:**
  > **Por que a órbita utiliza `R @ T` e a rotação própria do planeta fica à direita da translação?**  
  > A órbita utiliza `R @ T` (Rotação à esquerda da Translação) porque as transformações operam da direita para a esquerda sobre os vértices do objeto: o ponto é primeiro transladado para longe da origem (definindo o raio da órbita) e depois rotacionado em torno da origem (o Sol). A rotação própria e a escala do planeta ficam à direita da translação porque atuam no sistema de coordenadas local do próprio astro, fazendo-o girar em torno de seu eixo local antes que o resultado seja posicionado na órbita geral.

---

### 2. Atividade 2 – Braço Robótico
* **Descrição da Solução:** Modelagem de um braço robótico articulado utilizando um **Grafo de Cena** (`Object3D`). A estrutura é composta por um pivô na base, um braço laranja conectado pelo ombro, um pivô de cotovelo na extremidade superior, um antebraço azul e uma garra cinza na ponta. Os controles do teclado movimentam a base (`A`/`D`), o ombro (`W`/`S`) e o cotovelo (`I`/`K`).
* **Resposta da Questão Conceitual:**
  > **Por que foi necessário utilizar pivôs em vez de girar diretamente as caixas que representam o braço e o antebraço?**  
  > Os pivôs (`Object3D` vazios) funcionam como nós de articulação que definem o ponto exato de rotação (como as juntas do ombro e do cotovelo). Como as matrizes em um grafo de cena se propagam hierarquicamente para os filhos, rotacionar diretamente a geometria da caixa faria com que ela girasse em torno do seu próprio centro geométrico em vez da extremidade de conexão, causando desalinhamentos indesejados nas juntas.

---

### 3. Atividade 3 – Cubo com Satélite Texturizado
* **Descrição da Solução:** Aplicação de texturas OpenGL em malhas 3D. O cubo principal é renderizado utilizando a textura `mosaico.png` com velocidade de rotação ajustável pelas setas ($\uparrow$ e $\downarrow$). Um segundo cubo menor atua como satélite (filho do cubo principal), posicionado a 1.3 unidades com escala 0.4, texturizado com `grade_uv.png` repetida 2x2 (`repeatUV = [2,2]`) e com rotação autônoma de 2 rad/s em torno do seu próprio eixo X.
* **Resposta da Questão Conceitual:**
  > **Qual é o papel das coordenadas UV em uma textura e qual é o efeito da configuração `repeatUV = [2,2]`?**  
  > As coordenadas UV mapeiam os vértices de uma superfície geométrica 3D para o espaço bidimensional (2D) da imagem da textura, orientando a projeção da imagem sobre a malha. A configuração `repeatUV = [2,2]` faz com que a textura seja repetida duas vezes horizontalmente (U) e duas vezes verticalmente (V) em cada face do cubo, gerando um padrão de mosaico/grade duplicado (tiling).

---

## Estrutura do Repositório

```text
├── core/                           Engine base compartilhada
├── Aula_Transformacoes/
│   └── alunos/
│       ├── atividade_sistema_solar.py
│       └── capturas/resultado.png  Captura do Mini Sistema Solar
├── Aula_GrafoCena/
│   └── alunos/
│       ├── atividade_braco.py
│       └── capturas/resultado.png  Captura do Braço Robótico
├── Aula_Texturas/
│   └── alunos/
│       ├── atividade_cubo.py
│       └── capturas/resultado.png  Captura do Cubo com Satélite
└── README.md                       Documentação e respostas da entrega
