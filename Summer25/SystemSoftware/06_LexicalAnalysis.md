# Lexical Analyzer
THe purpose of the scanner is to decompose the source program into its elementary symbols or **tokens.**
## Process of a working lexical analyzer
1) Read input one character at a time.
2) Group characters into lexical units.
3) Remove white spaces, comments and control characters.
4) Encode lexical units into token types.
5) Detect errors and generate error messages.

The following stream of characters is read in by the scanner and the translated into a stream of tokens in order to ease the task of the **Parser.**
- Assume you have the following line:
	- `\tfarenheit   :=32+celsious*1.8;\n   /*Hello*/`
- The scanner eliminates white spaces, comments, and control characters to parse:
	- `[id,1][:=][int, 32][+][id,2][*][int,1.8][;]`
	- `02 fahrenheit 08 03 32 12 02 celsious 09 03 1.8 17`

### Lookahead:
This is the idea of looking ahead before checking if you have a keywork/identifier
- For Example:
	- `\t`
	- If you were currently on the `\` char then you world first look ahead to the next char (`t`) before assigning the identifier to the `\t` within the parser.

# Designing a scanner
To design a scanner you must use the following steps:
1) Define the token types (internal representation)
2) Create tables with initial values
	1) Reserved words name table
	2) Special symbols table
	3) External name table (symbol table)x