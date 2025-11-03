# Lexical Analyzer

[![Language: C](https://img.shields.io/badge/language-C-blue.svg)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Stability: Stable](https://img.shields.io/badge/stability-stable-brightgreen.svg)]()
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)]()

**A lightweight C tokenizer for lexical analysis in compilers and interpreters**

## About

This project implements a simple yet effective tokenizer in C, capable of analyzing input text files and identifying various tokens based on predefined patterns. The tokenizer recognizes arithmetic operators, parentheses, integer literals, and several other token categories, marking unrecognized tokens as lexical errors. This utility is particularly useful for lexical analysis in compilers or interpreters.

## Features

- **Token Recognition**: Identifies arithmetic operators (+, -, *, /), parentheses, integer literals, identifiers, and more
- **Error Handling**: Marks unrecognized tokens as lexical errors with detailed error reporting
- **Comprehensive Classification**: Categorizes tokens into various token types via the TokenCategory enumeration
- **File-based Processing**: Processes input files and generates output with tokenization results
- **PCRE Support**: Uses Perl Compatible Regular Expressions (PCRE) for robust pattern matching

## Project Files

- `tokenizer.c`: The main program source file containing the tokenization logic
- `tokenizer.h`: Header file with constants, function declarations, and TokenCategory enumeration
- `unix_input.txt`: Sample input file without errors for testing
- `unix_input_errors.txt`: Sample input file with intentional errors for error handling testing
- `output_with_tokens.txt`: Expected output from processing unix_input.txt
- `output_errors_with_tokens.txt`: Expected output from processing unix_input_errors.txt

## Prerequisites

- GCC compiler
- PCRE (Perl Compatible Regular Expressions) library
  - Ubuntu/Debian: `sudo apt-get install libpcre3-dev`
  - macOS: `brew install pcre`

## Installation & Usage

### Compilation

Make sure you are in the project directory, then compile using:

```bash
gcc -o tokenizer tokenizer.c -lpcre
```

To compile with warnings enabled:

```bash
gcc -Wall -o tokenizer tokenizer.c -lpcre
```

**Note**: The code compiles without warnings!

### Running the Tokenizer

Execute the compiled tokenizer with an input file and specify an output file:

```bash
./tokenizer unix_input.txt output_test.txt
./tokenizer unix_input_errors.txt output_test.txt
```

### Verification

After running the tokenizer, compare your output files to the expected outputs:

```bash
diff output_test.txt output_with_tokens.txt
diff output_test.txt output_errors_with_tokens.txt
```

The tokenizer should correctly categorize each token and handle lexical errors for unrecognized symbols.

## API Documentation

### Token Categories

The `TokenCategory` enumeration defines all recognized token types:

```c
typedef enum {
    TOKEN_PLUS,          // + operator
    TOKEN_MINUS,         // - operator
    TOKEN_MULTIPLY,      // * operator
    TOKEN_DIVIDE,        // / operator
    TOKEN_LPAREN,        // ( left parenthesis
    TOKEN_RPAREN,        // ) right parenthesis
    TOKEN_INTEGER,       // Integer literals (e.g., 123)
    TOKEN_IDENTIFIER,    // Variable/identifier names
    TOKEN_EQUALS,        // = operator
    TOKEN_SEMICOLON,     // ; statement terminator
    TOKEN_ERROR          // Unrecognized/lexical error tokens
} TokenCategory;
```

### Key Functions

**tokenize(const char *input, const char *output)**
- Main tokenization function that processes input file and writes results to output file
- Parameters:
  - `input`: Path to input file
  - `output`: Path to output file
- Returns: Status code indicating success or failure

**categorize_token(const char *token)**
- Determines the token category for a given token string
- Uses regex patterns to match token types
- Returns: Appropriate TokenCategory enum value

## Test Files & Output Demonstrations

Test your implementation using the provided files:

- [Test Input (No Errors)](./unix_input.txt)
- [Test Input (With Errors)](./unix_input_errors.txt)
- [Expected Output (No Errors)](./output_with_tokens.txt)
- [Expected Output (With Errors)](./output_errors_with_tokens.txt)

## Technologies

- **Language**: C
- **Regex Engine**: PCRE (Perl Compatible Regular Expressions)
- **Use Cases**: Compiler design, interpreter development, lexical analysis

## Topics

`tokenization` `nlp` `compiler` `lexical-analysis`

## Authors

- **Dagmawi Negatu** (d-negatu)
- **Darwin Bueso Galdamez** (DarwinBueso01)

## Date of Submission

March 17, 2024

## License

MIT License

## Support

For inquiries or further assistance, please contact the authors or open an issue in the repository.
