seisplot
========

A utility for plotting `SEG-Y files <http://www.agilegeoscience.com/blog/2014/3/26/what-is-seg-y.html>`_. 

.. image:: https://img.shields.io/badge/status-beta-yellow.svg?style=flat-square
    :target: #
    :alt: Project status

.. image:: https://img.shields.io/badge/release-v0.3-green.svg?style=flat-square
    :target: #
    :alt: Release

.. image:: https://img.shields.io/badge/python-3.4,_3.5-blue.svg?style=flat-square
    :target: #
    :alt: Python version

.. image:: https://img.shields.io/badge/license-Apache_2.0-blue.svg?style=flat-square
    :target: http://www.apache.org/licenses/LICENSE-2.0
    :alt: License


Installation
-------

If you don't already have a reliable Python installation, and know how to wield it, I recommend downloading and installing `Anaconda <https://www.continuum.io/downloads>`_.

Get this repo with ``git`` or by downloading the ZIP file, and enter that directory.

Make and enter a virtual environment::

    conda create -n seisplot --file package-list.txt
    source activate seisplot

Install one more dependency, `ObsPy <https://github.com/obspy/obspy>`_::

    conda config --add channels conda-forge
    conda install obspy

Or, if you already have ``obspy``, update it::

    conda update obspy


Quick start
-------

You can see what the thing does with::

    ./seisplot.py --demo


Running
-------

Edit ``config.yaml`` to meet your requirements.

Run the script from the command line, for example::

    ./seisplot.py </path/to/infile.sgy>
    
This will use the settings in ``config.yaml`` to make a PNG file in the same location, and with the same basic filename.

The input filename can be any POSIX path specifier, so ``*.sgy`` will find all files with that extension. to recursively descend in to directories, use ``**`` like so: ``data/**/*.sgy``. To match multiple file extensions, try ``*.[s,S]*[g,G][y,Y]`` or ``{*.segy}{*.sgy}`` (exact results may depend on your platform).

To use a specific config file with another name or location add the ``--config`` option. To specify the output filetype — use PDF or SVG for fully scalable vector graphics instead of a raster — add the ``--out`` parameter::

    ./seisplot.py </path/to/infile.segy> --config myconfig.yaml --out </path/to/result.pdf>

With ``--out`` you can specify an output file and `seisplot` will honour the filetype if the ``matplotlib`` backend you are using supports it. If you specify a directory, all the outout files will go there, using the SEG-Y file's name as the main part of the filename (for example, `31-08.sgy` will give you ``31-08.png`` in the output directory.

As in all things, stains are optional.


Example
-------

.. image:: https://dl.dropboxusercontent.com/u/14965965/31_81_PR.stupid.png


New in this version
-------

- The ability to plot from 3D seismic, inlcuding a dual inline/crossline plot, and a timeslice.
- An intersection line on dual inline/crossline displays for 3Ds.
- You can specify min and max time for the plot(s).
- Optional gridlines on the seismic plot.
- A colourbar for variable density plots.
- A highlight colour, applied to the histogram, spectrum, titles, and intersection lines.


Credits
-------

*Made with love and silliness by Evan and Matt at* `Agile <http://agilegeoscience.com>`_
