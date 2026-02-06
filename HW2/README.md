Virtual detectors in 4D-STEM revolutionize imaging by shifting the definition of the detector from hardware to software. In a traditional STEM setup, a physical detector (like a Bright-Field or Annular Dark-Field detector) is fixed in the microscope column, and the signal is integrated into a single value as the beam scans. Once the data is collected, the "type" of image is permanent.

##Post-Acquisition "Re-playing" of the Experiment

Because 4D-STEM records the full 2D diffraction pattern (DP) at every single 2D scan position $(x, y)$, the raw data contains nearly all the information about how electrons interacted with the sample.

Virtual detectors enable "re-playing" the experiment through the following mechanism:

Software-Defined Geometry: Instead of being limited by a physical diode's shape, you create a "mask" or "filter" in software (such as a circle, a ring, or even custom segments) that represents a virtual detector.

Retrospective Integration: The software iterates through every pixel in the 4D dataset and multiplies the recorded diffraction pattern by the virtual mask. The intensity values within the mask are summed to produce a single pixel value for a new 2D image.

Infinite Iteration: Since the raw 4D data is preserved, you can redefine the inner and outer radii of the detector geometry as many times as needed after the sample has been removed from the microscope.

##Enabling New Imaging Modes

This flexibility allows researchers to generate multiple types of contrast from a single scan:

Bright Field (BF): By placing a virtual mask over the central transmitted beam.

Annular Dark Field (ADF): By selecting a virtual ring that captures scattered electrons.

Phase Contrast: By using more complex geometries, such as split-detectors or Center of Mass (CoM) analysis, which were previously impossible without specialized hardware.
