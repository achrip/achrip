---
tags:
- how-to
date: 2024-02-25
title: Setting up Python with Anaconda3 for Machine Learning
summary: Step-by-Step guide to setting up your python environment for machine learning and data science
categories:
lastMod: 2024-02-28
---
# Why Anaconda
---

[Anaconda](https://anaconda.com/) is an open-source distribution of the programming language Python and R. The distribution comes with the Python interpreter and various packages related to machine learning and data science.

Basically, Anaconda is a simple way for people who are interested in these fields to start learning without having to think about the complexity of setting up the environment. This is because Anaconda installs most, if not all, of the packages that are needed with a single installation

# Anaconda vs Miniconda
---

By default, Anaconda installs all of the packages for you. If you feel that's overkill, or perhaps you don't want to sacrifice that much storage space, consider giving Miniconda a shot.

Miniconda only installs the Python interpreter and the `conda` package manager. So you would have to manage the installed packages by yourself.

Still don't know what to install? Go with [Anaconda](https://anaconda.com/)

# Installing Anaconda
___

> ⚠️
This guide is strictly for Windows only. I shall assume those who are on UNIX-Based distributions are smart and know how to navigate yourself throughout this guide

## Ensure `winget` is Installed

Open Windows Powershell and run the command

```
winget --version
```

If the output returns the version of `winget` installed on you machine, then continue to [1.2](## Installing Anaconda
)

If the output return an error, follow [this](https://www.microsoft.com/p/app-installer/9nblggh4nns1) link to install `winget` on your machine.

When installing `winget` fails, and you wouldn't bother searching on how to install it, you can jump to [here](You can also try installing Anaconda or Miniconda from the official Anaconda website [here](https://anaconda.com/download).
)

## Installing Anaconda
In Windows Powershell, run the following command

```
winget install -e -id Anaconda.Anaconda3
# OR 
winget install -e -id Anaconda.Miniconda3
```

You can also try installing Anaconda or Miniconda from the official Anaconda website [here](https://anaconda.com/download).
> ⚠️
When installing Anaconda from the official website, the `conda` package manager can only be run via the `Anaconda Command Prompt` or `Anaconda Powershell`.

## Verify Anaconda Installation

In Windows Powershell, run this command
```
conda --version
```

If the prompt returns the version of your `conda`, then you're all set!

# Setting Up Virtual Environments
___

## What is a Virtual Environment?

As I am not really the best person to explain this at the moment of this article written, I'd suggest reading [this](https://realpython.com/python-virtual-environments-a-primer/) post. It covers what is a virtual environment and why do we need to use virtual environments on every python projects.

## Creating new Virtual Environments

In Windows Powershell, run the command
```
conda create -n <virtual env name>
```

You can give the virtual environment any name, but be sure to **not use whitespaces**. Instead you can replace it with dashes (`-`) or underscores (`_`).  And don't forget to omit the `< > `.

Alternatively, you can also install a specific Python Interpreter to the virtual environment by running the following command instead when creating a virtual environment
```
conda create -n <virtual env name> python=x.x.x`
```

Replace `x.x.x.` with the Python Interpreter version of your choice.

Then follow any prompts `conda` gives you.

## Installing Libraries in the Virtual Environment

To view all of the virtual environments listed on your local machine, you can run the following command on Windows Powershell
```
conda env list
```

Activating a virtual environment is as easy as running the command below on Windows Powershell
```
conda activate <virtual env name>
```

After activating the virtual environment, you could install any required libraries using `pip` with the command 
```
pip install <library name>
```

Alternatively, you could also define a `.txt` file that consists of required libraries for your virtual environment somewhere in your machine. Installing those packages would be as simple as running 
```
pip install -r </path/to/your/requirements.txt>
```

If all goes well, you're done! You can use the virtual environment with any code editor of your choice!

> 💡
You only need to access the virtual environment via the terminal like this **only** when you're setting up the virtual environment for the first time. With the exception that you prefer using [Jupyter](https://jupter.org) rather than the mainstream code editors.

# Afterword
---

## Advice for The Brave

This is a personal hot take; sticking with Anaconda won't broaden your horizon. To the brave souls who are reading this article, I could advise you to try other methods (or at least consider trying). Because there's a whole new world out there that may or may not benefit you in a way.

Here are some open-source projects that could serve as a good starting point:

For WSL and UNIX-based OS users:

[`pyenv`](https://github.com/pyenv/pyenv)

[`pyenv-virtualenvwrapper`](https://github.com/pyenv/pyenv-virtualenvwrapper)

[`hygeia`](https://github.com/nbigaouette/hygeia)

[`uv`](https://github.com/astral-sh/uv)

For Windows Users:

[`hygeia`](https://github.com/nbigaouette/hygeia)

[`uv`](https://github.com/astral-sh/uv)
