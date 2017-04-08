# Virtual Python Environments

Much of this article is drawn from [_The Hitchiker's Guide to Python_](http://python-guide-pt-br.readthedocs.io/en/latest/).

## Create a Virtual Python Environment

`cd` to your project directory and use `virtualenv` to create the new virtual environment.

The following commands will create a new virtual environment under `my-project-folder/my-venv`.
<pre>
cd <i>my-project-folder</i>
virtualenv --python python3 <i>my-venv</i>
</pre>


## Activate the Environment.
<pre>
source <i>my-venv</i>/bin/activate
</pre>
After you activate the environment, your command prompt will be modified to reflect the change.

## Add Libraries and Create a `requirements.txt` File

After you activate the virtual environment, you can add packages to it using `pip`.  You can also create a description of your dependencies using `pip`.

The following command creates a file called `requirements.txt` that enumerates the installed packages.
<pre>
pip freeze > <i>requirements.txt</i>
</pre>

This file can then be used by collaborators to update virtual environments using the following command.
<pre>
pip install -r <i>requirements.txt</i>
</pre>

## Deactivate the Environment
To return to normal system settings, use the `deactivate` command.
<pre>
deactivate
</pre>

After you issue this command, you'll notice that the command prompt returns to normal.
