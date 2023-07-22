# TypeScript
TypeScript é um superSet de JavaScript. A linguagem do javaScript adicionado de outra funções.
Em typeScript a tipagem não é mais dinâmica. Logo não é possível atribuir um valor de tipagem diferente à uma variável que já foi inicializada com outra tipagem.
TS não é executado por navegadores/node, é necessário converter. Esta conversão não é apenas de linguagem do typescript para javascript, também pode ser de typescript moderno para javascript antigo.
A 'funcionalidade' dele é, ajudar durante a complicação/desenvolvimento, encontrar erros de lógica e tipagem no código. Ele não muda nada no 'runtime' do código. 
Extensão .ts
Instalando:
npm install -g typescript

tsc file.ts -> compila o arquivo em javascript
tsc file.ts --watch ou -w -> Deixa um arquivo sendo "observado" e atualizando a compilação sempre que o arquivo é salvo

tsc --init -> transforma o diretório em um diretório observado por typescript
após isso rodar tsc no terminal compila todos arquivos ts
tsc --watch -> observa todo o diretório por salvamentos e compilando novamente

### Tsconfig.json
Muitas das configurações comentadas, apesar de comentadas, já possui valores padrões e estão ativas. O uso delas são em situações específicas.
sourcemap -> Adiciona um arquivo map que fornece um documento de analise para o navegador. Útil para debugar código vendo o processo de leitura do códio pelo navegador em Sources. Muito bom com a extensão do chrome para debugar no vscode.
outdir -> usado para especificar uma pasta à qual será salvo os arquivos.js compilados.
removeComments -> remove os comentários durante a compilação
"noEmitOnError": true -> não cria os arquivos js caso haja erro no ts

Em strict como padrão tudo está true. Define os padrões do que é permitido ou não. Por exemplo se os parâmetros de uma função deve ou não possuir tipagem.

Em aditional checks é bom ligar unUsedLocals, unUsedParam e noImplicitReturns

Algumas configurações extras podem ser adicionadas após o primeiro valor, adicionando uma vírgula no final do objeto e adicionado a chave/valor desejado.
"excluse": "node_modules"    Exclui um arquivo ou pasta da compilação automática via tsc --init e tsc ou tsc -w, por padrão já tem node modules definido
"inclue": "arquivo.ts"       Por padrão já vem com todos arquivos, tendo que especificar todos caso queira especificar um arquivo
"files": "diretório"         Mesma coisa mas com diretórios

## Tipos
<details>
  <summary>

  ### Types cores (Sempre minúsculas)
  </summary>

  **number**
  **string**
  **boolean** (Sem truthy or falsy)
  **object**
  **array**
  **tuple**
  **Enum**
  **Any** (Praticamente perde os benefícios do uso do TS)
  **Void** (Ausente de tipo)

  ex.
  function (n1: number, n2: number) {
  }

  **Dica:** Em objetos e arrays, o ideal é dexar o typescript definir os tipos conforme os elementos são atribuidos
  const object: {
    CPF: number;
    nome: string;
    empregado: boolean;
  } = {
    CPF: 0000000,
    nome: 'Pedro',
    empregado: true
  }

  ### Tuple
  const person [string, number | string] = ['Pedro', 20];

  ### Enum
  Cria e da um valor iniciando em 0 ou a partir do valor explicito no anterior, para os elementos atribuidos. ADMIN = 0, READ_ONLY = 5, AUTHOR = 6.
  enum Role { ADMIN, READ_ONLY = 5, AUTHOR };

  ### Type Alias
  É um tipo que pode ser um ou outro

  type Combinados = {
    number | string
  }

  ### Void
  É a tipagem dada a uma função que não possui retorno.
  Apesar do retorno dela ser definido com undefined...

  ### Function types
  let combine: (a:number, b:number) => number;

  ### Unknown
  Quase a mesma coisa de any, mas ele ainda é verificado. Seria um any mantendo a verificação se o tipo esperado é compatível com o tipo armazenado em uma variável com unknown

  ### Never
  Uma função que retorna nada devido uma pausa/break/error ou que fica em um loop infinito. Uma função pode ter o retorno de tipo never


  class Department {
    private name: string;

    public constructor (n: string) {
      this.name = n;
    }
  }

  class Product {
    title: string;
    price: number;
    private isListed: boolean;
  
    constructor(name: string, pr: number) {
      this.title = name;
      this.price = pr;
      this.isListed = true;
    }
  }
  const accounting = new Department('Accounting');
  extends aproveita uma classe já criada e usa como parte na criação de uma nova mas com adições. É necessário usar o super.


  private -> deixa privado sendo acessado apenas pela própria classe
  public
  protected -> deixa privado mas pode ser acessado tanto pela própria classe como por classes que usem-a como extensão
</details>

## Classes & Interfaces
<details>
  <summary>

  ### Classes
  </summary>

  ### O que são:
  Uma classe é uma entidade abstrata que encapsula dados e comportamentos relevantes para um conceito específico dentro de um programa. Ela permite que você defina um novo tipo de dado personalizado, permitindo que crie instâncias desse tipo ao longo do código.

  ***Informações Basicas Sobre Classes***
  -É uma construção da programação orientada a objetos (POO) e é usada para criar objetos.
  -Pode conter implementações de métodos, ou seja, o código real que define o comportamento desses métodos.
  -Permite criar instâncias através do operador new.
  -Pode herdar propriedades e métodos de outra classe (herança).
  -É possível aplicar modificadores de acesso (public, private, protected) para controlar o acesso aos membros da classe.

  **EX:**

  class teste {
    mensagem: string
    numero: number

    constructor (escrita: string, numero: number){
        this.mensagem = escrita
        this.numero = numero
    }

    saida(){
        console.log(`Olá, ${this.mensagem}, ${ this.numero}`)
    }
  }
  const Teste1 = new teste("Testando",123)
  Teste1.saida()
  

</details>

<details>
  <summary>

  ### Interface
  </summary>
  
  ### O que são:
  Uma interface é uma especificação para um tipo de objeto, definindo quais propriedades e métodos o objeto deve ter. Isso permite que o TypeScript faça a verificação de tipos em tempo de compilação, garantindo que os objetos sigam as regras definidas pela interface.

  ***Informações Basicas Sobre Interfaces***

  -Uma interface é um contrato que define a estrutura de um objeto, descrevendo quais propriedades e métodos devem estar presentes no objeto.
  -É uma forma de definir tipos personalizados, mas não contém implementações de métodos.
  -Não pode ser instanciada diretamente, pois não é uma construção para criar objetos.
  -É usada principalmente para declarar a forma que um objeto deve ter, garantindo que certos atributos e métodos estejam presentes.
  -Pode ser implementada por classes (uma classe pode "assinar" um contrato representado por uma interface).


  **EX:**

  interface Testei {
    mensagem: string
    numero: number
  }

  const teste2: Testei = {
    mensagem: "Testando",
    numero: 123
  }

console.log(`${teste2.mensagem} ${teste2.numero}`)

</details>

## Genéricos
<details>
  <summary>

  ### O que são?
  </summary>

</details>

## Decoradores
<details>
  <summary>

  ### Decoradores O que são?
  </summary>

</details>



É preciso instalar node antes para utilizar!
[TypeScript Download](https://www.typescriptlang.org/)


