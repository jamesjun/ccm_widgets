## ccm_widgets installation

This file was auto-generated by reactopya and all reactopya projects share these installation instructions.

## Prerequisites

* Linux or OS X
* Python >= 3.6

## Installing the Python package

Install the ccm_widgets Python package:

```
# currently at version ccm_widgets==0.4.10
pip install --upgrade ccm_widgets
```

Then, depending on how you intend to use the library, use one or more of the following methods.


## JupyterLab and Jupyter Notebook

To use ccm_widgets within JupyterLab and in Jupyter Notebook you will first need to install the reactopya_jup notebook extension.

As a prerequisite (for JupyterLab) you need the ipywidgets lab extension.

You will need to first install jupyterlab unless you have it from a different place: `pip install jupyterlab`

Then install the extension (from npm):

```
jupyter labextension install @jupyter-widgets/jupyterlab-manager
```

Next, install the the latest reactopya_jup Python package:

```
pip install --upgrade reactopya_jup==0.9.1
```

For JupyterLab, install the lab extension:

```
jupyter labextension install reactopya_jup@0.9.1
```

For Jupyter Notebook, install and enable the notebook extension:

```
jupyter nbextension install --sys-prefix --py reactopya_jup
jupyter nbextension enable reactopya_jup --py --sys-prefix
```

Finally you should use the following at the top of your notebook:

```
import ccm_widgets
ccm_widgets.init_jupyter()
```

See the notebook_examples directory which might exist at the root of this repository.

## Desktop widgets (via electron)

To view the widgets as standalone desktop windows (outside of the notebook), you must first install electron. You will need NodeJS >= 8.

```
npm install -g electron
```

If you run into permissions problems, follow the instructions [here](https://github.com/sindresorhus/guides/blob/master/npm-global-without-sudo.md) to configure npm to install global packages inside your home directory.

Now you may write a .py script that begins with the following lines:

```
import ccm_widgets
ccm_widgets.init_electron()
```

or you can launch a widget from a .json file via:

```
ccm_widgets show --widget [file.json]
```

See the desktop_examples directory which might exist at the root of this repository.

## Web server

To host a ccm_widgets widget as a web server, simply create the widget in a Python script and then run:

```
widget.host(port=6065)
```

where 6065 may be replaced by any open port. Then you can view the widget in your browser by navigating to `http://localhost:6065`. There may be examples of this in the desktop_examples/ directory.

## Google colaboratory

No extensions are needed for colaboratory, but you do need to pip install reactopya_jup as above. Then the top of your notebook should include:

```
import ccm_widgets
ccm_widgets.init_colab()
```

While it is possible to use a local runtime for colab, this involves a bit of a hack to get the callbacks to work properly. Ask me about it if you are interested.


## Development installation

A development installation has the following additional prerequisites

* NodeJS >= 8
* Yarn
* reactopya

First install [reactopya](https://github.com/flatironinstitute/reactopya):

```
pip install --upgrade reactopya
```

Now clone this repo:

```
git clone [this_repo]
cd [directory-of-the-repo]
```

**Electron development mode**

This following is the best way to develop the widgets.

First create a file called dev_widget.json in the root directory containing the information about the widget you want to develop.

```
# you only need to run this once:
reactopya install-dev

# The following will open a widget in development mode
# with hot module reloading whenever the source code changes
reactopya start-dev
```

**JupyterLab and Jupyter Notebook (development installation)**

First install the reactopya_jup Python package and JupyterLab and Jupyter Notebook extensions as above

Then from the root directory of your project:

```
reactopya install-jupyter
```

Now you should be able to `import ccm_widgets` as in the example notebook

**Google colab**

Google colab usage is the same as JupyterLab and Jupyter Notebooks except replace `init_jupyter()` by `init_colab()`.

While it is possible to use a local runtime for colab, this involves a bit of a hack to get the callbacks to work properly. Ask me about it if you are interested.