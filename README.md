## Instructions

```text
1. Fork this repository.
2. Download Graphiz installer from https://graphviz.org/download/
3. Install the required packages:
   pip install lark graphviz
```
## Solutions

## 1.EBNF for simple  if-else if statement
```text
<preprocessor>::= "#include<iostream>" <directive>
<directive>::= "using namespace std;" <function>
<function>::= "int main () {" [<assignment> | <statements> | <return statement>]
<assignment>::= <type> <expression> ";"
<type>::= "int" | "float" | "bool" | "string"
<statements>::= <statement>
<statement>::= ["if" <condition>"{" <expression> ";" "}"| "else if" <condition> "{" <expression> ";" "}" | "else" "{" <expression> "}"]
<output>::=  "cout" "<<" <string> "<<" "endl" ";"
<expression>::= [<arithmetic> | <output>]
<arithmetic>::= (<variable> <operator> <term>";")
<operator>:="+" | "-" | "/" | "*" 
<condition>::= "("<variable> <comparator> <number> ")"
<comparator>::== "==" | "!=" | "<" | ">" | "<=" | ">=" 
<term>::= <number>
<variable>::= <letter> | <variable><letter>
<number>::= <number><digit> | <digit>
<string>::= ["<variable> is less than <number>" | "<variable> is equal to <number>" | "<variable> is greater than <number>" ]
<letter>::= "a" | "b" | "c" | "d" | "e" | .... |"A"|"B"|"C"|"D"|....|
<digit>::= "0" | "1" | "2" | "3" | "4" | "5" | .... |
<return statement>::= return 0;
```

## 2. Parsing according to the grammar rules
This parsing is divided into several parts: the main function and its statements and a return statement.
The full view of the parsing in `txt` file is uploaded in this repository.

```text
<preprocessor>::= #include<iostream> <directive>
                                          |
                           using namespace std; <function>
                                                    |
                                       int main () { <assignment> |       <statements> | <return_statement> }
                                                           |                    |                  |
                                                  <type> <expression>;      <statement>         return 0;
                                                     |        |                 |
                                                  int   <arithmetic>        <statement>
                                                           |                     |
                                              <variable> <operator> <term>;  <statement>
                                                     |       |       |      
                                                <letter>     -   <number>   
                                                     |               |      
                                                     x       <number><digit>
                                                                     |     |
                                                                  <digit>  0;
                                                                     |
                                                                     1


<statement> ::= if <condition> {                     <expression>; }
                        |                                   |
        (<variable> <comparator> <number>)               <output>
             |          |            |                      |
         <letter>       <       <digit>           cout << <string> << endl;
             |                      |                       |
             x                      5           "<variable> is less than to <number>"    
                                                      |                         |
                                                  <letter>                   <digit>
                                                      |                         |
                                                      x                         5


<statement> ::= else if <condition> {          <expression>; }
                                |                     |
            (<variable> == <number><digit>)         <output>
                 |           |       |                 |
             <letter>     <digit>    0        cout << <string> << endl;
                 |                                      |
                 x                            "<variable> is equal to <number>"
                                                    |                     |
                                                  <letter>   <number><digit>
                                                     |          |       |
                                                     x       <digit>    0
                                                     |
                                                     1        

<statement> ::= else { <expression> }
                            |
                         <output>
                          |
           cout << <string> << endl;
                      |
      "<variable> is greater than <number>"
            |                        |
         <letter>                 <digit>
             |                       |
             x                       5



```
## 3. Visual Representation 
This activity uses the following libraries:
1. `lark-parser`, a Python toolkit for parsing all context-free languages. It is capable of parsing almost any programming languages.
[🌐 Visit this repository](https://github.com/username/repository-name) for more `lark-parser` details.
2. `graphviz`, an open source graph visualization software. It is a wat of representing structural information as diagrams of abstract graphs and networks.
[🌐 Visit this website](https://graphviz.org/) for more `lark-parser` details.

The output is as follows:

<p align="center">
  <img src="image_url_or_path" width="300" />
</p>


   


