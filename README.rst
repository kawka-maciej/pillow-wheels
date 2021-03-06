Pillow Wheel Builder
====================

This repository creates wheels for tagged versions of Pillow::

    ./update-pillow-tag.sh <VERSION>

.. image:: https://img.shields.io/travis/python-pillow/pillow-wheels/master.svg
   :target: https://travis-ci.org/python-pillow/pillow-wheels
   :alt: Travis CI build status (wheels)

Archives
--------

https://github.com/python-pillow/pillow-depends contains archives for libraries
that will be built as part of the Pillow build.

In general, there is no need to put library archives there, because the
``multibuild`` scripts will download them from their respective URLs.

But, the build will look in that repository before downloading from the
URL, so if there is a library that often fails to download, or you think might
fail to download, then download it and add it to the Git repository.

See the ``pre_build`` in ``config.sh`` and the ``fetch_unpack`` routine in
``multibuild/common_utils.sh`` for the logic, and the build recipes in
``multibuild/library_builders.sh`` for the filename to give to the downloaded
archive.

Dependencies
------------

NumPy
~~~~~

Check minimum NumPy versions to build against in ``.travis.yml`` file. Build against the
earliest NumPy that Pillow is compatible with; see
`forward, backward NumPy compatibility <https://stackoverflow.com/questions/17709641/valueerror-numpy-dtype-has-the-wrong-size-try-recompiling/18369312#18369312>`_

Wheels
------

Wheels are uploaded to https://github.com/python-pillow/pillow-wheels/releases.
Credentials are encrypted to this specific repo in the ``.travis.yml`` file,
so the upload won't work from another repository.

PyPI
~~~~

Download wheels from the
`latest release <https://github.com/python-pillow/pillow-wheels/releases>`_ and upload
to PyPI::

    twine upload Pillow-<VERSION>-*