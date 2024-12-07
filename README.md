
| strumento | versione |
| --------- | -------- |
| JFlex     | 1.9.1    |
| CUP       | 11b-20160615 |
| Java      | 8        |


Let's consider the following  TOML-style configuration file 

```
import <../glob/file1.cnf>

[nomesez1]
#this is a comment
var1=3
var2="don't say cat"

[nomesez2]
miao=true
var1=$nomesez1.var2

[nomesez3]
inherit nomesez1
inherit nomesez2
miao=false

```

We have implemented a `Parser` (with relative `Lexer`) that given a configuration file of the above kind, it builds a data structures containing values to be associated with each variable of each section. Moreover, We have built the following features:  

* Remove a section or a single binding without leaving non-existent references, 
* Given a section and a name return the associated value by traversing a chain of references/`inherit` directives
* Resolve all recursive`inherit`/assignments/import
* a `pretty-printer` of the data structure that serializes it into correct syntax for the parser. 

To compile the sources run the `make` command.
To run a demo use the `make demo` command.
