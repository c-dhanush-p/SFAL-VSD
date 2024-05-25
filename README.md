<details>
    <summary>Day 0: System Tools Setup</summary>
    <ul>
        <li>
            <details>
                <summary>Yosys</summary>
                <p>Instructions:</p>
                <pre>
$ git clone https://github.com/YosysHQ/yosys.git 
$ cd yosys 
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
  libreadline-dev gawk tcl-dev libffi-dev git \
  graphviz xdot pkg-config python3 libboost-system-dev \
  libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install

![image](https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5f86b5da-7d96-44d2-8a8b-4772489f4bdf)
              </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Iverilog</summary>
                <p>Instructions:</p>
                <pre>
$ sudo apt-get install iverilog

![image](https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3c51039d-231e-43d9-8c15-b641772ff0de)
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>GTKWave</summary>
                <p>Instructions:</p>
                <pre>
$ sudo apt update
$ sudo apt install gtkwave

![image](https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c76a1b61-9cc6-48c2-bf90-521534261f92)
![image](https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3e3fcef3-7bd7-4871-aa75-d91b80c57d2a)
                </pre>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 0-->
<details>
    <summary>Day 1: RTL Design & Synthesis </summary>
    <ul>
        <li>
            <details>
                <summary>Lab using Iverilog and GTKWave</summary>
                <p>Step 1</p>
                <pre>
Load mux & its testbench to Iverilog.
<img width="1232" alt="Screenshot 2024-05-20 at 5 53 58 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ac9691e6-37c5-48d3-9a7b-791e065305d7">
A file (a.out) is generated.
<img width="1227" alt="Screenshot 2024-05-20 at 6 18 58 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/73d08cae-2730-4b28-99ac-117dbe313407">
                </pre>
                <p>Step 2</p>
                <pre>
a.out file is executed.
<img width="829" alt="Screenshot 2024-05-20 at 6 22 51 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/e0072702-71b4-4639-a23b-c59752776674">
A .vcd file (tb_good_mux.vcd) that contains all the value changes is generated.
<img width="1235" alt="Screenshot 2024-05-20 at 6 23 53 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/384cf76c-b95c-498a-8af1-78402293b5ec">
                </pre>
                <p>Step 3</p>
                <pre>
Load the .vcd file into GTKWave generator.
<img width="989" alt="Screenshot 2024-05-20 at 6 26 13 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2325d877-1d28-44d5-8918-508ab3557fa1">
The mux's behavior is analyzed on GTKWave
<img width="1440" alt="Screenshot 2024-05-20 at 5 55 23 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/92fce9e8-1473-48f6-bd10-0170dfea0ee1">
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Lab using Yosys & Logic Synthesis</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Realising the Logic and Generating Library Specific Design</summary>
                            <p>Step 1</p>
                            <pre>
Invoke Yosys by using command yosys
<img width="728" alt="1" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/511f0f1e-7d42-4ec1-865c-30033eaf2657">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read the library using read_liberty
<img width="736" alt="2" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/d9ab968a-7a51-4967-8d24-bedaf91ec5d4">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Read the design using read_verilog
<img width="726" alt="3" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7f13526a-9685-47bc-8088-0a543e154715">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Define the module that needs to be synthesized
<img width="300" alt="synth" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/085dd68a-11ad-4eb3-be55-543975d6ea92">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Use command show to view the design
<img width="734" alt="4" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4a925efb-34f4-4c75-aa5c-a13701ef8128">
<img width="472" alt="5" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/208e05f3-a20c-497d-a82c-7d98a7853a79">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Generate the netlist using abc command
<img width="616" alt="Screenshot 2024-05-20 at 8 12 40 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5be7431c-7507-47d7-83b0-fc377bd715f6">
View the netlist info after execution
<img width="892" alt="6" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1667a8f5-6170-4ee1-9ead-59ad4b5fa0d8">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Use command show again to view the library specific design
<img width="1355" alt="Screenshot 2024-05-20 at 8 14 31 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/8de63bd3-2131-4e56-8463-90a5a96642d1">
View the design using library modules
<img width="608" alt="7" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5245e764-c2de-4830-a35d-daea38089c90">
                            </pre>          
                        </details>
                    </li>
                </ul>
                <ul>
                    <li>
                        <details>    
                            <summary>PART 2: Write the netlist & Modify to View Without Additional Attributes</summary>
                            <p>Step 1</p>
                            <pre>
