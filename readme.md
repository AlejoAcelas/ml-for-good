# ML4G
This repo contains the instructions for the ML for Good bootcamp, for students and researchers interested in AI safety.

The program is aimed at beginners in machine learning, but is quite ambitious, and we hope that even advanced students will enjoy participating in this program.

# Curriculum ML4Good

We draw inspiration from the redwood mlab, and ARENA, both of which focuses mainly on the ML engineering part.
However there are a lot more workshops on strategy, goverance and conceptual AI safety during the ML4G.

## For teachers, contributors and assistants

To setup your machine for adding and editing the workshops, follow these steps:
```sh
# Create a virtual environemnt, for instance with venv.
python -m venv .env
# Activate the venv
source .env/bin/activate
# Install all the dependencies. If you don't have a GPU, start by installing pytorch without GPU support
# pip3 install torch  --index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt
# Setup the pre-commit hooks
pre-commit install
```

The pre-commit hooks will automatically format and **remove the output** of the notebooks before a commit. It will also prevent commiting large files.
You can also run them manualy at any time on staged files with `pre-commit run`.
If the hooks make any change, it will cancel the commit and add the changes as unstagged changes.

### Adding new workshops

New workshops go in `workshops/`. They should be jupyter notebooks, possibly with auxilary files.
- If they need auxilary files, check how it was done for the [tensors workshop](./workshops/tensors/tensors.ipynb). You will need code similar to that of the first code cell of the notebook.
- Precommit will also prevent you from commiting files of more than 500kb, if those are needed, discuss solutions with the team.
- Every cell output will be removed from the notebook when you commit (due to pre-commit). This is great for the health of the repo, but if you are still experimentating and developping the notebook you might want to remember it.
- It's helpful if you add a ![Open in colab](https://colab.research.google.com/assets/colab-badge.svg) badge at the start of the notebook with the correct url to open it directly. To do so, run in the virtual environment:
```
meta/tools.py badge <your-notebook.ipynb> --auto-add
```
- Once pushed, notebooks are then availaible on google colab with `https://colab.research.google.com/github/EffiSciencesResearch/ML4G/blob/main/<PATH TO NOTEBOOK IN THE GIT>`, which is the link auto-added by the previous command.
- To include solutions directly inside the notebooks, you can use html inside a markdown cell as follows:
    ~~~html
    <details>
    <summary>Solution</summary>

    ```python
    # Your solution here
    ```

    </details>
    ~~~
