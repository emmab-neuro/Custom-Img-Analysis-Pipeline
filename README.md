# Custom-Img-Analysis-Pipeline
I will be improving my original data pipeline that I used for my master's project using realistic test data. The pipeline is structured slightly inefficiently to accommodate for project adjustments, and I want to create a more seamless pipeline now that the order of operations has been established.

_**GOAL: clean up Python scripts and eliminate the need for more than 1 intermediary Excel file within the pipeline**_

# $\color{blue}{\text{Folders}}$

1. $\color{Turquoise}{\text{Raw FIJI Test Data - Snapshots}}$ : samples of raw image data to be processed in the pipeline
2. $\color{aquamarine}{\text{Primary Processing}}$ :
   - Python scripts that import the raw image data to Jupyter Notebook and export the processed results to Excel
   - CSV files showing the exported results that were sent to each Excel sheet

4. $\color{Gold}{\text{Final Analysis}}$ :
   - Python scripts that import the previously processed results (the exports from Primary Processing) to Jupyter Notebook and export the final statistical analysis to Excel
   - CSV files showing the final exported statistical findings that were sent to each Excel sheet

# The Pipeline

Software Workflow

```mermaid
graph TD;
    subgraph ide1 ["ACTIVE USER WORKSPACE"]
    A[Airyscan]== CZIs ===> B["FIJI (IJM w/ Read & Write Excel plugin)"]
    B["FIJI (IJM w/ Read & Write Excel plugin)"]-.-x D["Jupyter Notebook (IPYNB)"]
    end

    subgraph ide2 ["STORAGE INTERMEDIARY"]
    B["FIJI (IJM w/ Read & Write Excel plugin)"]== bridge XLSX ===> C[Excel]
    C[Excel]===> D["Jupyter Notebook (IPYNB)"]
    D["Jupyter Notebook (IPYNB)"]== bridge XLSX ===> C[Excel]
    end

    D["Jupyter Notebook (IPYNB)"]== final XLSX ==> E[Excel]
    C[Excel]== data copied to clipboard ==> F[SPSS]

    subgraph ide3 ["final stats"]
    E[Excel]
    F[SPSS]
    end

    style ide1 fill:#99f,stroke:#f73,stroke-width:4px,color:#fff,font-size: 16
    style ide2 fill:#19f,stroke:#00f,stroke-width:4px,color:#fff,font-size: 16,stroke-dasharray: 10 5
    style E fill:#9f9,stroke:#0d9,stroke-width:4px,color:#000
    style F fill:#9f9,stroke:#0d9,stroke-width:4px,color:#000
```
