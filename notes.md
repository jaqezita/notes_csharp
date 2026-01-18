# Treinamento Microsoft .NET

## Objetivos
- Implementar **classes**, **propriedades** e **métodos**.

## Tópicos

- Diferenças entre **Programação Estruturada** e **Programação Orientada a Objetos (POO)**.
- Principais conceitos da POO: **Abstração**, **Encapsulamento**, **Herança** e **Polimorfismo**.
- Benefícios da POO: reutilização de código, modularidade e flexibilidade.
### Programação Estruturada
Baseia-se em procedimentos e funções para organizar o código. O foco está na sequência de comandos e no fluxo de controle.  
**Exemplos**: C, Pascal.

### Programação Orientada a Objetos (POO)
Baseia-se em objetos que encapsulam dados e comportamentos. Promove a reutilização de código e a modularidade.  
**Exemplos**: C#, Java.

---

### Conceitos e Benefícios da POO

- **Abstração**: Permite ocultar detalhes complexos e mostrar apenas as funcionalidades essenciais de um objeto.
- **Encapsulamento**: É o processo de agrupar atributos e métodos dentro de um objeto, protegendo seus dados. Ele restringe o acesso direto a esses dados, permitindo que sejam manipulados apenas por meio de métodos específicos, garantindo maior segurança e controle sobre o comportamento do objeto.
- **Herança**: Permite que uma classe herde propriedades e métodos de outra classe, promovendo a reutilização de código.
- **Polimorfismo**: Permite que objetos de diferentes classes sejam tratados como objetos de uma classe comum, facilitando a flexibilidade e a extensibilidade do código.

### C#

- Forte tipagem estática.

    - Tipos internos: `int`, `float`, `double`, `char`, `bool`.

    - Tipos personalizados: `class`, `struct`, `enum`, `interface`, `record`.


### Sistema de Tipo Comum (CTS)

- Suporta herança entre tipos (tipos derivados e tipos base).

- Tipos derivados herdam métodos, propriedades e membros do tipo base.

- Permite herança em múltiplos níveis (hierarquia de herança).

- Todos os tipos, inclusive os tipos primitivos como `System.Int32` (palavra-chave C#: `int`), derivam de `System.Object` (palavra-chave C#: `object`).

- Garante uma hierarquia de tipos unificada no .NET.

- Cada tipo é classificado como tipo de valor ou tipo de referência.

- **Tipos de valor:** definidos com `struct` e incluem os tipos numéricos internos.

- **Tipos de referência:** definidos com `class` ou `record`.

- Tipos de valor e de referência possuem regras diferentes em tempo de compilação e comportamentos distintos em tempo de execução.

## A ilustração a seguir mostra a relação entre tipos de valor e tipos de referência no CTS.

                                           +-----------------------------------------------------------+
                                           | Reference Types                                           |
                                           |                                                           |
                                           |                  +-------------------+                    |
                                           |                  |   System.Object   |                    |
                                           |                  +---------^---------+                    |
                                           |                     |      |                              |
                                           |                     |      |  All Base Class Library      |
                                           |   +---------+---------+    |  classes and interfaces,     |
                                  +--------|---| System.ValueType  |    |  including:                  |
                                  |        |   +-------------------+    |                              |
                                  |        |        |                   |     +-------------------+    |
                                  |        |        |                   |---- |   System.String   |    |
                                  |        |      +--------------+      |     +---------^---------+    |
                                  |        |      |  System.Enum |------|               |              |
                                  |        |      +--------------+      |     +---------+---------+    |
                                  |        |        |                   |-----|   System.Array    |    |
                          +----------------|--------+                   |     +---------^---------+    |
                          |       |        |                            |                              |
                          |       |        |     +----------------+     |                              |
                          |       |        |     |  User-defined  |     |                              |
                          |       |        |     |   classes and  |-----|                              |
                          |       |        |     |   interfaces   |     |                              |
                          |       |        |     +----------------+     |                              |
                          |       |        |                            |                              |
                          |       |        |                            |                              |
                          |       |        |                            |     ...Etc.                  |
                          |       |        +-----------------------------------------------------------+
                          |       |                        
        +----------------------------------------------------------------+
        | Value Types     |       |                                      |
        |                 |       |                                      |
        |                 |       | All structs, including               |
        |                 |       | built-in numeric types               |
        |                 |       |                                      |
        |                 |       |     +-------------------+            |
        |             All enums   |-----|   System.Int32    |            |
        |                         |     +---------^---------+            |
        |                         |                                      |
        |                         |     +---------+---------+            |
        |                         |-----|  System.Boolean   |            |
        |                         |     +---------^---------+            |
        |                         |                                      |
        |   +---------------+     |                                      |
        |   | User-defined  |     |                                      |
        |   | structs       |-----|                                      |
        |   +---------------+     |                                      |
        |                         |     ...Etc.                          |
        +----------------------------------------------------------------+

##

### Classes, Structs e Records no CTS

- Classes, structs e records são construções fundamentais do sistema de tipos do .NET.

- Representam estruturas que agrupam dados e comportamentos como uma unidade lógica.

- Seus membros incluem propriedades, métodos, campos e outros.

### Instâncias e Tipos

- class, struct ou record funcionam como blueprints.

- O nome (ex: Person) define o tipo.

- Cada variável criada desse tipo é uma instância (objeto).

- Múltiplas instâncias podem existir com valores diferentes.

### Classes

- São tipos de referência.

- A variável armazena apenas a referência ao objeto na memória.

- Ao copiar a variável, ambas apontam para o mesmo objeto.

- Alterações em uma variável afetam a outra.

- Usadas para modelar comportamentos mais complexos.

- Normalmente armazenam dados mutáveis.

### Structs

- São tipos de valor.

- A variável armazena os dados reais.

- Ao copiar, os dados são duplicados.

- Alterações em uma cópia não afetam a outra.

- Indicadas para estruturas pequenas.

- Normalmente armazenam dados imutáveis.

### Records

- Podem ser:

    - record class → tipo de referência

    - record struct → tipo de valor

- Suportam igualdade por valor.

- São usados principalmente para representar dados imutáveis.

- Possuem membros gerados automaticamente pelo compilador.


##

| Característica      | Class                           | Struct                         | Record                            |
| ------------------- | ------------------------------- | ------------------------------ | --------------------------------- |
| Categoria           | Tipo de referência              | Tipo de valor                  | Pode ser referência ou valor      |
| Declaração          | `class`                         | `struct`                       | `record class` ou `record struct` |
| Armazenamento       | Heap (referência)               | Stack/Inline (valor direto)    | Depende do tipo                   |
| Cópia de variável   | Copia a referência              | Copia os dados                 | Depende se é class ou struct      |
| Igualdade padrão    | Referência                      | Valor campo a campo            | Valor por padrão                  |
| Mutabilidade típica | Mutável                         | Geralmente imutável            | Geralmente imutável               |
| Uso comum           | Lógica complexa e objetos ricos | Estruturas pequenas            | Modelos de dados                  |
| Herança             | Suporta herança                 | Não suporta herança de classes | `record class` suporta herança    |
| Performance         | Mais flexível                   | Mais leve                      | Otimizado para dados              |

##

### Use class para lógica e comportamento complexo.

### Use struct para pequenos conjuntos de dados.

### Use record para representar dados imutáveis com igualdade por valor.