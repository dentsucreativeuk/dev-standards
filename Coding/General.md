## Consistency
 - Where practicable, remain consistent with the host code, even if it does not adhere to the below standards. It is the aim of this document for all code we produce to follow the same standard so this rule should only apply to third party libraries and very old code.
 - If you adopt a style not specified within these guidelines, remain consistent throughout that language when used within your document. Such examples of non-specified consistency are:
	- String quoting (single vs double)
	- Comma dangling, comma placement
	- Spacing within parentheses
	- Naming conventions

## Refactoring
It is not Whitespace policy to spend inordinate amounts of time refectoring old code that does not follow the standards. Code will eventually be replaced and it is not time-effective to create work consisting of purely syntactical changes.

### Exceptions
1. If the code requires refactoring due to a known and replicated issue, then syntax improvements can be crucial to improving the code and are welcomed.

## Spacing & indentation
Unless otherwise stated in the language-specific guidance, all indentation **must** be with tabs. A single tab per level of indentation should be used.

Lines should be spaced sensibly with readability in mind. Individual lines **must not** have whitespace after the last visible character.

Files **should not** end with an empty line.

Individual lines **should not** exceed 80 characters in length, and **must not** exceed 100 characters in length.

### Exceptions
1. Language-specific guidance may override the guidance in this document. Please read the standards document for the language you intend to code in, if it exists.

2. If a file is using another intentation rule and was not created by our team the indentation used within the file should not be changed.