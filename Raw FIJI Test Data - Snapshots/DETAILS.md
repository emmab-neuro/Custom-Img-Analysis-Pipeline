# $\color{blue}{\text{Experiment}}$

Identify and quantify any significant differences in the structure of specific synapses in control vs. disease.

- **Where is the raw data coming from?**

  Images of synapses in neural tissue
- **How are synapse types and subtypes differentiated within images?**

  Specific pairings (or 2 or more overlapping signals) of immunolabelled presynaptic and postsynaptic proteins within an image (aka protein colocalization)

  Example: Synaptophysin signal overlapping with PSD95 signal(s) = a ubiquitous excitatory synapse
- **What variables are used to quantify synaptic structure?**

  density, number, size

# $\color{purple}{\text{Purpose of this Pipeline}}$
Using custom FIJI macros and Python scripts, this pipeline eliminates the need to copy-n-paste hundreds of lines of data into Excel, reducing analysis time and human error. 

It runs statistical analysis in less than 60 seconds whereas this can take weeks when done by hand. 

Manual image processing (thresholding and binarization) is still required in FIJI, but the custom macros speed up this process and while keeping variable measurements for each signal in separate Excel sheets. 

# $\color{red}{\text{Experimental Parameters}}$

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
  - be separated by signal into separate Excel sheets
  - for each image, contain the variable measurements for each signal (regardless of any pairings) AND for the signal when factoring in colocalizations
  - be transfered from FIJI to Excel in the same order as the images listed in the key
