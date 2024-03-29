SVGDreamer
===============

.. _svgdreamer:

`[Project] <https://ximinng.github.io/SVGDreamer-project/>`_ `[Paper] <https://arxiv.org/abs/2312.16476>`_ `[Code] <https://github.com/ximinng/SVGDreamer>`_

The SVGDreamer algorithm was proposed in *SVGDreamer: Text Guided SVG Generation with Diffusion Model*.

The abstract from the paper is:

`Recently, text-guided scalable vector graphics (SVGs) synthesis has shown promise in domains such as iconography and sketch. However, existing text-to-SVG generation methods lack editability and struggle with visual quality and result diversity. To address these limitations, we propose a novel text-guided vector graphics synthesis method called SVGDreamer. SVGDreamer incorporates a semantic-driven image vectorization (SIVE) process that enables the decomposition of synthesis into foreground objects and background, thereby enhancing editability. Specifically, the SIVE process introduce attention-based primitive control and an attention-mask loss function for effective control and manipulation of individual elements. Additionally, we propose a Vectorized Particle-based Score Distillation (VPSD) approach to tackle the challenges of color over-saturation, vector primitives over-smoothing, and limited result diversity in existing text-to-SVG generation methods. Furthermore, on the basis of VPSD, we introduce Reward Feedback Learning (ReFL) to accelerate VPSD convergence and improve aesthetic appeal. Extensive experiments have been conducted to validate the effectiveness of SVGDreamer, demonstrating its superiority over baseline methods in terms of editability, visual quality, and diversity.`

Examples of VPSD
^^^^^^^^^^^

SVGDreamer generates various styles of SVG based on text prompts. It supports the use of six vector primitives, including Iconography, Sketch, Pixel Art, Low-Poly, Painting, and Ink and Wash.

**Note: The examples provided here are based on VPSD only.**

Iconography
""""""""""""

Synthesize the SVGs of the Sydney Opera House in the style of Van Gogh's oil paintings,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='Sydney Opera House. oil painting. by Van Gogh' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 x.num_paths=512 result_path='./svgdreamer/SydneyOperaHouse'

You will get the following result:

.. image:: ../../examples/svgdreamer/icon_sydney_opera_house_1.png
.. image:: ../../examples/svgdreamer/icon_sydney_opera_house_2.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>The oil paintings of Sydney Opera House by Van Gogh's. iconography. Number of vector particles: 6</p>

------------

Synthesize a German shepherd in vector art,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='A colorful German shepherd in vector art. tending on artstation.' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 result_path='./svgdreamer/GermanShepherd'

You will get the following result:

.. image:: ../../examples/svgdreamer/icon_GermanShepherd_1.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>German shepherd in vector art. iconography. Number of vector particles: 6</p>

------------

Synthesize a ship on the high sea,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='Seascape. Ship on the high seas. Storm. High waves. Colored ink by Mikhail Garmash. Louis Jover. Victor Cheleg' save_step=60 x.guidance.n_particle=4 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=4 x.num_paths=512 result_path='./svgdreamer/ship'

You will get the following result:

.. image:: ../../examples/svgdreamer/icon_ship_1.png
.. image:: ../../examples/svgdreamer/icon_ship_randT_1.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>A ship on the high sea. iconography. Number of vector particles: 4</p>

Sketch
""""""""""""

Synthesize the free-hand sketches of the Lamborghini,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='A free-hand drawing of A speeding Lamborghini. black and white drawing.' x.style='sketch' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 x.num_paths=128 result_path='./svgdreamer/Lamborghini'

You will get the following result:

.. image:: ../../examples/svgdreamer/sketch_Lamborghini_1.png
.. image:: ../../examples/svgdreamer/sketch_Lamborghini_randT_1.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>Lamborghini. sketch. Number of vector particles: 6</p>

------------

Synthesize the free-hand sketches of elephants,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='a freehand drawing of an elephant. white background. minimal 2d line drawing. trending on artstation.' x.style='sketch' save_step=60 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 x.num_paths=256 x.guidance.t_schedule='randint' result_path='./svgdreamer/sketch_elephant' multirun=True

You will get the following result:

.. image:: ../../examples/svgdreamer/sketch_elephant_P256.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>Elephants. sketch. Number of vector particles: 6</p>

Pixel Art
""""""""""""

Synthesize German shepherds in vector art,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='Darth vader with lightsaber. ultrarealistic.' x.style='pixelart' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 result_path='./svgdreamer/DarthVader'

You will get the following result:

.. image:: ../../examples/svgdreamer/pixelart_DarthVader_1.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>Darth vader. pixel art. Number of vector particles: 6</p>

Low-Poly
""""""""""""

Synthesize bald eagles in low-poly,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='A picture of a bald eagle. low-ploy. polygon' x.style='low-poly' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 result_path='./svgdreamer/eagle'

You will get the following result:

.. image:: ../../examples/svgdreamer/lowpoly_eagle_1.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>Bald eagle. low-poly. Number of vector particles: 6</p>

------------

Synthesize scarlet macaws in low-poly,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='A picture of a scarlet macaw. low-ploy. polygon' x.style='low-poly' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 result_path='./svgdreamer/ScarletMacaw'

You will get the following result:

.. image:: ../../examples/svgdreamer/lowpoly_ScarletMacaw.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>Scarlet Macaw. low-poly. Number of vector particles: 6</p>

Painting
""""""""""""

Synthesize phoenixes coming out of the fire drawing,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='a phoenix coming out of the fire drawing. lineal color. trending on artstation.' x.style='painting' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 x.num_paths=384 result_path='./svgdreamer/phoenix'

You will get the following result:

.. image:: ../../examples/svgdreamer/painting_phoenix_1.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>Phoenixes. Painting. Number of vector particles: 6</p>

------------

Synthesize self-portraits of Van Gogh,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='self portrait of Van Gogh. oil painting. cmyk portrait. multi colored. defiant and beautiful. cmyk. expressive eyes.' x.style='painting' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 x.num_paths=1500 result_path='./svgdreamer/VanGogh_portrait'

You will get the following result:

.. image:: ../../examples/svgdreamer/painting_VanGogh_portrait.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>self-portraits of Van Gogh. Painting. Number of vector particles: 6</p>

Ink and Wash
""""""""""""

Synthesize the Big Wild Goose Pagoda,

.. code-block:: console

   $ python svg_render.py x=svgdreamer prompt='Big Wild Goose Pagoda. ink style. Minimalist abstract art grayscale watercolor.' x.style='ink' save_step=30 x.guidance.n_particle=6 x.guidance.vsd_n_particle=4 x.guidance.phi_n_particle=2 x.guidance.t_schedule='max_0.5_2000' x.num_paths=128 x.width=6 result_path='./svgdreamer/BigWildGoosePagoda'

You will get the following result:

.. image:: ../../examples/svgdreamer/ink_BigWildGoosePagoda_1.png
.. image:: ../../examples/svgdreamer/ink_BigWildGoosePagoda_2.png
.. raw:: html

    <p style="text-align: center;"><strong>Fig. </strong>Big Wild Goose Pagoda. Ink and Wash. Number of vector particles: 6</p>