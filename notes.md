- Methodology: Design Science Research
  - identify problem and motivate
  - define objective of a solution
  - design & develop
  - demonstrate -> benchmarks
  - evaluate -> evaluate benchmarks and compare against other solutions to the problem if possible
  - communicate -> publish

- Problem and Motivation
  - since information systems get more and more complex it is harder to manage and maintain them
  - a lot of companies use the philosophy of clone-and-own to create new software solutions
  - this leads to a lot of identical code which needs to be fixed at every point it exists if a bug occurs
  - thus a software product line is very attractive but the reengineering and design of such a SPL is often time consuming -> expensive and error prone -> lots of manual work
  - the automation of the creation of SPLs has a lot of research done, for example Wille et. al. proposed such an automatic solution for block based programming languages
  - problem, only block based languages, but a lot of programming languages are not block based
  - we propose a solution that is applicable to all common programming languages and allows for easy decomposition of code into reusable blocks and easy recomposition for generating different versions of the same system
  - ideas are taken from Eisenecker et. al. thought of SPL Systems as sets which can be intersected

- objective for a solution:

RQ1 Language Independence:
Is the proposed isolation technique capable of isolating common and unique features for different programming languages and other use cases? (esp. Java/C++ or simple text files, e.g. requirements, docs)
RQ2 Correctness:
Are the generated code blocks as such correct and can they be used to regenerate the original code files?
RQ3 Minimalisem:
Do the generated code blocks result in minimal redundancy?
RQ4 Comparison:
How well does our technique compare to similar techniques in the same task?

## design and development

- started with the question: Is it possible to build a language and feature agnostic feature isolation algorithm? Inspired by J. Martinez et. al
- how to tokenize? Use character level or token level?
- choose token level since tokens are more reliable in the alignment we generate and allow for larger blocks
- problem no difference between the gotoh aligner and the standard LCS
- Line level alignment leads to better alignments between files

1. we check are directories or single files specified
2. if directories we read out files and continue the file algorithm path with ever file
3. we check if files are identical if so, no comparison is needed
4. First round begins by parsing files by line, each line represents a token
5. we use longest common subsequence alignment to align the lines
6. keep only the lines that where not aligned
7. Second round begins, tokenize the lines into tokens that are on a word/expression level
8. we use longest common subsequence to align each of the token sequences
9. find the best match between the token sequences
   10.all remaining tokens are kept as unique features
