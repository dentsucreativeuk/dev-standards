# General coding standards
> Part of [Coding](/Coding/Index.md)

## Consistency
 - Where practicable, remain consistent with the host code, even if it does not adhere to the below standards. It is the aim of this document for all code we produce to follow the same standard so this rule should only apply to third party libraries and very old code.
 - If a style  not specified within these guidelines is to be adopted, it should remain consistent throughout that language when used within a project. Such examples of non-specified consistency are:
	- String quoting (single vs double)
	- Comma dangling, comma placement
	- Spacing within parentheses
	- Naming conventions

## Refactoring
It is not our policy to spend inordinate amounts of time refactoring old code that does not follow the standards. Code will eventually be replaced and it is not time-effective to create work consisting of purely syntactical changes.

### Exceptions
1. If the code requires refactoring due to a known and replicated issue, then syntax improvements can be crucial to improving the code and are welcomed.

## Spacing & indentation
Unless otherwise stated in the language-specific guidance, all indentation **must** be with tabs. A single tab per level of indentation should be used.

Lines should be spaced sensibly with readability in mind. Individual lines **must not** have white space after the last visible character.

## Line length
Individual lines **should not** exceed 80 characters in length, and **must not** exceed 120 characters in length.

### Exceptions
1. The exception to the hard 120 character line length limit is when creating Markdowno or plain-text documentation for applicable projects.

## File endings
Text files **must** end with an empty line, ensuring that the last line with visible characters ends with a line-break character.

### Exceptions
1. Language-specific guidance may override the guidance in this document. Please read the standards document for the language being written, if it exists.

2. If a file is using another intentation rule and was not created by our team the indentation used within the file should not be changed.
