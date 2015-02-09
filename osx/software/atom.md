# Atom

## Installation

```ShellSession
$ brew cask install atom
```

## Packages

### Misc UI

- **`atom-color-highlight`**:
  - Installation: `apm install atom-color-highlight`
- **`file-icons`**:
  - Installation: `apm install file-icons`
- **`highlight-selected`**:
  - Installation: `apm install highlight-selected`

### Find

- **`todo-show`**:
  - Installation: `apm install todo-show`

### Minimap

- **`minimap`**:
  - Installation: `apm install minimap`
- **`minimap-find-and-replace`**:
  - Installation: `apm install minimap-find-and-replace`
- **`minimap-selection`**:
  - Installation: `apm install minimap-selection`
- **`minimap-git-diff`**:
  - Installation: `apm install minimap-git-diff`
- **`minimap-color-highlight`**:
  - Installation: `apm install minimap-color-highlight`

### Formatting

- **`atom-beautify`**:
  - Installation: `apm install atom-beautify`
  - Dependencies:

    ```ShellSession
    $ sudo gem install htmlbeautifier     # For HTML formatting.
    $ pip install sqlparse                # For SQL formatting.
    $ brew install pandoc                 # For Markdown formatting.
    $ sudo gem install ruby-beautify      # For Ruby formatting.
    $ sudo pip install --upgrade autopep8 # For Python formatting.
    $ brew install uncrustify             # For Java/C/C++/C#/Objective-C/D/Pawn/Vala formatting.
    $ # (for PHP you need PHP_Beautify, but I didn't find a good way to install pear).
    ```

- **`csscomb`**:
  - Installation: `apm install csscomb`

### Integration

- **`marked`**:
  - Installation: `apm install marked`

### AutoComplete

- **`autocomplete-paths`**:
  - Installation: `apm install autocomplete-paths`
- **`autocomplete-plus`**:
  - Installation: `apm install autocomplete-plus`
- **`autocomplete-snippets`**:
  - Installation: `apm install autocomplete-snippets`
- **`atom-ternjs`**:
  - Installation: `apm install atom-ternjs`

### Languages

- **`language-gitignore`**:
  - Installation: `apm install language-gitignore`
- **`language-haml`**:
  - Installation: `apm install language-haml`
- **`language-lisp`**:
  - Installation: `apm install language-lisp`
- **`editorconfig`**:
  - Installation: `apm install editorconfig`

### Snippets

- **`javascript-snippets`**:
  - Installation: `apm install javascript-snippets`

### Refactoring

- **`refactor`**:
  - Installation: `apm install refactor`.

- **`js-refactor`**:
  - Installation: `apm install js-refactor`.

- **`coffee-refactor`**:
  - Installation: `apm install coffee-refactor`.

### Linting

- **`linter`**:
  - Installation: `apm install linter`
- **`linter-coffeelint`**:
  - Installation: `apm install linter-coffeelint`
  - Dependencies:

    ```ShellSession
    $ npm install -g coffeelint # For the program `coffeelint`.
    ```
- **`linter-csslint`**:
  - Installation: `apm install linter-csslint`
  - Dependencies:

    ```ShellSession
    $ npm install -g csslint # For the program `csslint`.
    ```
- **`linter-erb`**:
  - Installation: `apm install linter-erb`
- **`linter-haml`**:
  - Installation: `apm install linter-haml`
  - Dependencies:

    ```ShellSession
    $ sudo gem install haml-lint # For the program `haml-lint`.
    ```
- **`linter-jshint`**:
  - Installation: `apm install linter-jshint`
  - Dependencies:

    ```ShellSession
    $ npm install -g jshint # For the program `jshint`.
    ```
- **`linter-rubocop`**:
  - Installation: `apm install linter-rubocop`
  - Dependencies:

    ```ShellSession
    $ sudo gem install rubocop # For the program `rubocop`.
    ```
- **`linter-ruby`**:
  - Installation: `apm install linter-ruby`
- **`linter-scss-lint`**:
  - Installation: `apm install linter-scss-lint`
  - Dependencies:

    ```ShellSession
    $ sudo gem install scss-lint # For the program `scss-lint`.
    ```
- **`linter-lua`**:
  - Installation: `apm install linter-lua`
- **`linter-pylint`**:
  - Installation: `apm install linter-pylint`
  - Dependencies:

    ```ShellSession
    $ pip install pylint # For the program `pylint`.
    ```
- **`linter-rst`**:
  - Installation: `apm install linter-rst`
- **`linter-javac`**:
  - Installation: `apm install linter-javac`
  - Dependencies:
    - JDK
- **`linter-rustc`**:
  - Installation: `apm install linter-rustc`
  - Dependencies:
    - Rust

### Projects

- **`project-manager`**:
  - Installation: `apm install project-manager`

### External commands integration

- **`script`**:
  - Installation: `apm install script`
- **`term2`**:
  - Installation: `apm install term2`
- **`ruby-bundler`**:
  - Installation: `apm install ruby-bundler`
