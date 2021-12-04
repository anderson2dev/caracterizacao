# Caracterização linguagem elixir

## Caracterização

### Aspectos Gerais

Linguagem de programação funcional criada para criar aplicações escaláveis. O elixir roda na maquina virtual erlang, conhecidada pela baixa latência, sistemas distribuidos e tolerantes a falha, podendo ser utilizada no desenvolvimento web, de aplicações embarcadas e processamento multimedia.



#### Estruturas de controle

A linguagem elixir possui as seguintes estruturas de controle:

**case**:  A estrutura de controle de fluxo case permite que a comparação de um valor com múltiplos outros até que consigamos encontrar algum que  coincida com ele

```shell
iex> case {1, 2, 3} do
...>   {4, 5, 6} ->
...>     "This clause won't match"
...>   {1, x, 3} ->
...>     "This clause will match and bind x to 2 in this clause"
...>   _ ->
...>     "This clause would match any value"
...> end
"This clause will match and bind x to 
```

**cond**: Enquanto case é útil quando nós precisamos verificar se um valor coincidi com uma sequencia de outros valores, as vezes necessitamos apenas  checar diferentes condições e encontrar a primeira que não é interpretada como *false* ou *nil* nesses casos nós utlizamos a  estrutura **cond**

Exemplo: 

```shell
iex> cond do
...>   2 + 2 == 5 ->
...>     "This will not be true"
...>   2 * 2 == 3 ->
...>     "Nor this"
...>   1 + 1 == 2 ->
...>     "But this will"
...> end
"But this will"
```

**if**:  Além de  *case* e *cond*, elixir também proporciona  os macros *if* e *unless*  que são especialmente úteis  quando se é necessária apenas a validação de uma condição .

```shell
iex> if true do
...>   "This works!"
...> end
"This works!"
iex> unless true do
...>   "This will never be seen"
...> end
nil
```

Também há o suporte a claúsulas *else* 

Exemplo:

```shell
iex> if nil do
...>   "This won't be seen"
...> else
...>   "This will"
...> end
"This will"
```

---

#### Tipos de dados

A linguagem elixir possui como tipo de dados:

<table style="border: 1px solid black;">
    <thead>
        <th>
            Nome
        </th>
        <th>
            Descrição
        </th>
        <th>
            Exemplo
        </th>
    </thead>
    <tbody>
        <tr>
            <td> Números </td>
            <td> Inteiros e números de ponto flutuante  são representados como uma sequência de digitos  que pode ser separada por underline para proprósitos de redigibilidade, números inteiros nunca possuem um <strong> . </strong> na sua representação  enquanto números de ponto flutuante possuem o <strong> .  </strong> e pelo menos um outro digito após o ponto </td>
            <td>
                <code>
                 12
                 22.22
                </code>
            </td>
        </tr>
         <tr>
            <td> Atómos </td>
            <td> 
                Podendo ser envoltos em <em> " "</em> ou começarem com o prefixo <em> : </em> atómos são constantes cujo o seu valor é o próprio nome, eles são especificamente úteis para enumerar valores distintos ou para demonstrar o estado de uma operação
            </td>
            <td>
                <code> 
                    :ok 
                    :error
                    :orange
                    :smartwatch
                    :orange === :watermelon
                </code>
            </td>
        </tr> 
         <tr>
            <td>  Strings </td>
            <td> Strings na linguagem elixr são representadas usando o padrão UTF-8 e são delimitadas por <em> "" </em>, elixir também suporta interpolação de strings </td>
            <td>
                <code>
                name = "joao"
                "I'm a string #{name}"
                // I'm a string joao
                </code>
            </td>
        </tr>
         <tr>
            <td> Listas de caracteres (charlists) </td>
            <td> Diferentemente de strings,listas de caracteres são delimitadas por  <strong> single quotes</strong>(<em> ' '</em>) e são representadas como uma lista de caracteres no padrão ascii</td>
            <td>
             <pre> 
                iex> 'hełło'
                [104, 101, 322, 322, 111]
                iex> is_list('hełło') 
                true
             </pre>
            </td>
        </tr>
         <tr>
            <td> Listas, tuplas e binários </td>
            <td> </td>
        </tr>
         <tr>
            <td> Mapas e listas chave valor </td>
            <td> São estruturas de dados associativas que permitem a associação de  um dado (ou conjunto de dados)  à uma chave  </td>
        </tr>
         <tr>
            <td> structs </td>
            <td> Permitem a criação de tipos de dados mais complexos como por exemplo um tipo de dado pessoa, são extensões criadas em cima de maps </td>
        </tr>
    </tbody>
</table>

#### Ortogonalidade

#### Frameworks

1. [Phoenix framework](https://www.phoenixframework.org/)
1. [Nerves](https://www.nerves-project.org/)
1. [Sugar](https://sugar-framework.github.io/)

Fatores:
- Simplicidade
- Ortogonalidade
- Estruturas de controle
- Estruturas e tipos de dados
- Aspectos sintáticos


#### Redigibilidade