Write the netlist using command 'write_netlist'
<img width="404" alt="Screenshot 2024-05-21 at 9 22 06 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2bb73b22-1488-4cf5-9a74-910712431df5">
                            </pre>
                            <p>Step 2</p>
                            <pre>
View the netlist using command '!gvim'
<img width="432" alt="Screenshot 2024-05-21 at 9 23 38 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/36b0d303-b002-41e3-9a27-adcd7684dcf0">
The Generated Netlist:
<img width="784" alt="Screenshot 2024-05-21 at 9 23 51 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/79d3bb51-99ee-4871-9e4e-b4376cc6935c">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Generate a netlist without attributes using -noattr
<img width="954" alt="Screenshot 2024-05-21 at 9 57 20 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/47c08fe2-b816-4d71-adff-8a305ba8f132">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Use '!gvim' again to view the modified netlist
<img width="432" alt="Screenshot 2024-05-21 at 9 23 38 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c9f300fb-99d2-4263-9d6d-6f30834072c3">
The Modified Netlist:
<img width="781" alt="Screenshot 2024-05-21 at 9 34 05 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ecc95ee1-9381-47fd-9b01-577e77fd55c0">
                            </pre>
                        </details>
                    </li>
                </ul>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 1-->
<details>
    <summary>Day 2: Timing Libs, Hierarchial vs Flat Synthesis & Efficient Flop Coding Styles and Optimization </summary>
    <ul>
        <li>
            <details>
                <summary>Introduction to Timing .libs</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Understanding the name of .libs</summary>
                            <p>Step 1</p>
                            <pre>
View the library using 'gvim'
<img width="1045" alt="Screenshot 2024-05-21 at 10 20 10 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9a511f07-2aca-4e40-a8b0-930dfad2a10a">
The Library:
<img width="547" alt="Screenshot 2024-05-21 at 10 22 13 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/70919fd1-9bb1-424e-bebb-090657349b39">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Reading the library name
<img width="370" alt="Screenshot 2024-05-21 at 10 35 22 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/e0e42b16-19ce-42d4-831c-d463776317ac">
From the name, 
'130' refers to the technology being '130nm',
'tt' refers to the library being a typical .lib,
'025C' refers to the temperature, &
'1v80' refers to the voltage.
These give us the operating conditions of the cells in the library
                            </pre>          
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: Understanding the cells in library</summary>
                            <p>Step 1</p>
                            <pre>
'cell' refers to the beggining of a new cell
Multiple cells in .lib:
<img width="592" alt="Screenshot 2024-05-21 at 10 39 03 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2d792ba9-5cc6-4bd7-8bab-3718225cf798">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Attributes inside cell
<img width="376" alt="Screenshot 2024-05-21 at 10 37 49 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ac3682e7-079c-4fbf-8480-1290f9794bb3">
Cell includes information about a cell's:
- Leakage Power of different input combinations
<img width="253" alt="Screenshot 2024-05-21 at 10 45 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/fefb7cbf-707f-427c-971a-78b12c5b14b1">
- Area
<img width="184" alt="Screenshot 2024-05-21 at 10 50 09 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7aa8360b-55b8-4dda-b703-a03d18bc4b31">
- Power ports
<img width="380" alt="Screenshot 2024-05-21 at 10 52 28 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7cb149fb-8353-46a3-a04b-7062ff3c1769">
-Input Pins (input capacitance, internal power, transition & delay)
<img width="1091" alt="Screenshot 2024-05-21 at 10 54 24 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/70c1b5ef-6baa-4765-b465-3da0998f3f7c">
                            </pre>
                        </details>
                    </li>
                </ul>
            </details>
        </li>
        <li>
            <details>
                <summary>Hierarchial vs Flat Synthesis</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Hierarchial Synthesiss</summary>
                            <p>Step 1</p>
                            <pre>
