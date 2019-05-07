

reStructuredText
================

Document Layout
---------------

General
~~~~~~~
There shall be two blank lines at the start of each document. There shall be three blank lines at the end of each document.

Headings
~~~~~~~~
There should be one blank line between sections of the same level (e.g. H1 -- H1) and between a section and a sub-section (e.g. H1 -- H2). There should be two blank lines between a sub-section and a greater section (e.g. H2 -- H1). There should be no blank line between a heading and the section's contents, where contents exist::

   Section
   =======
   contents

   Sub-section
   -----------
   contents


   Next Section
   ============
   
   Sub-section
   -----------
   contents

The following symbols should be used for headings::

   H1 ===
   H2 ---
   H3 ~~~
   H4 +++
   H5 ^^^

Only top-level headings should use Title Case. Sub-headings should use Sentence case.


Links
-----

Internal links
~~~~~~~~~~~~~~
::

   :ref:`text <folder/docname:heading>`

External links
~~~~~~~~~~~~~~
::

   `text <URL>`_


Admonitions
-----------
Admonitions are specially marked topics or notes which appear inline with other content. They can be styled with custom CSS.

Standard
~~~~~~~~
::

   Example: 

   .. attention:: This is an attention admonition.

.. attention:: This is an attention admonition.
.. caution:: This is a caution admonition.
.. danger:: This is a danger admonition.
.. error:: This is an error admonition.
.. hint:: This is a hint admonition.
.. important:: This is an important admonition.
.. note:: This is a note admonition.
.. tip:: This is a tip admonition.
.. warning:: This is a warning admonition.

Custom
~~~~~~
::

   Example:

   .. admonition:: This is a Custom Admonition

      And this is its content.


.. admonition:: This is a Custom Admonition
   
   And this is its content.


References
----------
::

   The quick brown fox jumped over the lazy [#chapman]_ dog.

   .. [#chapman] Chapman, B. et al. (2019) The laziness of the common dog. Journal. Issue. DOI.


The quick brown fox jumped over the lazy [#chapman]_ dog.

.. [#chapman] Chapman, B. et al. (2019) The laziness of the common dog. Journal. Issue. DOI.


Images
------
::

   .. image:: images/image_name.png


Figures
-------
::

   .. figure:: /images/figure_name.png
      :align: center

      This is the descriptive text for the figure.