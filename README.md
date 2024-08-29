# TrainingBook

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://fieldofnodes.github.io/TrainingBook.jl/stable/)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://fieldofnodes.github.io/TrainingBook.jl/dev/)
[![Build Status](https://github.com/fieldofnodes/TrainingBook.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/fieldofnodes/TrainingBook.jl/actions/workflows/CI.yml?query=branch%3Amain)

# TrainingBook

Welcome to the `TrainingBook` module! This Julia package is designed to assist in generating and managing training books, particularly by creating LaTeX input lists for training modules. It builds on the `TrainingContent` module, making it easy to organize training content into a structured book format.

## Features

- **Chapter and Module Input Generation**: Automatically generate LaTeX input commands for chapters and modules.
- **Create Module Lists**: Generate a comprehensive list of module inputs for inclusion in LaTeX documents.
- **Export to File**: Easily write the generated LaTeX input list to a file, ready for use in compiling a training book.

## Installation

To use `TrainingBook`, ensure that you have Julia installed on your system. You can add this module to your Julia environment by including it in your project or environment:

```julia
] add https://github.com/your-repo/TrainingBook
```

## Usage

Begin by importing the module into your Julia environment:

```julia
using TrainingBook
```

### Generating a Chapter Input

The `generate_chapter_input` function provides a template for including the introduction chapter in your LaTeX document:

```julia
chapter_input = generate_chapter_input()
```

This function returns a string with the LaTeX command to input the `introduction.tex` file:

```latex
\input{TrainingBook/introduction.tex}
```

### Generating Module Inputs

To generate the LaTeX input command for a specific module, use the `generate_input` function:

```julia
module_input = generate_input(module_number::Int)
```

This function formats the module number with leading zeros and returns a string with the LaTeX command to input the corresponding module file, such as:

```latex
\input{TrainingBook/module01.tex}
```

### Creating a Complete Module List

To generate a full list of module inputs based on a `TrainingTableData` object, use the `generate_module_list` function:

```julia
module_list = generate_module_list(ttd::TrainingTableData)
```

This function combines the chapter input with a list of module inputs, producing a comprehensive list for inclusion in a LaTeX document.

### Writing the Module List to a File

Once the module list is generated, you can write it to a file using the `write_training_book_list_to_file` function:

```julia
write_training_book_list_to_file("training_book.tex", ttd::TrainingTableData)
```

This will create a `.tex` file containing the LaTeX commands to include the introduction and all modules specified in the `TrainingTableData`.

### Example Usage

```julia
# Assuming you have already generated `TrainingTableData` from the TrainingContent module
using TrainingContent

# Create some sample content titles
titles = ["Introduction", "Module 1: Basics", "Module 2: Advanced Topics"]

# Generate the training table data
training_data = generate_TrainingTableData(titles; course_length=10)

# Generate the LaTeX module list as a string
latex_module_list = generate_module_list(training_data)

# Write the LaTeX module list to a file
write_training_book_list_to_file("my_training_book.tex", training_data)
```

## Contributing

Contributions to `TrainingBook` are welcome! Please submit a pull request with your changes or open an issue if you encounter any problems.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions, suggestions, or feedback, feel free to reach out via [GitHub Issues](https://github.com/your-repo/TrainingBook/issues).

---

This README provides an overview of the functionality within `TrainingBook`. For detailed examples and additional information, please refer to the module's source code and documentation.
