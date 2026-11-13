# Doxygen - Automatic Code Documentation

## 1. Introduction
Doxygen is an open-source documentation generator for programming languages such as C, C++, Python and Java. It reads specially formatted comments in source code and generates reference documentation, commonly in HTML or LaTeX/PDF.

Documentation explains what functions, classes and modules are meant to do. It helps other developers understand, maintain and use a codebase.

## 2. Why documentation matters
Technical documentation clarifies requirements, supports software maintenance and onboarding, helps with quality checks, and improves knowledge sharing in a team.

## 3. Main features
- Extracts documentation from source-code comments.
- Documents functions, classes and modules.
- Generates cross-references, call graphs and inheritance diagrams.
- Supports Markdown, LaTeX formulas, Graphviz diagrams and code examples.
- Can be integrated into CI/CD workflows.

## 4. Installation
**Windows:** Download the installer from [doxygen.nl/download.html](https://www.doxygen.nl/download.html).

**macOS:**
```bash
brew install doxygen
```

**Debian/Ubuntu:**
```bash
sudo apt-get install doxygen
```

Verify the installation:
```bash
doxygen --version
```

## 5. Basic workflow
1. Write specially formatted comments in source files.
2. Generate a configuration file.
3. Edit the configuration if required.
4. Run Doxygen.
5. Browse the generated documentation.

```bash
doxygen -g Doxyfile
doxygen Doxyfile
```

The first command creates a sample `Doxyfile`; the second runs Doxygen using it. The generated HTML can be opened from `html/index.html`.

## 6. C/C++ comment syntax
Doxygen comments contain tags that describe code elements.

```cpp
/**
 * \\brief Calculates the square of a number.
 *
 * Multiplies the input value by itself.
 * \\param x The number whose square is required.
 * \\return The square of x.
 */
int square(int x);
```

For a class:

```cpp
/**
 * \\class Car
 * \\brief Represents a car object.
 *
 * This class contains basic car operations.
 */
class Car {
public:
    /**
     * \\brief Starts the engine.
     * \\return True if the engine starts successfully.
     */
    bool startEngine();
};
```

## 7. Python documentation
For Python, the lecture demonstrates documentation in docstrings.

```python
def increment(value):
    '''
    Brief description.
    More details about the function.

    :param value: The input value
    :type value: int
    :return: The incremented value
    :rtype: int
    '''
    return value + 1
```

The fields describe the parameter, its type, the return value and its type.

## 8. Common Doxygen tags
| Tag | Purpose |
|---|---|
| `\\brief` | Short summary of a function, class or module |
| `\\param` | Parameter description |
| `\\return` | Return value description |
| `\\author` | Author information |
| `\\version` | Version information |
| `\\see` | Reference to related items |
| `\\note` | Additional note |

## 9. Configuration and output formats
Doxygen settings are stored in the `Doxyfile`. The lecture shows settings such as:

```text
GENERATE_HTML = YES
GENERATE_LATEX = YES
GENERATE_RTF = NO
GENERATE_XML = NO
```

HTML is convenient for browsing, while LaTeX/PDF is useful for printable manuals. Other available formats include RTF, XML, DocBook and man pages.

For call and include diagrams, the slides mention enabling Graphviz support:

```text
HAVE_DOT = YES
```

The slides also mention `@dot` and PlantUML directives for embedding diagrams.

## 10. Best practices
- Explain the purpose and contract of a function, not only its parameters.
- Keep brief and detailed descriptions separate.
- Document public APIs and modules.
- Use a consistent tag set and layout.
- Store the `Doxyfile` in the source repository.
- Update documentation along with code changes.
- Generate documentation as part of continuous integration when possible.

## 11. Doxygen with version control
Keeping the configuration file in the source repository allows team members to generate the same documentation. Documentation updates can be reviewed with code changes, and generated pages can be published through GitHub Pages or an internal wiki.

## 12. What I learned
Doxygen connects documentation directly to source code. Writing explanations near the functions and classes makes API documentation easier to maintain when the code changes.

## 13. Further reading
- [Doxygen Manual](https://www.doxygen.nl/manual/)
