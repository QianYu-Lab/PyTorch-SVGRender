Word-As-Image
===============

.. _wordasimage:

`[Project] <https://wordasimage.github.io/Word-As-Image-Page/>`_ `[Paper] <https://arxiv.org/abs/2303.01818>`_ `[Code] <https://github.com/Shiriluz/Word-As-Image>`_

The Word-As-Image algorithm was proposed in *Word-As-Image for Semantic Typography*.

The abstract from the paper is:

`A word-as-image is a semantic typography technique where a word illustration presents a visualization of the meaning of the word, while also preserving its readability. We present a method to create word-as-image illustrations automatically. This task is highly challenging as it requires semantic understanding of the word and a creative idea of where and how to depict these semantics in a visually pleasing and legible manner. We rely on the remarkable ability of recent large pretrained language-vision models to distill textual concepts visually. We target simple, concise, black-and-white designs that convey the semantics clearly. We deliberately do not change the color or texture of the letters and do not use embellishments. Our method optimizes the outline of each letter to convey the desired concept, guided by a pretrained Stable Diffusion model. We incorporate additional loss terms to ensure the legibility of the text and the preservation of the style of the font. We show high quality and engaging results on numerous examples and compare to alternative techniques.`

**Examples:**

Word-As-Image follows a text prompt to style a letter in a word.

Inject the meaning of the word *bunny* into the 'Y' in the word 'BUNNY':

.. code-block:: console
    
   $ python svg_render.py x=wordasimage x.word='BUNNY' prompt='BUNNY' x.optim_letter='Y'

You will get the following result:

.. image:: ../../examples/wordasimage/wordasimage_BUNNY_Y.svg
   :width: 224