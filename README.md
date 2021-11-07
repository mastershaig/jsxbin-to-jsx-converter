# Introduction to JSXBIN to JSX Converter
JSXBIN is a binary format of JSX, which is a superset of JavaScript made by Adobe for automating certain tasks in Adobe products such as Photoshop. Sometimes it's useful to decode and read JSXBIN files but since there's no official decoder available, here is an alternative instead.

# Usage
1. Download the [latest version from the releases page](https://github.com/mastershaig/jsxbin-to-jsx-converter/releases)
2. Extract the converter
2. Run jsxbin_to_jsx on your command line using the following syntax:

```
jsxbin_to_jsx [-v] JSXBIN JSX
Flags:
-v print tree structure to stdout
```

Example:

```
jsxbin_to_jsx encoded.jsxbin decoded.jsx
```

The converter automatically formats the code using [JsBeautifier](https://github.com/ghost6991/Jsbeautifier).

# Debugging
To view the parse tree created by the decoder use the -v flag:

```
jsxbin_to_jsx -v encoded.jsxbin decoded.jsx > debug.txt
```

Decoding the following code:

```javascript
var test = 5;
if (test > 5) {
        doSomething();
}
```

translates into the following parse tree:

```
StatementList
    ExprNode
        AssignmentExpr
    IfStatement
        StatementList
            ExprNode
                FunctionCallExpr
                    IdNode
        BinaryExpr
            IdRefExpr
```

# Tests
The Tests-Project contains one single test. This test decodes all jsxbin-Files found in the testfiles folder comparing them with their jsx-File equivalent, also found in the same folder.

# Feedback
If you encounter any problems or have any feedback, please open an issue.
