# project Module LoRaWAN

This project is an ns-3 module that can be used to perform simulations of a LoRaWAN network, and it is based in the initial version of this code was developed as part of a master's thesis at the University of Padova (https://github.com/signetlabdei/lorawan), under the supervision of Prof. Lorenzo Vangelista, Prof. Michele Zorzi and with the help of Marco Centenaro.

## Getting Started ##

This section is aimed at getting a user to a working state starting with a machine that may never have had LoRaWAN-NS3 installed. It covers prerequisites, ways to obtain LoRaWAN-NS3, ways to build LoRaWAN-NS3, and ways to verify your build and run LoRaWAN program.

### Prerequisites ###

To run simulations using this module, you will need to install ns-3, and clone this repository inside the src directory:
```

git clone https://github.com/nsnam/ns-3-dev-git ns-3
git clone https://github.com/heldercs/loraModule.git ns-3/src/lorawan

```
If you are interested in having the latest features (and more bug-prone code), you can check out the develop branch:
```

cd ns-3/src/lorawan
git checkout develop
```


### Building ###

To configure the NS-3 you will need to execute the following commands:
```
$ ./ns3 configure --build-profile=debug --enable-examples --enable-tests
```
The build system is now configured and you can build the debug versions of the LoRaWAN-NS3 programs by simply typing
```
$ ./ns3 build
```

### Testing the LoRaWAN Module ###

You can run the unit tests of the ns-3 distribution by running the ./test.py script:
```
$ ./test.py --no-build
```
These tests are run in parallel by ns3. You should eventually see a report saying that
```
92 of 92 tests passed (92 passed, 0 failed, 0 crashed, 0 valgrind errors)
```
### Running the Script ###

We typically run scripts under the control of Waf. This script allows the build system to ensure that the shared library paths are set correctly and that the libraries are available at run time. To run the applications LoRa program, to run the runSimulator shell script by typing the following:
```
$ ./runSimulator.sh gwRing App gwRad rad simTime interval pEDs trial
```
in which the above parameters are defined as:
```
* App      - Applications options 
* gwRing   - Number of gateway rings to include;
* rad      - The radius of the area to simulate;
* gwRad    - The distance between two gateways;
* simTime  - The time for which to simulate;
* interval - The period in seconds to be used by periodically transmitting applications;
* pED      - Whether or not to print a file containing the ED's positions;
* trial    - The results directory.
```
Applications Options (App):
```
* 0      - lorawan Application base 
* 1      - lorawan Application multiClass
* 2      - lorawan Application Regular and Alarm 
* 3      - lorawan Application dualClass

```
The results will be placed in TestReult:
```
$ ls TestResult/
$ test0 test1 test2 testX
```
where X is trial's options
