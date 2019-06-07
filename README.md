# Model-Based Product-Line Regression Testing of Variants and Versions of Variants
This repository provides the download of the prototypical implementation as well as the experimental data for the PhD thesis "Model-Based Product-Line Regression Testing of Variants and Versions of Variants" by Sascha Lity submitted to [Carl-Friedrich-Gauß-Fakultät](https://www.tu-braunschweig.de/fk1/index.html) of [Technische Universität Carolo-Wilhelmina zu Braunschweig](https://www.tu-braunschweig.de/) (Under Review).

The prototype is part of the tool support of the research project [IMoTEP](http://www.dfg-spp1593.de/imotep/).
The IMoTEP project focuses on efficient and effective model-based testing of evolving (dynamic) software product lines.

## Download
* [Eclipse Modeling Tools Photon](https://www.eclipse.org/downloads/packages/release/photon/r/eclipse-modeling-tools) for accessing the data obtained by the application of the prototype to the input data.
* [Meta-model](Metamodel_plugins) Eclipse plugins representing the data structure of our prototype. The plugins are required to access the input and result XMI files of the subject SPL systems (Wiper, Vending Machine & Mine Pump) in an installed [Eclipse](https://www.eclipse.org/downloads/packages/release/photon/r/eclipse-modeling-tools) instance.
<!--* [Prototypical implementation](prototype.jar) of our framework facilitating SPL regression testing.-->
<!--* [Input](Input) files of the vending machine and wiper SPL comprising 1. the XMI file with the feature model versions and respective feature configurations ([VendingMachineNEARIN.xmi](Input/VendingMachineNEARIN.xmi) & [WiperNEARIN.xmi](Input/WiperNEARIN.xmi)) and 2. the XMI file with the higher-order delta model ([HODModel_vm.xmi](Input/HODModel_vm.xmi) & [HODModel_wiper.xmi](Input/HODModel_wiper.xmi))-->
<!--* [Result](Result) files of the vending machine as well as wiper SPL comprising the XMI file (*.regression) with the respective test artifacts.-->
<!--* [Meta-model](Meta_Model_Plugins) Eclipse plugins representing the data structure of our prototype. The plugins are required to access the input and result XMI files of the subject SPL systems (Vending Machine & Wiper) in an installed Eclipse instance.-->

## Data Access
To access the data used as input and obtained by applying our prototype, the download and installation of Eclipse modeling tools is required. In addition, the meta model plugins (*.jar files) have to be added to the plugins folder of the installed Eclipse instance. Afterwards, start the Eclipse instance, create an empty project, and add the input as well as the already obtained result files to the project. The files can be opened via the sample ecore model editor.
```
"Right click on File" --> "Open with" --> "Other.." --> "Sample Ecore Model Editor"
```
## Prototype Execution
For executing the prototype of our framework, we require as parameters 1. the project name (*projectName*), 2. the path to the XMI file comprising the feature model and feature configuration versions (*pathToFMandConfig*), 3. the path to the XMI file containing the higher-order delta model (*pathToHOD*), and 4. the path to the output folder (*pathToOutput*). As the prototype prints information on the command line, we suggest to pipe the command line output to a separate log file facilitating an easier review of the execution. In addition, the execution of the included test-case generator requires a specific amount of heap memory, where we suggest 10GB if possible. To this end, the prototype is executed via the command
```
java -Xmx10000M -jar prototype.jar projectName pathToFMandConfig pathToHOD pathToOutput > eval.log 2>&1
```
