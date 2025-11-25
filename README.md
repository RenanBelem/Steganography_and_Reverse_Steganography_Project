## Projeto de Esteganografia e Esteganografia Reversa em Java

Este projeto, dividido em duas pastas lógicas (**Esteganografia** e **Esteganografia Reversa**), implementa um sistema de desktop em Java, utilizando a biblioteca Swing, para embutir (esconder) informações (texto ou outra imagem) dentro de uma imagem portadora e, subsequentemente, extrair essas informações.

O método de esteganografia provavelmente utiliza a técnica de LSB (Least Significant Bit), alterando os bits menos significativos dos pixels da imagem portadora para armazenar a mensagem secreta, uma prática comum em projetos demonstrativos.

---

### 🗃️ Estrutura do Projeto

O projeto é composto por classes Java, arquivos `.class` (bytecode) e arquivos de *layout* (`.form`) gerados pelo IDE (provavelmente NetBeans, devido ao uso do `org.netbeans.modules.form`).

#### 1. Pasta Lógica: Esteganografia (Ocultação)

| Arquivo | Descrição |
| :--- | :--- |
| `FormPrincipal.class` | O *bytecode* da classe principal da interface gráfica (GUI) para a funcionalidade de embutir informações. |
| `FormPrincipal.form`  | O arquivo de *layout* (NetBeans Form) que define a estrutura visual da janela principal de esteganografia (Embutir). |
| `FormPrincipal$1.class`, `FormPrincipal$2.class`, `FormPrincipal$3.class`, `FormPrincipal$4.class` | Classes internas anônimas que implementam os `ActionListener`s para os botões e interações da `FormPrincipal`. |
| `Algoritmo.class` | Contém a lógica central para embutir e extrair informações. Possui métodos como `embedText`, `embedImage`, `extractText` e `extractImage`. |
| `Util.class` | Classe de utilidades com métodos para abrir imagens (`openFullImage`, `openEmbbededImage`) e redimensionar imagens (`resize`). Define constantes como `defaultWidth` e `defaultHeight` (implícito, geralmente 50x50 para imagens embutidas). |

#### 2. Pasta Lógica: Esteganografia Reversa (Extração)

| Arquivo | Descrição |
| :--- | :--- |
| `FormReverso.class` | O *bytecode* da classe da interface gráfica (GUI) para a funcionalidade de extrair informações (reversa). |
| `FormReverso.form`  | O arquivo de *layout* (NetBeans Form) que define a estrutura visual da janela de esteganografia reversa (Extrair). |
| `FormReverso$1.class`, `FormReverso$2.class`, `FormReverso$3.class`, `FormReverso$4.class` | Classes internas anônimas que implementam os `ActionListener`s para os botões da `FormReverso`. |

---

### ✨ Funcionalidades (Interface Gráfica)

O projeto apresenta duas janelas principais para as operações de esteganografia.

#### 1. Esteganografia (`FormPrincipal`)

A tela principal é intitulada **"Esteganografia - Prof. Vilmar Abreu Junior"**.

| Componente | Função |
| :--- | :--- |
| **Imagem Original** | Permite selecionar a imagem portadora (capa). É recomendado usar imagens com resolução acima de 800x600. |
| **Imagem para Embutir** | Permite selecionar uma imagem secreta, que será convertida para a resolução 50x50. |
| **Texto para Esconder** | Uma área de texto (`JTextArea`) onde o usuário insere a mensagem secreta. |
| **Diretório de Saída** | Onde os resultados (`resultado_Texto.png`, `resultado_Figura.png`, etc.) serão armazenados. |
| **Botão "Executar o algoritmo"** | Inicia o processo de esteganografia. |

**Saídas Mencionadas no Código Fonte (`FormPrincipal.class`):**

* `resultado_Texto.png` (Imagem com o texto embutido)
* `resultado_Figura.png` (Imagem com a figura embutida)

#### 2. Esteganografia Reversa (`FormReverso`)

A tela de extração é intitulada **"Esteganografia Reverso"**.

| Componente | Função |
| :--- | :--- |
| **Imagem modificada** | Permite selecionar a imagem esteganografada para extração. |
| **Tamanho do texto** | Campo para informar o tamanho do texto que será extraído. |
| **Botão "Extrair texto"** | Inicia a extração do texto secreto. |
| **Botão "Extrair imagem (imagem será redimensionada)"** | Inicia a extração da imagem secreta. |

**Saídas Mencionadas no Código Fonte (`FormPrincipal.class`):**

* `resultado_FiguraExtraida.png` (Figura extraída)
* `resultado_TextoExtraido.txt` (Texto extraído)

---

### ⚙️ Detalhes da Implementação (`Algoritmo.class` e `Util.class`)

#### `Algoritmo.class`

Esta classe contém a implementação real da esteganografia:

* **`embedText` / `embedImage`:** Responsáveis por modificar os pixels da `BufferedImage` portadora (`imageC`) com os dados da mensagem/imagem secreta (`text` / `imageS`). O processo envolve manipular os valores RGB dos pixels (utilizando `getRGB` e `setRGB`) e a lógica de bits para ocultação.
* **`extractText` / `extractImage`:** Responsáveis por ler os bits modificados dos pixels da imagem esteganografada para reconstruir a informação secreta. A função `extractImage` redimensiona a imagem extraída antes de exibi-la.

#### `Util.class`

Esta classe é usada para manipulação de arquivos e imagens:

* **`openFullImage`:** Abre uma imagem a partir do caminho especificado.
* **`openEmbbededImage`:** Abre e redimensiona a imagem que será embutida.
* **`resize`:** Redimensiona uma imagem para as dimensões padrão (implícito: 50x50).

---
