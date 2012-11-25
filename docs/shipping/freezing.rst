Freezing Your Code
==================

An alternative to shipping your code is freezing it — shipping it as an
executable with a bundled Python interpreter.

Many applications you use every day do this:

- Dropbox
- BitTorrent
- ...

.. todo:: Fill in "Freezing Your Code" stub



Comparison
----------

Solutions and platforms/features supported:

=========== ======= ===== ==== ======== ======= ============= ============== ==== =====================
Solution    Windows Linux OS X Python 3 Licence One-file mode Zipfile import Eggs pkg_resources support
=========== ======= ===== ==== ======== ======= ============= ============== ==== =====================
bbFreeze    yes     yes   yes  no       MIT     no            yes            yes  yes                  
py2exe      yes     no    no   no       MIT     yes           yes            no   no                   
pyInstaller yes     yes   yes  no       GPL     yes           no             yes  no                   
cx_Freeze   yes     yes   yes  yes      PSF     no            yes            yes  no                   
=========== ======= ===== ==== ======== ======= ============= ============== ==== =====================

.. todo:: Add other solutions: py2app

.. note::
    Freezing Python code on Linux into a Windows executable was only once
    supported in PyInstaller, `but later dropped
    <http://stackoverflow.com/questions/2950971/cross-compiling-a-python-script-on-linux-into-a-windows-executable#comment11890276_2951046>`_.

.. note::
    All solutions need MS Visual C++ dll to be installed on target machine.
    Only Pyinstaller makes self-executable exe that bundles the dll when
    passing ``--onefile`` to `Configure.py`.


Windows
-------


cx_Freeze
~~~~~~~~~

Prerequisite is to install :ref:`Python, and the modules required to run your python scripts <install-windows>`.

cx_Freeze is a module used to create the python scripts into an executable(.exe) file. It is very easy method.

1. Download and install cx_Freeze windows binary for your python version from http://www.lfd.uci.edu/~gohlke/pythonlibs/ (at this site you can download hundreds of python modules in windows binary format. So it is worth visiting it even if you don't need cx_Freeze). 

2. Find the location of the your source code folder. for example- I created a test.py and stored it in c:\\samp.

::

    #c:\samp\test.py
	x="hai this is an exe file created from python scripts using cxfreeze. Press Enter to exit >> "
	y=input(x)
	
3. Create a folder to store the build file(.exe and other files). for eg- i created a folder c:\\samp\\build\

4. Open Command Prompt(start->run type "cmd" press enter) and type 

.. code-block:: console

	C:\Documents and Settings\suh>c:\python32\scripts\cxfreeze c:\samp\test.py --target-dir=c:\samp\build

The first word stand for the path of cxfreeze software(note python32 stands for Python 3.2 version, you must replace it with your python version. ie-python26,python27,python32 etc), next word for the main python source code file and the third word for the destination directory of build files(ie .exe and other files)

for more options type

::

	C:\Documents and Settings\suh>c:\python32\scripts\cxfreeze -help

bbFreeze
~~~~~~~~

Prerequisite is to install :ref:`Python, Distribute and pywin32 dependency on Windows <install-windows>`.

.. todo:: Write steps for most basic .exe

py2exe
~~~~~~

Prerequisite is to install :ref:`Python on Windows <install-windows>`.

1. Download and install http://sourceforge.net/projects/py2exe/files/py2exe/

2. Write setup.py (`List of configuration options <http://www.py2exe.org/index.cgi/ListOfOptions>`_)::

    from distutils.core import setup
    import py2exe

    setup(
        windows=[{'script': 'foobar.py'}],
    )

3. (Optionally) `include icon <http://www.py2exe.org/index.cgi/CustomIcons>`_

4. (Optionally) `one-file mode <http://stackoverflow.com/questions/112698/py2exe-generate-single-executable-file#113014>`_

5. Generate `.exe` into `dist` directory::

   $ python setup.py py2exe

6. Provide the Microsoft Visual C runtime DLL. Two options: `globally install dll on target machine <https://www.microsoft.com/en-us/download/details.aspx?id=29>`_ or `distribute dll aloneside with .exe <http://www.py2exe.org/index.cgi/Tutorial#Step52>`_.

PyInstaller
~~~~~~~~~~~

Prerequisite is to have installed :ref:`Python, Distribute and pywin32 dependency on Windows <install-windows>`.

- `Most basic tutorial <http://bojan-komazec.blogspot.com/2011/08/how-to-create-windows-executable-from.html>`_
- `Manual <http://www.pyinstaller.org/export/d3398dd79b68901ae1edd761f3fe0f4ff19cfb1a/project/doc/Manual.html?format=raw>`_


OSX
---


py2app
~~~~~~

PyInstaller
~~~~~~~~~~~


Linux
-----


bbFreeze
~~~~~~~~

PyInstaller
~~~~~~~~~~~
