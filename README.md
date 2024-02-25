# Clean Code
Curso ministrado pelo Diego Fernandes da **Rocketseat**.

## Fundamentos
Clean Code é um conceito para programoderes manter um cógido legível, de fácil manutenção e confiável, assim, tornando o código limpo. Lembrando que clean code técnico e diferente da prática, porque para nascer um código limpo antes passamos por muitos sujos, e um dos maiores desafios é manter um código limpo trabalhando em equipe onde o código é maior.

Não confunda Clean Code com arquitetura de pasta ou código pequeno, pelo contrário, o clean code é o crescimento do seu projeto, mostrar que ele está maior, e que mesmo assim as pessoas conseguem ler e dar manutenção com confiança. Pois é fácil uma pessoa escrever um código limpo para ela mesma.

Assim devemos lembrar que clean code NÃO é:
* Manual
* Estrutura de pasta
* Código pequeno
* Arquitetura
* Performance

> Clean code é o que você vive!
<br>

Princípios:
1. Testes automatizados
2. Revisão
3. Refatoração
4. Simplicidade (Keep It Simple Stupid)
5. Iterações curtas (pequenas adições)

> Simplicidade e boas escolhas. Mantenha seu código simples e idiota, só traga complexidade se realmente for necessário e benéfico para o código. Não pense em otimizações e soluções para problemas que não existem. Adicione as coisas conforme elas tiverem necessidade!

## Código limpo com JavaScript
### Nomeclatura de variáveis
1. Evite diminutivos e abreviações
2. Evite nomes genéricos, os nomes das variáveis devem ter significado
3. Quando o dado for booleano o nome da variável deve ser escrito como uma pergunta
4. Sempre nomear a variável pela causa e não pelo efeito que ela vai ter na interface

### Código em inglês
O código tem que ser em inglês, independente da "padronização" da equipe, pois um código que não está em inglês não é acessível. Misturar dois idiomas deixa o código difíl de entender, então ele se torna sujo.

### Regras em condicionais
1. Evite sempre que possível as negações dentro de ifs
2. Early return vs else
```
// dentro do JavaScript quando se usa o return dentro de uma função, o restante do código não será execultado, então não tem porque usar o else

function isUserOlderThan18Years(user) {
    if(user) {
        return {error: true}
    }
    return user.age >= 18
}

// usa-se o else quando o early return não é fácilmente visto no código, ou seja, quando se tem muitos ifs e retuns encadeados
```
3. Evite sempre que possível condicionais aninhadas (uma dentro da outra)

> Uma condicional é como uma linha do tempo dentro do código, se tem um if dentro de outro, é como se outra linha do tempo se abrisse dentro daquela já existente, tornando o código confuso.

### Parâmetros e desestruturação
Desestruturação é basicamente repartir um objeto ou vetor em variáveis.
```
function createUserController(data) {
    usersRepository.create(data)
}

// desestruturação
function createrUserController(data) {
    const {name, email, password} = data

    usersRepository.create ({
        name, email, password
    })
}
```

Práticas: 
1. Sempre que possível enviar e receber parâmetros nomeados
2. Prefira receber nas funções objetos ao invés de multiplos parâmetros

### Números mágicos
Números mágicos são cálculos que colocamos no codigo que muitas vezes não são fáceis de ser entendidos por uma pessoa que nunca deu manutenção ou não sabe o contexto.

Casos de uso:
* Simples
```
setTimeout(() => {}, 2592000000)

// reescreva fazendo as operações no código
setTimeout(() => {}, 1000 * 60 * 60 * 24 * 30)

// para ficar mais claro crie uma variável ou simplesmente coloque um comentário
const trintaDias = 1000 * 60 * 60 * 24 * 30
setTimeout(() => {}, trintaDia)
```
* Avançado
```
function calculateDiscount(price, discountAmount){
    // retorna desconto
}

// formato do número
function calculateDiscount(priceInCents, discountAmountInPercent){
    // retorna desconto
}
```

### Comentários vs documentação
O código pode conter comentários, desde que, estes não descreva linha por linha, porque se torna uma coisa redundante. Geralmente os comentários são usados como alertas para futuras pessoas que forem olhar o código, destacando as razões que justificam a abordagem adotada.
```
// o código foi escrito assim porque a biblioteca X ainda não suporta Y
// link do repositório
```
Já a documentação deve ser a descrição precisa de um sistema de software, seja uma implementação ou configuração.

### Evite syntactic sugars
Syntatic sugars é a sintaxe dentro de uma linguagem de programação projetada para tornar as coisas mais fáceis de ler ou expressar, lembrando que isso é uma característca de determinadas linguagens. Mas cuidado, evite syntactic sugars até o momento em ele não atrapalhe a sua produtividade e a legebilidade do seu código. 
```
// errado mas funciona, porém não é legivel para pessoas que vinheram de outra tecnologia

const numberInString = "12373"
const number = +numberInString 

// correto
const numberInString = "12373"
const number = Number(numberInString)
```
O artigo do Lucas Santos [As más práticas mais comuns no JavaScript](https://blog.lsantos.dev/mas-praticas-javascript/), aborda algumas exemplos de "más" práticas no JavaScript.

Boas práticas com syntactic sugars:
* [Artigo Javascript Syntactic Sugar](https://giuliacajati.medium.com/javascript-syntactic-sugar-157217c4faab) 
* [Artigo Syntactic Sugar and Modern JavaScript.](https://medium.com/@teamtechsis/syntactic-sugar-and-modern-javascript-b0293ff28311#:~:text=What%20is%20syntactic%20sugar%20exactly,alternate%2C%20more%20verbose%2C%20form.)