# Intro to conda environments

## Creating Environments (fresh)

(This is all derived from https://conda.io/docs/using/envs.html, if you want more detail)

These commands can only be used if conda is on the path (either you added it to your PATH, or via the anaconda prompt).

To create a fresh environment, you can do something like:

```shell
conda create --name <env name>
```

You can also install things simultaneously, and specify versions of those pieces of software if needed.

```shell
conda create -n <env name> python=3.5 numpy scipy>=0.15.0
```

## Creating Environments (from file)

Another useful way to create environments is by specifying the environment in a YAML file, and then running

```shell
conda env create -f <filename>.yml
```

Here's an example YAML file.

```yaml
name: replan-09292017

dependencies: # these are installed from conda packages
  - python=3.5
  - numpy
  - scipy
  - pip: # these are installed via pip, i.e. `pip install <name>`
    - git+https://github.com/psychopy/psychopy
    - toon
    - transitions
```

## Using environments

Once the environment has been created (budget 10 - 20 mins, depending on your internet connection, cached packages, operating system, etc.), you can activate an environment via:

```shell
activate <env name>
```

With certain command-line tools, you may need to prepend a `source` to that command, i.e. `source activate <env name>`.

As a sanity check, you can then check whether the version of the python interpreter matches the expected value, via `python --version`.
