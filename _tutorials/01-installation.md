---
title: "Installation"
permalink: /tutorials/installation/
excerpt: "Select preferences and run the command to install MatchZoo locally."
last_modified_at: 2020-08-12
redirect_from:
  - /theme-setup/
toc: true
---

## Prerequisites

### Python

MatchZoo is dependent on Python 3. It is recommended that you use Python 3.6 or greater, which can be installed either through the Anaconda package manager (see below), [Homebrew](https://brew.sh/), or the [Python website](https://www.python.org/downloads/mac-osx/).

### Package Manager

MatchZoo can be installed through two package Manager, [Anaconda](https://www.anaconda.com/download/) or [pip](https://pypi.org/project/pip/). Anaconda is the recommended package manager as it will provide you all of the MatchZoo dependencies in one, sandboxed install, including Python.

#### Anaconda

To install Anaconda, you can download [graphical installer](https://www.anaconda.com/download/) or use the command-line installer. If you use the command-line installer, you can right-click on the installer link, select `Copy Link Address`, and then use the following commands:

   ```bash
   # The version of Anaconda may be different depending on when you are installing`
   curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
   sh Miniconda3-latest-MacOSX-x86_64.sh
   # and follow the prompts. The defaults are generally good.`
   ```

#### pip

If you installed Python via Homebrew or the Python website, `pip` was installed with it. If you installed Python 3.x, then you will be using the command `pip3`.

**Tip:** If you want to use just the command `pip`, instead of `pip3`, you can symlink pip to the pip3 binary.
{: .notice--info}

## Installation

### Anaconda

To install MatchZoo via Anaconda, use the following conda command:

   ```bash
   conda install matchzoo-py
   ```

### pip

To install MatchZoo via pip, use one of the following two commands, depending on your Python version:

   ```bash
   pip install matchzoo-py
   # Python 3.x
   pip3 install matchzoo-py
   ```

### Building from source

Install MatchZoo-py from the Github source:

   ```bash
   git clone https://github.com/NTMC-Community/MatchZoo-py.git
   cd MatchZoo-py
   python setup.py install
   ```