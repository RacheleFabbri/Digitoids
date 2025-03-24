README.txt
The folder contains the following file:
1. 'adapthr_spikedetection.m': fucntion for detecting spikes with the adaptive threshold
2. 'buildDigitoids.m': starting from Models_data.m this scritp creates the correspondent Digitoids Simulink scheme positioning the neuron blocks, wiring them and putting the desired weights.
3. 'buildNoOxygenModel.m':tarting from Models_data.m this scritp creates the correspondent oxygen-independent model Simulink scheme positioning the neuron blocks, wiring them and putting the desired weights.
4. 'metrics_analysis.m': suggested pipeline for analysing the output of the simulated Digitoids and oxygen-independent models
5. 'Models_data.mat': the data of the experimental network layout identified in the paper "Ballesteros-Esteban, L. M., et al. "Self-organization and evolution of structure and function in cultured neuronal networks." Chaos, Solitons & Fractals 173 (2023): 113764." and processed with the Watts-Strogatz function by MATLAB (the user can define different network layouts using the same metrics defined in Models_data).
6. 'neuron.m': MATLAB function called within the single neuron block in the Simulink Neuron library. It defines the oxygen-dependent model of firing and metabolism, as described in the paper.
7. 'Neuron_lib.slx': this is the Simulink library where the single neuron blocks are defined. Each user can tune and define further blocks or modify the existing to tailor the desired characteristics.
8. 'neuronNOdiff': Hodgkin-Huxley model with no dependence on energetic considerations
9. 'oxygen_diff.m': MATLAB function called within the single neuron block in the Simulink Neuron library. It defines the diffusion of oxygen across the column of medium above the neuron and its triggering by the single neuron consumption, as described in the paper.
10. 'oxygen_NOdiff.m': fictious diffusion of oxygen (diffusion coefficient is 0) to have the same architecture as the oxygen-dependent model
11. 'sl_customization.m': function to be called before using the Neuron library to see it appear at the top of the Simulink Library browser
12. 'slblocks.m': function to be called before using the Neuron Library to see it appear with the desired name in the Simulink Library browser

--------------------------------------------------------------------------------------------

Istructions for running your own simulations:

1) Download and unzip the data to your FILE FOLDER
2) Open MATLAB and go to your FILE FOLDER
3) Run 'sl_customization.m'
4) Run 'slblocks.m' (if here or at 3) some errors rise, please ignore them)

Now you can define the Digitoids Simulink scheme:
1) Running the 'buildDigitoids.m' script you create the Digitoids with the same layout as in the experimental data used to validate the model (stored in 'Models_data.mat' file). You can also define your own models and layouts and tune the input parameters of the neurons in this script (medium height, oxygen concentration, ...)
2) Each Digitoids is saved as a Simulink scheme in the FILE FOLDER and then you can simulate them. The output of each simulation is a variable 'out' where the values of time, oxygen concentration and membrane potential are stored for each neuron of the Digitoid.
3) To run the analysis you can use the script 'metrics_analysis.m', but you can also define your own analysis pipeline.