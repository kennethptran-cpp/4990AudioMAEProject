You do not need to install Python, configure environments, or own a dedicated graphics card to run this experiment. 
Step 1: Open Google Colab
1. Go to [Google Colab](https://colab.research.google.com/).
2. Sign in with any standard Google account.

Step 2: Upload the Notebook
1. In the Colab interface, click on File > Upload notebook in the top navigation bar.
2. Drag and drop the `.ipynb` file from this GitHub repository into the upload window.

Step 3: Enable the GPU (Crucial Step)
Vision Transformers require hardware acceleration to compile and train effectively. 
1. In the top menu, go to Runtime > Change runtime type.
2. Under the "Hardware accelerator" dropdown, select T4 GPU (or any available GPU).
3. Click Save.

Step 4: Execute the Pipeline
1. Go to Runtime > Run all.
2. The notebook will sequentially download the required datasets (ESC-50 and GTZAN), fetch the pre-trained model weights, apply our custom software patches to the source code, and initiate the hardware simulations.


Expected System Behavior & Hardware Limitations
Please note that this notebook acts as a **Hardware Stress Test**. 

When the execution reaches the "Constrained Edge Simulation" cells (where batch sizes are restricted to simulate embedded memory limits), the system may experience severe processing latency, DataLoader bottlenecks, or `CUDA Out of Memory` (OOM) faults. 

This is not the intended result of the experiment but it demonstrates our core finding: the 86-million parameter footprint of the ViT-Base encoder is fundamentally too large for native, unoptimized edge deployment. This repository serves as proof that aggressive model compression (such as INT8 quantization or structural pruning) is likely required to run on edge devices.
