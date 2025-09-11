# Good Enough Computing in Science (GECS) | Tutorial 2 | Project template

<a target="_blank" href="https://cookiecutter-data-science.drivendata.org/">
    <img src="https://img.shields.io/badge/CCDS-Project%20template-328F97?logo=cookiecutter" />
</a>

A tutorial on project folder templates using Cookiecutter Data Science package.

## Project Organization

```
├── LICENSE            <- Open-source license if one is chosen
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── analyzed           <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── pyproject.toml     <- Project configuration file with package metadata for 
│                         src and configuration for tools like black
│
│
├── results            <- Generated histogram of word counts.
│
├── scripts            <- Source code for use in this project.
│   │
├   ├── clean_book.py           <- Clean raw book text
│   │
│   ├── count_words.py          <- Count words in a cleaned book text
│   │
│   └── plot_counts.py          <- Plot a word count histogram
│
└── src   <- Source code for use in this project.
    │
    ├── __init__.py             <- Makes src a Python module
    │
    ├── config.py               <- Store useful variables and configuration
    │
    ├── dataset.py              <- Code to download or generate data
    │
    ├── analysis.py             <- Code to analyze processed data
    │
    └── plots.py                <- Code to create visualizations
```

## Installation

Use the package manager [pixi](https://pixi.sh) to install the virtual enviroemnet for this project.

```bash
pixi install
```

## Usage

To execute the project pipeline via command-line interface (CLI), first active the virtual environement shell

```bash
pixi shell
```

Next, run the following commands in the given order:

```bash
python src/dataset.py main
python src/analysis.py main
python src/plots.py main
```

The word count histogram, `histogram.pdf`, can be found in `results` folder.

For running each of the steps using [Pixi tasks](https://pixi.sh/latest/workspace/advanced_tasks) execute the following:

```bash
pixi run process
pixi run analyze
pixi run plot
```

In order to run all of these tasks together, use a convieniet task that combines the above together:

```bash
pixi run all
```

You might wish to clean the folders before you do so with

```bash
pixi run clean
```

To see how the pipeline has been refactored, you can run the same commands as in the Tutorial 1:

```bash
python src/dataset.py data/raw/book.txt data/processed/book.txt
python count_words.py data/processed/book.txt analyzed/word_count.csv
python plot_histogram.py analyzed/word_count.csv results/histogram.pdf
```

The commands above are scripted versions of src layout run code using [Typer](https://typer.tiangolo.com/).

`notebooks/0.01-igorsdub-generate_book_word_count_histogram.ipynb` contains the whole pipeline from start to finish but without any file saving. `## Local library import` section very well illustractes the power of src layout. You don't need to edit code in the notebook or relaoed it upon every edit of the module.

## Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.

Please make sure to update tests as appropriate. To be added...

## License

[MIT](https://choosealicense.com/licenses/mit/)

## References

1. [Make a README](https://www.makeareadme.com/)
2. [Cookiecutter Data Science](https://cookiecutter-data-science.drivendata.org/)
