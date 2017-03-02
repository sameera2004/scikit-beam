.. current module:: skbeam.roi

ROI(Region of Interests)
=======================


Scikit-beam roi module contain convenience methods to generate ROI labeled array for simple
shapes and some helper functions to see the statistics of the speckle data.'

ROI labeled arrays
------------------
Rings
+++++

Segmented Rings
^^^^^^^^^^^^^^^

.. code-block:: python

    import skbeam.core.roi as roi

    first_q = 5.0  # inner radius of the inner-most ring
    delta_q = 5.0  #ring thickness
    num_rings = 4  # number of rings

    slicing = 4 # number of pie slices or list of angles in radians
    spacing = 4 # margin between rings, 0 by default
    img_shape = (150, 150)

    # inner and outer radius for each ring
    edges = roi.ring_edges(first_q, width=delta_q, spacing=spacing,
                           num_rings=num_rings)

    label_array = roi.segmented_rings(edges, slicing, center,
                                      img_shape, offset_angle=0)


.. plot::

    import matplolib.pyplot as plt
    import skbeam.core.roi as roi
    import xray_vision.mpl_plotting as mpl_plot

    first_q = 5.0  # inner radius of the inner-most ring
    delta_q = 5.0  #ring thickness
    num_rings = 4  # number of rings

    slicing = 4 # number of pie slices or list of angles in radians
    spacing = 4 # margin between rings, 0 by default
    img_shape = (150, 150)

    # inner and outer radius for each ring
    edges = roi.ring_edges(first_q, width=delta_q, spacing=spacing,
                           num_rings=num_rings)

    label_array = roi.segmented_rings(edges, slicing, center,
                                      img_shape, offset_angle=0)

    # plot the figure
    fig, axes = plt.subplots(figsize=(6, 5))
    axes.set_title("Segmented Rings")
    axes.set_xlim(38, 120)
    axes.set_ylim(38, 120)
    im = mpl_plot.show_label_array(axes, label_array, cmap)
    plt.show()




Rectangles
++++++++++

Lines
+++++

Boxes
+++++

Bars
++++

Statistic tests for speckle data
--------------------------------