Read the library
<img width="736" alt="Screenshot 2024-05-22 at 12 00 54 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f9547e34-b5cd-4c7b-af72-d67552ba0c8a">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read the verilog file
<img width="738" alt="Screenshot 2024-05-22 at 12 08 15 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/82af6189-157e-4029-8ad7-a8936a0a27f6">
                            </pre>          
                            <p>Step 3</p>
                            <pre>
Define the module to be synthesized 
<img width="347" alt="Screenshot 2024-05-22 at 12 11 25 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ac72627f-c6b4-4876-8b41-14d83e0ef96c">
View the design hierarchy:
<img width="407" alt="Screenshot 2024-05-22 at 12 12 18 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ec43f8fe-fab0-4f5b-b451-101013b8d780">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Generate the netlist
<img width="614" alt="Screenshot 2024-05-22 at 12 13 21 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/16402311-0504-42a8-b0e7-7342a86a26dc">
                            </pre>
                            <p>Step 5</p>
                            <pre>
run command 'show' to view the design
<img width="1362" alt="Screenshot 2024-05-22 at 12 15 46 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/415a1018-68d4-4281-8e86-bbbdeacfbab2">
<img width="609" alt="Screenshot 2024-05-22 at 12 15 24 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f6ae7601-49e0-4c1a-b32e-25bd1e5bc372">
As both submodule 1 and submodule 2 are instantiated seperately, hierachy is maintained and such design is a Hierarchial Design.
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: Flat Synthesis</summary>
                            <p>Step 1</p>
                            <pre>
run command 'flatten' to write a flat netlist
<img width="439" alt="Screenshot 2024-05-22 at 12 21 24 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/bfa29843-5c21-4dbe-8847-890bf82d5e58">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Write the netlist to a .v file
<img width="532" alt="Screenshot 2024-05-22 at 12 26 25 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3fad90f2-389a-46ef-8a93-f03243f87190">
                            </pre>
                            <p>Step 3</p>
                            <pre>
View the netlist
<img width="482" alt="Screenshot 2024-05-22 at 12 27 00 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/cf1e6b0f-2548-468c-9ed0-63bd2c3b8334">
<img width="796" alt="Screenshot 2024-05-22 at 12 27 38 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/b838955e-d680-432f-8f6e-0e027a31ebbc">
As we can see the sub-modules don't appear in the netlist indicating that the design has been flattened out
                            </pre>
                            <p>Step 4</p>
                            <pre>
Run command 'show' to view the flattened module
<img width="1369" alt="Screenshot 2024-05-22 at 12 32 01 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/35553002-d975-4e24-9de8-1f0d4066c653">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 3: Sub-Module Level Synthesis</summary>
                            <p>Step 1</p>
                            <pre>
Read library
<img width="755" alt="Screenshot 2024-05-22 at 7 26 39 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f521083f-1d23-4e6a-87ef-45a96b043e23">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read Verilog
<img width="713" alt="Screenshot 2024-05-22 at 7 28 58 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f3bddcb1-5888-4288-9b9a-119535f53cbd">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Synthesize at sub module level using 'synth -top'
<img width="310" alt="Screenshot 2024-05-22 at 7 31 10 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/232776a6-02a3-4097-9cd9-ec88e525d29f">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Generate the netlist
<img width="615" alt="Screenshot 2024-05-22 at 7 32 50 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/e54d33a7-9d88-4df7-a6f0-2d6f8e2a5a9f">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Run show command
<img width="1362" alt="Screenshot 2024-05-22 at 7 33 46 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f04ad95e-7c92-4b21-8f02-a4e3a7b2151d">
<img width="1360" alt="Screenshot 2024-05-22 at 7 34 39 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7f953408-0771-48c1-b307-33c96a04fed1">
Multiple Instances: Such module level synthesis is done when multiple instances of the same module are 
used in the top level design.
Divide & Conquer: If you have a massive design, this type of synthesis can be done to generate 
multiple understandable netlists that can be stitched together.
                            </pre>
                        </details>
                    </li>
                </ul>
            </details>
        </li>
        <li>
            <details>
                <summary>Flop Coding Styles</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Different Flip Flops</summary>
                            <p>Step 1</p>
                            <pre>
