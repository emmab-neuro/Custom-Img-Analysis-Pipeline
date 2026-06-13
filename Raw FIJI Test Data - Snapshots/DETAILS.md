# $\color{blue}{\text{Experiment}}$

Identify and quantify any significant differences in the structure of specific synapses in control vs. disease.

- **Where is the raw data coming from?**

  Images of synapses in neural tissue
- **How are synapse types and subtypes differentiated within images?**

  Specific pairings (2 or more overlapping signals) of immunolabelled presynaptic and postsynaptic proteins within an image (aka protein colocalization)

  Example: Synaptophysin signal (orange) overlapping with PSD95 signals (blue) = a ubiquitous excitatory synapse

<p align="center">
  <img width="128" height="120" alt="Synapse Example" src="https://github.com/user-attachments/assets/1f3d4198-9b1b-4fb8-9278-3bdf352fe25d" />
</p>
  
- **What variables are being used to quantify synaptic structure?**

  density, number, size
- **How are these variables obtained from the images?**

  keep reading!

# $\color{purple}{\text{Raw Image Data Collection}}$
  FIJI keeps each fluorescent signature within an image separated within its own color channel. This is called a "hyperstack". In other words, one image contains multiple overlayed channels separated by color.

  Measurements, like area or signal intensity, are calculated for all signals but only for one color channel at a time. However, you can also specify if you want these measurements calculated only for signals that overlap with signals in another color channel. That way, we can make sure that we're calculating variables for specific synapses.

  For example, if we want to measure the area of the ubiquitous excitatory synapses referenced above, we can first ask FIJI to measure the areas of Synaptophysin signals (orange color channel) but only those that are colocalized with PSD95 signals (blue color channel). This ensures that we're only measuring the presynaptic areas of these particular ubiquitous synapses. We can also do this for the postsynaptic areas, and there is even a way to match up individual signals in one channel with the signals they overlap with in another channel.

  FIJI generates channel calculations in a separate results window. Density is obtained by dividing signal area by total image area. Size is characterized by 2D area, and number is of course signal count.

# $\color{red}{\text{Purpose of this Pipeline}}$
Using custom FIJI macros and Python scripts, this pipeline eliminates the need to copy and paste hundreds of lines of data from the FIJI results window into Excel, reducing analysis time and human error. 

It runs statistical analysis in less than 60 seconds whereas this can take weeks when done by hand in Excel. 

Manual image processing (thresholding and binarization) is still required in FIJI, but the custom macros speed up this process while keeping variable measurements for each signal in separate Excel sheets. 

# $\color{orange}{\text{Experimental Parameters}}$

- n<sub>1 </sub>= # of images (CZI files) per test group
- n<sub>2 </sub>= # of subjects per test group
- researcher should be blinded to any identifiers for the control vs. disease group
   - there should be a CSV or XLSX sheet that contains the identifying info the researcher is blinded to - this key is necessary for analysis and must be uploaded into Jupyter Notebook along with the raw image data
   - example:

|ID #|Group|
|---|---|
|1234| Control |
|5678| Disease |

- the raw image data must:
  - be transfered from FIJI to Excel via the Read & Write Excel plugin
  - remain organized by the fluorescent signature measured, funneling these signal-specific results, including any colocalization data, into distinct Excel sheets
    - Example: one Excel sheet contains the areas of all Synaptophysin signals as well as only Synaptophysin signals colocalized with PSD95 for each image 
  - be transfered from FIJI to Excel in the same order as the images listed in the key

# $\color{gold}{\text{Files}}$

The "TEST_FIJI-EXPORTS" CSV files show sample raw image data that was sent from FIJI to specific sheets within one Excel file based on the color channel measured. Sheets were separated by the signal (or color channel) measured.
- The sample data in these files show results from 2 images that each contained 3 color channels.
    - S1 means signal 1, S2 means signal 2, and so forth
- The top row of each file again indicates which signal is being measured for each image. "Mask of" just refers to the binarization part from the image processing
- The second row indicates the variables measured
    - "Label" - indicates whether the variables correspond with all signals within the channel (if the signal labels match the top row) or only signals colocalized with another channel's signals (if the signal labels do NOT match the top row)
    - "Area" - the area of each signal within the channel
    - "Mean" - mean intensity of each signal (0-255)
        - signals not colocalized with another channel's signals have a mean intensity of 0, and this is a way to filter out the non-colocalized signals
- For this sample data, each image contains three result "blocks" per signal: measurements for all signals and measurements for only signals colocalized with another channel's signals (two other channels).
