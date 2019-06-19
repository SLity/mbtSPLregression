# Model-Based Product-Line Regression Testing of Variants and Versions of Variants
This repository provides the download of the prototypical implementation as well as the experimental data for the PhD thesis "Model-Based Product-Line Regression Testing of Variants and Versions of Variants" by Sascha Lity submitted to [Carl-Friedrich-Gauß-Fakultät](https://www.tu-braunschweig.de/fk1/index.html) of [Technische Universität Carolo-Wilhelmina zu Braunschweig](https://www.tu-braunschweig.de/) (Under Review).

The prototype is part of the tool support of the research project [IMoTEP](http://www.dfg-spp1593.de/imotep/).
The IMoTEP project focuses on efficient and effective model-based testing of evolving (dynamic) software product lines.

## Input and Result Data
### Download
* [Eclipse Modeling Tools Photon](https://www.eclipse.org/downloads/packages/release/photon/r/eclipse-modeling-tools) for accessing the data obtained by the application of the prototype to the input data.
* [Meta Model Eclipse Plugins](Metamodel_plugins) Eclipse plugins representing the data structure of our prototype. The plugins are required to access the input and result XMI files of the subject SPL systems (Wiper, Vending Machine & Mine Pump) in an installed [Eclipse](https://www.eclipse.org/downloads/packages/release/photon/r/eclipse-modeling-tools) instance.
* [Input & Result](PhD_thesis_data) files of the wiper, vending machine, and mine pump SPL encapsulated in an eclipse project. The project comprises for each SPL 1. the XMI file with the feature model versions and respective feature configurations ([WiperNEARIN.xmi](PhD_thesis_data/Wiper/WiperNEARIN.xmi), [VendingMachineNEARIN.xmi](PhD_thesis_data/VendingMachine/VendingMachineNEARIN.xmi) & [MinePumpNEARIN.xmi](PhD_thesis_data/MinePump/MinePumpNEARIN.xmi)), 2. the XMI file with the higher-order delta model ([HODModel_wiper.xmi](PhD_thesis_data/Wiper/HODModel_wiper.xmi), [HODModel_vm.xmi](PhD_thesis_data/VendingMachine/HODModel_vm.xmi) & [HODModel_mp.xmi](PhD_thesis_data/MinePump/HODModel_mp.xmi)), and 3. the XMI file of the wiper, vending machine as well as mine pump SPL comprising the reulst with the respective test artifacts ([Wiper.regression](PhD_thesis_data/Wiper/Wiper.regression), [VendingMachine.regression](PhD_thesis_data/VendingMachine/VendingMachine.regression) & [MinePump.regression](PhD_thesis_data/MinePump/MinePump.regression)).

### Data Access
To access the data used as input and obtained by applying our prototype, the download and installation of [Eclipse Modeling Tools](https://www.eclipse.org/downloads/packages/release/photon/r/eclipse-modeling-tools) is required. In addition, the [meta model plugins](Metamodel_plugins) (*.jar files) have to be added to the plugins folder of the installed Eclipse instance. Afterwards, start the Eclipse instance, and import the provided [eclipse project](PhD_thesis_data) comprising the input as well as the already obtained result files. The files can be opened via the sample ecore model editor.
```
"Right click on File" --> "Open with" --> "Other.." --> "Sample Ecore Model Editor"
```

<!--* [Prototypical implementation](prototype.jar) of our framework facilitating SPL regression testing.-->
## Evaluation and Prototype Execution
### Download
* [ComputeKeyParameters.jar](Jar/ComputeKeyParameters.jar): Executable Jar to compute all key parameters of the three subject SPLs, e.g., number of versions, number of deltas, average size of state machine test models etc.
* [SlicingEvaluation.jar](Jar/SlicingEvaluation.jar): Executable Jar to perform the slicing evaluation.
* [HodReasoningEvaluation.jar](Jar/HodReasoningEvaluation.jar): Executable Jar to perform the evaluation of the reasoning about higher-order delta applications.

### Computing Key Parameters
For executing the jar, we require as parameters 1. the project name (*projectName*), 2. the path to the XMI file comprising the feature model and feature configuration versions (*pathToFMandConfig*), and 3. the path to the XMI file containing the higher-order delta model (*pathToHOD*). As the ouput is printed on the command line, we suggest to pipe the command line output to a separate log file facilitating an easier review of the execution. The jar is exexuted via the command
```
java -jar ComputeKeyParameters.jar projectName pathToFMandConfig pathToHOD > eval.log 2>&1
```

### Incremental Slicing Evaluation
For executing the jar, we require as parameters 1. the project name (*projectName*), 2. the path to the XMI file comprising the feature model and feature configuration versions (*pathToFMandConfig*), 3. the path to the XMI file containing the higher-order delta model (*pathToHOD*), 4. the number of the SPL version for which the evaluation is to be executed (*versionNum*), 5. the amount of repetitions for the slicing evaluation (*repetitions*), and 6. the output directory for the generated CSV files comprising the time values required for the application of slicing (*outputPath*). As some additional ouput is printed on the command line, we suggest to pipe the command line output to a separate log file facilitating an easier review of the execution. The jar is exexuted via the command
```
java -jar SlicingEvaluation.jar projectName pathToFMandConfig pathToHOD versionNum repetitions outputPath> eval.log 2>&1
```

### Evaluation of Reasoning about Higher-Order Delta Application
For executing the jar, we require as parameters 1. the project name (*projectName*), 2. the path to the XMI file comprising the feature model and feature configuration versions (*pathToFMandConfig*), 3. the path to the XMI file containing the higher-order delta model (*pathToHOD*), 4. the amount of repetitions for the evaluation of the higher-order delta application reasoning (*repetitions*), and 5. the output directory for the generated CSV files comprising the time values required for the application of higher-order delta application reasoning (*outputPath*). As some additional ouput is printed on the command line, we suggest to pipe the command line output to a separate log file facilitating an easier review of the execution. The jar is exexuted via the command
```
java -jar HodReasoningEvaluation.jar projectName pathToFMandConfig pathToHOD repetitions outputPath> eval.log 2>&1
```

<!--### Prototype Execution
For executing the prototype of our framework, we require as parameters 1. the project name (*projectName*), 2. the path to the XMI file comprising the feature model and feature configuration versions (*pathToFMandConfig*), 3. the path to the XMI file containing the higher-order delta model (*pathToHOD*), and 4. the path to the output folder (*pathToOutput*). As the prototype prints information on the command line, we suggest to pipe the command line output to a separate log file facilitating an easier review of the execution. In addition, the execution of the included test-case generator requires a specific amount of heap memory, where we suggest 10GB if possible. To this end, the prototype is executed via the command
```
java -Xmx10000M -jar prototype.jar projectName pathToFMandConfig pathToHOD pathToOutput > eval.log 2>&1
```
-->