Run iverilog for an Asynchronous Reset D-Flip Flop using its testbench
![Screenshot 2024-05-25 at 5 40 49 PM](https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/82b144e5-745a-49d8-9746-bd27aca1c82b)
                            </pre>
                            <p>Step 2</p>
                            <pre>
Execute the output file (a.out)
<img width="827" alt="Screenshot 2024-05-25 at 5 40 57 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3065ff21-438d-44d6-9faa-05e510d9ec13">
                            </pre>          
                            <p>Step 3</p>
                            <pre>
Run GTKWave to view the behaviour of the Asynchronous Reset D-Flip Flop
<img width="1020" alt="Screenshot 2024-05-25 at 5 42 49 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ffed249b-5274-463e-8c0e-5ffcc76b8833">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Observe the behaviour of the Asynchronous Reset D-Flip Flop
<img width="1370" alt="Screenshot 2024-05-25 at 5 43 08 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f59e27b2-fbc6-4265-a9eb-030e3b6e8f22">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Repeat Steps 1-3 using the Asynchronous Set D-Flip Flop
<img width="1198" alt="Screenshot 2024-05-25 at 5 50 56 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/e5b3c737-6a0c-41b9-9943-551f4a65df7a">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Observe the behaviour of the Asynchronous Set D-Flip Flop
<img width="1376" alt="Screenshot 2024-05-25 at 5 50 28 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/cd91a7e2-1462-4417-becc-41a1ba3804ef">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Repeat Steps 1-3 using the Synchronous Reset D-Flip Flop
<img width="1160" alt="Screenshot 2024-05-25 at 5 52 33 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/e0176eba-30d7-4ec2-a455-f65c29ff1bf4">
                            </pre>
                            <p>Step 8</p>
                            <pre>
Observe the behaviour of the Synchronous Reset D-Flip Flop
<img width="1374" alt="Screenshot 2024-05-25 at 5 53 54 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6d135130-4828-4ee0-b37a-f34cc56c8ce9">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: Flop Synthesis</summary>
                            <p>Step 1</p>
                            <pre>
In Yosys, read the library
<img width="742" alt="Screenshot 2024-05-25 at 6 07 46 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f7d5a769-be16-4bb1-8b92-bfa3ac26ade0">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read the verilog file for Asynchronous Reset for D-Flip Flop
<img width="676" alt="Screenshot 2024-05-25 at 6 08 24 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/d98c8b23-14d0-447c-8673-b8a8289fbfd1">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Define the module to be sunthesized
<img width="328" alt="Screenshot 2024-05-25 at 6 09 26 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/28083be8-f27b-4be0-91c5-546b5e58155b">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Map  the flip flops in the library for synthesis
<img width="887" alt="Screenshot 2024-05-25 at 6 10 25 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/137cc8c9-0908-4e76-af12-94c682009a93">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Generate the netlist
<img width="898" alt="Screenshot 2024-05-25 at 6 11 43 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1b986c23-31dd-4d6d-aa74-4df281b2009c">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Execute show to view the netlist for the Asynchronous Reset D-Flip Flop
<img width="1373" alt="Screenshot 2024-05-25 at 6 12 04 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f2ed91e7-5a74-4bc1-9345-20266e043938">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Repeat Steps 2-5 using for the Asynchronous Set D-Flip Flop
                            </pre>
                            <p>Step 8</p>
                            <pre>
