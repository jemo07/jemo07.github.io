# Exploring FORTH: A Unique Language and Its Functionalities

FORTH, an innovative programming language, is fundamentally a list processor. It leverages an intricate set of commands and an interpreter to systematically process lists of commands. These commands act as individual records, stored in memory within a structure known as a dictionary.

Each command, or 'word' in FORTH parlance, within this dictionary is composed of several fields. Firstly, there's a link field which weaves together the commands, forming the comprehensive dictionary. Secondly, there is a name field, storing the unique name of commands in ASCII. Next is a code field, containing the executable code and any necessary data to perform the specific function for this command. Optionally, a parameter field may be included, carrying additional data required by the command.

The unique construct of link and name fields allows the interpreter to swiftly lookup a command in the dictionary, while the code field furnishes the executable code to perform the function tied to this command. Notably, a FORTH command possesses two representations: an external, ASCII-based name, and an internal token, which invokes executable code stored in the code field. While in many FORTH systems, the token is an address, it can also assume different forms according to the particular requirements of the implementation.

FORTH commands can be classified into two types: primitive and compound. Primitive commands contain machine code in their code fields, whereas compound commands house token lists.

```
+-----------------------------------+           
|        FORTH System               |  
|                                   |
|  +-----------------------------+  | 
|  |        Commands            |  |
|  |                             |  |
|  |   +---------------------+  |  |
|  |   |     Command         |  |  |
|  |   |                     |  |  |
|  |   |   Link  ---> *------|--|  |
|  |   |   Name  ---> "Name" |  |  |
|  |   |   Code  ---> {Exec} |  |  |
|  |   |   Param ---> [Data] |  |  |
|  |   +---------------------+  |  |
|  +-----------------------------+  |
|                                   |
|   +--------------------------+    |
|   |   Text Interpreter       |    |
|   |                          |    |
|   |  Interpreting  <--> Compiling |
|   +--------------------------+    |
|                                   |
|   +--------------------------+    |
|   |   Token Interpreter      |    |
|   +--------------------------+    |
|                                   |
+-----------------------------------+
```

Interpreters in FORTH function on two levels: a text interpreter, also known as the outer interpreter, and a token interpreter or the inner interpreter. The text interpreter processes lists of FORTH commands represented in text, without limitations to the number of commands in a text list. On the other hand, the token interpreter processes lists of tokens embedded in compound commands. Often referred to as the address interpreter, tokens in many FORTH systems are addresses directing to code fields.

The text interpreter operates in two distinct modes: interpreting and compiling. In the interpreting mode, a list of command names is parsed and executed. However, in compiling mode, the list of command names is parsed and the corresponding tokens are compiled into a token list. This token list can be assigned a name, giving rise to a new compound command by creating a new command record in the dictionary.

Herein lies the core of FORTH's power - its compiler. Forth is a FORTH Language Text Compiler that operates in compiling mode. Its purpose is to compile new compound commands, converting a text list of FORTH commands into an equivalent token list. It works by constructing nested token lists one atop another until the final solution is reached in the last token list. This robust process characterizes FORTH's flexibility and efficiency, truly distinguishing it as a unique and powerful programming language.
