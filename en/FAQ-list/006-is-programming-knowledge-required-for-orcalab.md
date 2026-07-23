# Is programming knowledge required to use OrcaLab?

## Question
OrcaLab is a high-fidelity physics AI simulation system. For beginners, is programming knowledge required to use it?

## Answer

OrcaLab embraces the core philosophy of "Goodbye complex code — robot training techniques anyone can learn" and aims to lower the barrier to entry for robot virtual simulation training. Therefore, **deep programming knowledge is not strictly required for basic functionality**, but having some programming knowledge will greatly expand your scope of use and capabilities.

## 💡 Requirements by User Level

### 🟢 Users with Zero Programming Experience

#### Applicable Scenarios
- **Quick Start**: Experience the core functionality of OrcaLab.
- **Scene Building**: Drag and drop assets through the graphical interface to build simulation scenes.
- **Physical Interaction**: Manually manipulate objects in the simulation and observe physical effects.
- **Teaching Demonstrations**: Use as a teaching tool to demonstrate physics simulation principles.

#### Primary Operation Methods
- **Graphical User Interface (GUI)**: The OrcaLab client provides an intuitive GUI where operations are completed by clicking, dragging, and entering parameters.
- **Asset Library**: Subscribe to and use pre-built models and scenes from the online Asset Library.
- **AI Generation Tools**: Generate 3D assets via text or image descriptions — no code required.



#### Recommended Learning Path
1. **Installation & Environment Setup**: Configure the runtime environment following the installation guide.
2. **Basic Operation Guide**: Familiarize yourself with the various modules and basic operations of the client interface.
3. **Quick Start Examples**: Try running the simulation examples included with OrcaLab.
4. **Asset Library Usage**: Learn how to search, subscribe to, and use assets.

### 🟡 Users with Some Programming Experience

#### Applicable Scenarios
- **Custom Simulation Logic**: Write Python scripts to control robot behavior.
- **Data Processing**: Analyze and process data collected from simulations.
- **Algorithm Validation**: Integrate your own AI algorithms or control strategies for testing.
- **Extending Functionality**: Develop external programs that interact with OrcaLab.

#### Required Programming Skills
- **Python Basics**: Master Python syntax, data structures, and object-oriented programming.
- **Conda Environment Management**: Create, activate, and manage Python virtual environments.
- **OrcaLab API**: Understand the Python API interfaces provided by OrcaLab (via libraries such as `orca-gym`).
- **Git Basics**: Obtain and manage open-source example code (such as OrcaPlayground).


#### Recommended Learning Path
1. **Python Programming Introduction**: Learn core Python knowledge.
2. **Conda and Pip Usage**: Master Python package and environment management.
3. **Study Open-Source Examples**: Explore code in OrcaPlayground and OrcaManipulation to understand how to write simulation programs.
4. **Modify Configuration Files**: Learn how to configure `.orcalab/config.toml` and add custom simulation programs.
5. **Data Collection Scripts**: Try running and modifying VR teleoperation data collection scripts.

### 🔴 Professional Developer Users

#### Applicable Scenarios
- **Deep Customization**: Develop complex, high-performance simulation applications.
- **Algorithm R&D**: Deeply integrate cutting-edge AI algorithms with the simulation environment.
- **System Integration**: Integrate OrcaLab into larger R&D or production systems.
- **Optimization & Extension**: Perform advanced tuning of simulation performance and physics engines.

#### Required Programming Skills
- **Advanced Python**: Familiarity with asynchronous programming, multithreading/multiprocessing, and performance optimization.
- **Scientific Computing Libraries**: NumPy, SciPy, Pandas, etc.
- **AI/ML Frameworks**: PyTorch, TensorFlow, Stable-Baselines3, etc.
- **Data Structures & Algorithms**: Optimize simulation logic and data processing efficiency.
- **Unix/Linux Command Line**: Efficiently manage systems and development environments.

## 📚 Recommended Learning Resources

### OrcaLab Official Documentation
- **Installation Guide**: Understand environment setup and installation steps.
- **Basic Operation Guide**: Familiarize yourself with the GUI interface.
- **Quick Start Simulation Examples**: Learn how to run your first simulation.
- **Asset Library Basic Operation Guide**: Master asset usage.
- **VR Teleoperation & Data Collection Guide**: Understand the data collection workflow.

### Python Learning Resources
- **Python Official Tutorial**
- **Python courses on online platforms** such as Codecademy, Coursera, and Udemy
- **Introductory books** such as "Python Crash Course"

### Git Learning Resources
- **Git Official Documentation**
- **Pro Git** e-book

## Summary

OrcaLab aims to make robot simulation technology accessible to more people. If you simply want to explore, learn basic operations, or build simple scenes, **deep programming knowledge is not required**. However, if you wish to perform custom development, algorithm validation, data collection, or other advanced operations, then mastering a certain level of **Python programming skills will be essential**.

## Related Links
- [OrcaLab Product Introduction](orca-lab-introduction/orca-lab-product-introduction-v1.0.md)
- [OrcaLab Basic Operation Guide](user-guide/orca-lab-basic-operation-guide-v1.0.md)
- [OrcaLab Quick Start Simulation Example](environment-setup/orca-lab-quick-start-simulation-v1.0.md)