Execute show to view the netlist design for the Ashynchronous Set D-Flip Flop
<img width="1369" alt="Screenshot 2024-05-25 at 6 31 28 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/12fa0bd2-5b1d-4407-a983-2dc652d11c8a">
                            </pre>
                            <p>Step 9</p>
                            <pre>
Repeat Steps 2-5 using for the Synchronous Reset D-Flip Flop
                            </pre>
                            <p>Step 9</p>
                            <pre>
Execute show to view the netlist design for the Synchronous Reset D-Flip Flop
<img width="1371" alt="Screenshot 2024-05-25 at 6 36 55 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/8177cd93-1abe-4674-a81f-ceb7b86dc48e">
                            </pre>
                        </details>
                    </li>    
                </ul>
            </details>
        </li>
        <li>
            <details>
                <summary>Special Case Optimizations</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: mul2 Synthesis</summary>
                            <p>Step 1</p>
                            <pre>
In Yosys, read the library
<img width="725" alt="Screenshot 2024-05-25 at 7 01 08 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/a32d5539-b2a4-40bb-95c1-bac1b3332cd0">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read the verilog file for mult_2
<img width="625" alt="Screenshot 2024-05-25 at 7 01 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/be30de05-0579-4545-991e-e52d33d88751">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Define the module to be synthesized
<img width="262" alt="Screenshot 2024-05-25 at 7 02 00 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/727bbedd-fe7d-4532-9a3c-2985192970b4">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Generate the netlist and notice the prompt to not call for abc as there are no cells to be synthesized
<img width="814" alt="Screenshot 2024-05-25 at 7 02 23 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/a2ea3b99-0d86-4c5a-a151-2be5bdeed93b">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Execute show to view the netlist design
<img width="1374" alt="Screenshot 2024-05-25 at 7 02 33 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/73b2dfce-944f-4809-bd10-e6f467c07f71">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Write the netlist
<img width="416" alt="Screenshot 2024-05-25 at 7 20 51 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/76314161-76ae-4b65-9744-bc8a89549651">
                            </pre>
                            <p>Step 7</p>
                            <pre>
View the netlist
<img width="370" alt="Screenshot 2024-05-25 at 7 30 02 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/bdb9adae-f924-4403-8aba-9d7580f264f9">
<img width="794" alt="Screenshot 2024-05-25 at 7 30 17 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ac88fca2-8995-46a5-8360-81df681e06c5">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: mult8 Synthesis</summary>
                            <p>Step 1</p>
                            <pre>
Read the verilog file for mult_8
<img width="626" alt="Screenshot 2024-05-25 at 7 32 14 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5847d9a9-9f18-45cc-8571-b7bb62e9f544">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Define the module to be sunthesized
<img width="293" alt="Screenshot 2024-05-25 at 7 33 20 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c7ba86b6-f541-44e2-91ca-05cde1f011bf">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Generate the netlist and notice the prompt to not call for abc as there are no cells to be synthesized
<img width="860" alt="Screenshot 2024-05-25 at 7 35 13 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2a4de562-57cf-4c46-820f-0babb6797425">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Execute show to view the netlist design
<img width="608" alt="Screenshot 2024-05-25 at 7 35 49 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5f8764bf-8775-4d9a-a504-bb47971b04fa">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Write the netlist
<img width="431" alt="Screenshot 2024-05-25 at 7 38 22 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/24820a31-19eb-497e-bcc2-c11ec0fb3c4c">
                            </pre>
                            <p>Step 7</p>
                            <pre>
View the netlist
<img width="774" alt="Screenshot 2024-05-25 at 7 39 06 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9b5427d8-49c0-4b9c-ad29-3a17fc0baa41">
<img width="779" alt="Screenshot 2024-05-25 at 7 39 21 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/8c4e7a38-c5aa-4774-81b6-e4a9ea022214">
                            </pre>
                        </details>
                    </li>    
                </ul>
            </details>
        </li>
    </ul>
</details>
