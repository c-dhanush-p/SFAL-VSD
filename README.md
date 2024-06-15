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
Multiple Instances: Such module level synthesis is done when multiple instances of the 
same module are used in the top level design.
Divide & Conquer: If you have a massive design, this type of synthesis can be done to 
generate multiple understandable netlists that can be stitched together.
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
<!--End of Day 2-->
<details>
    <summary>Day 3: Combinational and Sequential Optimization </summary>
    <ul>
        <li>
            <details>
                <summary>Combinational Logic Optimization</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: For opt_check Modules</summary>
                            <p>Step 1</p>
                            <pre>
In Yosys, read the library
<img width="728" alt="Screenshot 2024-05-25 at 10 52 57 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/bf2a8b14-da19-41ff-96ac-ee1fc0572722">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read the verilog file for opt_check
<img width="652" alt="Screenshot 2024-05-25 at 10 55 56 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1c68e3e0-f349-4a91-9aa0-df769f531e71">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Define the module to be synthesized
<img width="286" alt="Screenshot 2024-05-25 at 11 23 08 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7e9cb74a-e0d5-4779-b786-eb7d62618c60">
View the number of cells in module
<img width="420" alt="Screenshot 2024-05-25 at 10 57 03 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ea4b5d4a-122a-4881-903f-66d5a37996c0">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Execute opt_clean to remove unused cells and wires                                
<img width="623" alt="Screenshot 2024-05-25 at 10 57 18 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/b9d682ef-5229-4092-9dff-ac44c408aff0">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Generate the netlist
<img width="611" alt="Screenshot 2024-05-25 at 10 57 38 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4d887668-b080-4942-a05d-5350f1ac6e51">
Notice the number of cells reduce
<img width="598" alt="Screenshot 2024-05-25 at 10 57 51 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/78dbf1ca-d2c6-458c-9b3e-8ef595bd0c82">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Execute show to view the netlist design
<img width="611" alt="Screenshot 2024-05-25 at 10 58 00 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/0992c28f-063b-4a43-90b0-b2abdfad762b">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Repeat Steps 2-5 for opt_check2
Notice the number of cells reduce from before opt_clean to after
After synth command,
<img width="418" alt="Screenshot 2024-05-25 at 10 59 48 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/16b97a65-65b6-4b51-ac38-3218c9d2865d">
After abc command,
<img width="556" alt="Screenshot 2024-05-25 at 11 00 18 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/17c9dd9f-fd22-4312-bb51-0be49eadb040">
                            </pre>
                            <p>Step 8</p>
                            <pre>
Execute show to view the netlist design
<img width="602" alt="Screenshot 2024-05-25 at 11 00 27 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/576287f0-b732-4a4f-a572-0c0fb3d21e93">
                            </pre>
                            <p>Step 9</p>
                            <pre>
Repeat Steps 2-5 for opt_check3
Notice the number of cells reduce from before opt_clean to after
After abc command,
<img width="497" alt="Screenshot 2024-05-25 at 11 04 17 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3607a834-f446-462b-ab11-25856870721a">
                            </pre>
                            <p>Step 10</p>
                            <pre>
Execute show to view the netlist design
<img width="607" alt="Screenshot 2024-05-25 at 11 04 32 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/21cde162-5510-4588-8bc4-7eeea1b899b2">
                            </pre>
                            <p>Step 11</p>
                            <pre>
Repeat Steps 2-5 for opt_check4
Notice the number of cells reduce from before opt_clean to after
After abc command,
<img width="577" alt="Screenshot 2024-05-25 at 11 06 52 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/8196fbe3-8fea-47d0-99e3-ab764930e3e5">
                            </pre>
                            <p>Step 12</p>
                            <pre>
Execute show to view the netlist design
<img width="599" alt="Screenshot 2024-05-25 at 11 06 59 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/b3d8a2af-1625-43ed-b4dd-4c39cc89c4e1">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: multiple_modules Optimization</summary>
                            <p>Step 1</p>
                            <pre>
Read the verilog file for multiple_modules_opt.v
<img width="744" alt="Screenshot 2024-05-25 at 11 12 50 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4ef7a599-3701-4953-8c1a-450a923a9876">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Define the module to be synthesized
<img width="398" alt="Screenshot 2024-05-25 at 11 12 57 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/73c1c313-ae77-45ad-9814-436b4d1cdebf">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Flatten the design
<img width="475" alt="Screenshot 2024-05-25 at 11 13 15 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7dd4686a-7897-4ba8-8a65-52111a04903d">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Execute opt_clean to remove unused cells and wires                                
<img width="635" alt="Screenshot 2024-05-25 at 11 13 21 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4bfecaba-c49b-4ca9-958e-f1e7486aaa62">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Generate the netlist 
<img width="617" alt="Screenshot 2024-05-25 at 11 13 54 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c7b85d9d-f18d-4992-bf0b-151f22301e3d">
Notice the number of cells reduce
<img width="571" alt="Screenshot 2024-05-25 at 11 14 04 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/cf863f0b-27aa-4781-8b36-0e6bd0f6275a">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Execute show to view the netlist design
<img width="595" alt="Screenshot 2024-05-25 at 11 14 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/83c65d81-da59-49a9-8735-3938a35d7c18">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Repeat Steps 1-5 for multiple_modules_opt2.v
Notice the number of cells reduce from before opt_clean to after
                            </pre>
                            <p>Step 8</p>
                            <pre>
Execute show to view the netlist design
<img width="353" alt="Screenshot 2024-05-25 at 11 15 33 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/18374a6c-27ec-4bb3-9094-b057cbc6a9e2">
                            </pre>          
                        </details>
                    </li>
                </ul>
            </details>
        </li>
        <li>
            <details>
                <summary>Sequential Logic Optimization</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Dff_const Synthesis</summary>
                            <p>Step 1</p>
                            <pre>
Read the library
<img width="735" alt="Screenshot 2024-05-25 at 11 54 14 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c4b43fb9-4a90-4695-842f-d68680ce4f0b">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read the verilog file dff_const1.v
<img width="669" alt="Screenshot 2024-05-25 at 11 54 27 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/e85367f2-5aa3-4692-9684-a5726016a08e">
                            </pre>          
                            <p>Step 3</p>
                            <pre>
Define the module to be synthesized 
<img width="306" alt="Screenshot 2024-05-25 at 11 54 52 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c5e25901-ce0f-4520-9e21-ac1d5bc2666c">
View the design hierarchy:
<img width="422" alt="Screenshot 2024-05-25 at 11 55 02 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/80bc0503-0ade-47e4-bb10-a6773c53051f">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Run dfflibmap to map dff cells to sequential cells
<img width="870" alt="Screenshot 2024-05-25 at 11 56 14 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/76ce4935-130d-4692-a5b3-211c7211afdc">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Generate the netlist
<img width="611" alt="Screenshot 2024-05-25 at 11 57 03 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4802d8a6-2763-4975-be62-805a4473ac2a">
                            </pre>
                            <p>Step 6</p>
                            <pre>
run command 'show' to view the design
<img width="594" alt="Screenshot 2024-05-25 at 11 57 27 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/8dcc75b9-0bc2-43a3-89ae-9b0a1a8b6122">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Repeat Steps 2-5 for dff_const2.v
                            </pre>
                            <p>Step 8</p>
                            <pre>
run command 'show' to view the design
<img width="609" alt="Screenshot 2024-05-26 at 12 02 02 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/481c7486-83c1-4fe3-8301-ba1f930bc791">
                            </pre>
                            <p>Step 9</p>
                            <pre>
Repeat Steps 2-5 for dff_const3.v
                            </pre>
                            <p>Step 10</p>
                            <pre>
run command 'show' to view the design
<img width="1359" alt="Screenshot 2024-05-26 at 12 37 59 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5f8109ea-1f69-4d4f-bdb5-fb59e37cc882">
                            </pre>
                            <p>Step 11</p>
                            <pre>
Repeat Steps 2-5 for dff_const4.v
                            </pre>
                            <p>Step 12</p>
                            <pre>
run command 'show' to view the design
<img width="616" alt="Screenshot 2024-05-26 at 12 39 53 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/69a155b4-d899-4597-9631-59e497c7edb5">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: Sequential optimzations for unused outputs</summary>
                            <p>Step 1</p>
                            <pre>
Read the library
<img width="744" alt="Screenshot 2024-05-26 at 1 13 14 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f2b3de6b-a2c1-498b-b957-aec0487c08be">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Read the verilog file counter_opt.v
<img width="663" alt="Screenshot 2024-05-26 at 1 13 34 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c603c612-d903-4e05-ab1d-bde84a52fd3c">
                            </pre>          
                            <p>Step 3</p>
                            <pre>
Define the module to be synthesized 
<img width="324" alt="Screenshot 2024-05-26 at 1 13 55 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1a4979c3-0da7-4cf9-9bb2-a698f2b4c51d">
View the design hierarchy:
<img width="407" alt="Screenshot 2024-05-26 at 1 14 07 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ecd2ad69-1e69-44cf-8403-d8670bf7028e">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Run dfflibmap to map dff cells to sequential cells
<img width="873" alt="Screenshot 2024-05-26 at 1 14 39 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/65e34b53-4b7a-4d55-a43f-0cf59489a386">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Generate the netlist
<img width="621" alt="Screenshot 2024-05-26 at 1 15 10 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/d4b49572-0224-4ca6-978d-71ace7464ce3">
                            </pre>
                            <p>Step 6</p>
                            <pre>
run command 'show' to view the design
<img width="1361" alt="Screenshot 2024-05-26 at 1 15 31 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/26807584-5733-4728-bc9f-de30d5d18d4d">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Repeat Steps 2-6 for counter_opt2.v
<img width="425" alt="Screenshot 2024-05-26 at 1 21 36 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2fdaa020-ca5a-4bf7-9ca2-b4087914ac52">
                            </pre>
                            <p>Step 8</p>
                            <pre>
run command 'show' to view the design
<img width="1370" alt="Screenshot 2024-05-26 at 1 22 42 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/848db3bb-35bd-4fd2-8e92-122e76d86f70">
                            </pre>
                        </details>
                    </li>
                </ul>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 3-->
<details>
    <summary>Day 4: Gate Level Simulation, Synthesis Simulation Mismatch, and Blocking & Non-Blocking Statements </summary>
    <ul>
        <li>
            <details>
                <summary>Lab on GLS and Synth Simulation Mismatch</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: For ternary_operator_mux</summary>
                            <p>Step 1</p>
                            <pre>
Load ternary_operator_mux.v & its testbench to Iverilog.
<img width="1333" alt="Screenshot 2024-05-26 at 2 25 18 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5fb664a3-428b-40b5-95c3-6e5e76385d2e">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Execute a.out file.
<img width="831" alt="Screenshot 2024-05-26 at 2 25 28 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/0845279c-0fdb-458a-b911-593f7f138990">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Load the .vcd file genrated into GTKWave.
<img width="895" alt="Screenshot 2024-05-26 at 2 25 46 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/a17efccf-4528-4b08-856c-e3366dea9441">
The ternary_operator_mux's behavior is analyzed on GTKWave                            
<img width="1374" alt="Screenshot 2024-05-26 at 2 26 56 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/b2f81f99-be77-4d8f-8c5f-c76efa0db555">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Invoke Yosys by using command yosys
<img width="817" alt="Screenshot 2024-05-26 at 2 27 23 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5aeace9b-91d1-43df-b7a7-95a22d2f7dca">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Read the library using read_liberty
<img width="733" alt="Screenshot 2024-05-26 at 2 27 36 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c7df753c-4859-4517-b10b-844be452fbc0">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Read the ternary_operator_mux.v using read_verilog
<img width="754" alt="Screenshot 2024-05-26 at 2 27 54 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9bd5d509-2035-4be9-b17f-084f80f58835">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Define the module that needs to be synthesized
<img width="397" alt="Screenshot 2024-05-26 at 2 28 29 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6b23f59f-4e02-43ec-932b-750d183b30f0">
                            </pre>
                            <p>Step 8</p>
                            <pre>
Generate the netlist using abc command
<img width="622" alt="Screenshot 2024-05-26 at 2 28 54 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9565e3d5-66ba-45ef-8464-7cec13c5cdd4">
                            </pre>
                            <p>Step 9</p>
                            <pre>
Write the netlist to ternary_operator_mux_net.v
<img width="490" alt="Screenshot 2024-05-26 at 2 29 20 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/61065d52-6532-4a74-b8ae-34b8734fbce6">
                            </pre>
                            <p>Step 10</p>
                            <pre>
Execute show to view the design
<img width="609" alt="Screenshot 2024-05-26 at 2 29 30 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/76ee78c8-95fe-47e6-a9aa-ec2b6fa1e9c1">
                            </pre>
                            <p>Step 11</p>
                            <pre>
Exit yosys and load the ternary_operator_mux_net.v to iverilog.
<img width="1372" alt="Screenshot 2024-05-26 at 2 32 32 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/30cf677a-e529-4f09-a0e2-7d77f5ab48e5">
                            </pre>
                            <p>Step 12</p>
                            <pre>
Execute a.out file.
<img width="829" alt="Screenshot 2024-05-26 at 2 32 47 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9194b986-d637-4919-9a9a-a66ef5fd8150">
                            </pre>
                            <p>Step 13</p>
                            <pre>
Load the generated .vcd file into GTKWave
<img width="1107" alt="Screenshot 2024-05-26 at 2 33 19 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4b04c1e3-5aff-4937-9670-706364e92fa3">
                            </pre>
                            <p>Step 14</p>
                            <pre>
Observe the GLS of ternary_operator_mux
<img width="1357" alt="Screenshot 2024-05-26 at 2 33 52 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/746f372e-4dd9-4da4-a4ff-57836f00945e">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: For bad_mux</summary>
                            <p>Step 1</p>
                            <pre>
Load bad_mux.v & its testbench to Iverilog.
<img width="1072" alt="Screenshot 2024-05-26 at 2 47 47 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3886f80b-b39e-4f91-9cfb-d7fd26f87a2b">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Execute a.out file.
<img width="836" alt="Screenshot 2024-05-26 at 2 47 59 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/80bff7b8-6f38-42e9-b7ee-b527d9e06de7">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Load the .vcd file genrated into GTKWave.
<img width="980" alt="Screenshot 2024-05-26 at 2 48 17 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/94c68039-9cd8-435f-b02d-914619642094">
The bad_mux's behavior is analyzed on GTKWave                            
<img width="1362" alt="Screenshot 2024-05-26 at 2 49 01 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/cb432d9f-023b-4b28-ac59-c25e9abff098">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Invoke Yosys by using command yosys
<img width="815" alt="Screenshot 2024-05-26 at 2 49 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3a80b296-11d9-4150-ae87-17d6d2c971d1">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Read the library using read_liberty
<img width="731" alt="Screenshot 2024-05-26 at 2 49 25 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4e9fade6-5f81-41ac-a5d1-f3dbf9c35e98">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Read the bad_mux.v using read_verilog
<img width="756" alt="Screenshot 2024-05-26 at 2 49 40 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3d74ecc6-a028-4c2f-bf0b-9567d5270b26">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Define the module that needs to be synthesized
<img width="268" alt="Screenshot 2024-05-26 at 2 50 33 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ac8165b4-4a23-46ad-8196-242af9a8a9a8">
                            </pre>
                            <p>Step 8</p>
                            <pre>
Generate the netlist using abc command
<img width="612" alt="Screenshot 2024-05-26 at 2 50 51 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ca4dc976-5645-4c1f-878c-650c93136276">
                            </pre>
                            <p>Step 9</p>
                            <pre>
Write the netlist to bad_mux_net.v
<img width="364" alt="Screenshot 2024-05-26 at 2 51 09 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/87c4ebdf-95ff-4a34-847e-d49d5fe62e2a">
                            </pre>
                            <p>Step 10</p>
                            <pre>
Execute show to view the design
<img width="603" alt="Screenshot 2024-05-26 at 2 51 21 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/287737a1-3d21-4fde-8578-7a65d568b560">
                            </pre>
                            <p>Step 11</p>
                            <pre>
Exit yosys and load the bad_mux_net.v to iverilog.
<img width="1368" alt="Screenshot 2024-05-26 at 2 52 52 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f4bc8f2c-e08a-4675-be9a-e905b879c28a">
                            </pre>
                            <p>Step 12</p>
                            <pre>
Execute a.out file.
<img width="835" alt="Screenshot 2024-05-26 at 2 53 02 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7813fe2a-bb20-43de-9cf7-ec53c1459f51">
                            </pre>
                            <p>Step 13</p>
                            <pre>
Load the generated .vcd file into GTKWave
<img width="979" alt="Screenshot 2024-05-26 at 2 53 25 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/87f26967-6d37-45e9-963e-15d4107e767f">
                            </pre>
                            <p>Step 14</p>
                            <pre>
Observe the behavior of GLS of ternary_operator_mux due to Simulation Mismatch
<img width="1365" alt="Screenshot 2024-05-26 at 2 53 59 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/16ececd7-a724-43be-91a3-b394763a3678">
                            </pre>          
                        </details>
                    </li>
                </ul>
            </details>
        </li>
        <li>
            <details>
                <summary>Synthesis Simulation Mismatch</summary>
                <p>Step 1</p>
                <pre>
Load blocking_caveat.v & its testbench to Iverilog.
<img width="1232" alt="Screenshot 2024-05-26 at 3 20 01 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/98e89aec-e1e0-4371-9865-7f4d46970466">
                </pre>
                <p>Step 2</p>
                <pre>
Execute a.out file.
<img width="831" alt="Screenshot 2024-05-26 at 3 20 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/cabfbd67-5caf-467e-a4fe-36b9dd3613ae">
                </pre>
                <p>Step 3</p>
                <pre>
Load the .vcd file genrated into GTKWave.
<img width="1056" alt="Screenshot 2024-05-26 at 3 20 37 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/cd3b4d01-c92d-40e8-842f-e41fcb512967">
The blocking_caveat's behavior is analyzed on GTKWave                            
<img width="1362" alt="Screenshot 2024-05-26 at 3 21 17 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/0313fa9c-df40-46d2-9e31-0e18b9eb5b84">
                </pre>
                <p>Step 4</p>
                <pre>
Invoke Yosys by using command yosys
<img width="809" alt="Screenshot 2024-05-26 at 3 21 29 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/45aa14d6-5cc0-4a4d-b629-74bc87fda4fa">
                </pre>
                <p>Step 5</p>
                <pre>
Read the library using read_liberty
<img width="727" alt="Screenshot 2024-05-26 at 3 21 43 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/e4aa45a5-c575-4ecc-9fe6-e10553ba31da">
                </pre>
                <p>Step 6</p>
                <pre>
Read the blocking_caveat.v using read_verilog
<img width="709" alt="Screenshot 2024-05-26 at 3 21 55 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2c84de8b-63bc-4394-b833-79569ab86d0c">
                </pre>
                <p>Step 7</p>
                <pre>
Define the module that needs to be synthesized
<img width="596" alt="Screenshot 2024-05-26 at 3 23 34 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/886c9129-5cf7-4622-8857-326ffef0597f">
                </pre>
                <p>Step 8</p>
                <pre>
Generate the netlist using abc command
<img width="615" alt="Screenshot 2024-05-26 at 3 24 14 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3035c361-2a06-41ca-8363-5a40d4827d87">
                </pre>
                <p>Step 9</p>
                <pre>
Write the netlist to blocking_caveat_net.v
<img width="523" alt="Screenshot 2024-05-26 at 3 25 02 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/cef23d28-8d32-4c0c-941f-a0420db792d6">
                </pre>
                <p>Step 10</p>
                <pre>
Execute show to view the design
<img width="603" alt="Screenshot 2024-05-26 at 3 25 14 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f05de1e7-98ce-4ac3-bbaa-fbf14a31336c">
                </pre>
                <p>Step 11</p>
                <pre>
Exit yosys and load the blocking_caveat_net.v to iverilog.
<img width="1370" alt="Screenshot 2024-05-26 at 3 27 05 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/db39196e-3fba-424f-95ad-6b2f2e069d03">
                </pre>
                <p>Step 12</p>
                <pre>
Execute a.out file.
<img width="832" alt="Screenshot 2024-05-26 at 3 27 14 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/897f10b8-5491-46d7-a7ff-ca0eac28123a">
                </pre>
                <p>Step 13</p>
                <pre>
Load the generated .vcd file into GTKWave
<img width="1059" alt="Screenshot 2024-05-26 at 3 27 38 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2f6188c0-d262-48f1-a756-24f1c709de6f">
                </pre>
                <p>Step 14</p>
                <pre>
Observe the behavior of GLS of blocking_caveat due to Simulation Mismatch
<img width="1357" alt="Screenshot 2024-05-26 at 3 28 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4f2dcd1c-5d73-474e-bf68-12c82ff30205">
                </pre>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 4-->
<details>
    <summary>Day 5: DFT</summary>
    <ul>
            <summary>_What is DFT?_</summary>
            <p>
Design for Testability (DFT) is the methodology in VLSI that makes manufactured designs easier to test.
            </p>
            <summary>_Why do we do DFT?_</summary>
            <p>
Simply put, DFT helps to improve the testability of a complex chip. With chips becoming more complex with day and age, it becomes more essential to have effecient DFT that can test all the components because "whatever can go wrong, will go wrong." (Murphy's Law)
            </p>
            <summary>_DFT for economic and market needs_</summary>
            <p>
-> DFT for Economic Needs:
.            
                As mentioned before, with chips becoming more complex day by day, testing them might becoming eeconomically challenging. Having an effecient DFT methodology can decrease these costs. Also, DFT helps in finding defects or faults early in the process of designing which helps in short time for getting the design to the market which is profittable for a company.

-> DFT for Market Needs:
.            
            Having a faster time to market also helps in quick turnaround time which can satisfy the customer's needs while also ensuring defect-free and completely tested products. 
            </p>
            <summary>_When and where is DFT conducted?_</summary>
            <p>
DFT is conducted during the early stages of DFT.
It is usually conducted before the synthesis stage as well as before the final netlist generation.
            </p>
            <summary>_Pro's and Con's of DFT_</summary>
            <p>
Pro's:

-> Reduces Test Time

-> Reduces Costs

-> Early Fault Detection

-> Improves Design Reliability

Con's:

-> Increases Area of Design

-> Increases Power Consumption

-> Might Reduce Performance

-> Increased Design Time
            </p>
            <summary>_Basic Terminologies in DFT_</summary>
            <p>
-> Controllability: Ability to control a circuit's state or it's logic.

-> Observability: Ability to observe the circuit's state or logic.

-> Fault: Defect detected in design that may lead to system failure.

-> Error: A wrong signal outputted by a circuit.

-> Failure: Repeated occurances of faults or errors that leads to system failure.

-> Fault Coverage: The effectiveness of a test set in detecting faults. Calculated using percentage of faults that can be tested.

-> Defect Level: Refers to the number of defect chips which aren't detected as defected.
            </p>
            <summary>_How long can scan chains be?_</summary>
            <p>
Scan chains can be however long but the trade-offs need to taken into account.
With longer scan chains, the trade offs are:

-> Increase in number of ports

-> Increase in Area

-> Decrease in Performance

-> Increase in Test Time
            </p>
            <summary>_Draw the waveform of the following?_
            <img width="1055" alt="Screenshot 2024-05-29 at 2 47 43 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/83cf58f1-9371-4767-b6fb-ceabd259190f">
            </summary>
            <p>
<img width="1440" alt="Screenshot 2024-05-29 at 3 16 37 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ff8e0948-8ce4-4721-a352-45bc5f942971">

A posedge clock was considered for designing the waveform.

-Designed using https://wavedrom.com/editor.html
            </p>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 5-->
<details>
    <summary>Day 6: Introduction to Logic Synthesis</summary>
    <ul>
        <li>
            <details>
                <summary>Logic Synthesis</summary>
                <p>What is Logic Synthesis</p>
                <pre>
- Logic synthesis takes an RTL description of a circuit and converts it into a netlist of logic gates and 
their connections.
- HDL Compiler is used to convert RTL to Generic Boolean (without timing info)
- Design Compiler is used to convert the Generic Boolean into our Target Technology (with timing info)
                </pre>
                <p>What is Design Compiler</p>
                <pre>
- Design Compiler (DC) is a EDA tool used for Synthesis made by Synopsys
- dc_shell is used as the text interface & Design Vision is used as the graphical interface for the users
- Uses the .db format for library files
- .ddc files contain design information which can be used across various Synopsys tools
- Synopsys Design Constraint (SDC) file contains information about design constraints (power, timing and area) and 
uses TCL script
                </pre>
                <p>Design Compiler Flow</p>
                <pre>
|  Set & link .db 
V  Read .v filed
|  Read SDC
V  Integrate the Design
|  Synthesize
V  Report
|  Check Quality of Results (qor) files
V  Write Netlist
                </pre>
                <p>Netlist & Libraries</p>
                <pre>
- Design is written using standard cells (gates, mux, flops, etc) provided in .db
- Target Library is the database with standard cell information (area, pin names, timing)
- Multiple libraries can be appended using link library
                </pre>
                <p>Getting Started:</p>
                <pre>
- Target & link libraries must be specified.
- File formats have to be considered.
- For GUI:
    design_vision
- For non-GUI:
    dc_shell
- From non-GUI to GUI:
    gui_start/start_gui
- .synopsys_dc.setup is used for integrating libraries at startup
                </pre>
                <p>TCL Tips</p>
                <pre>
- Keep track of bracket types.
- Referring a variable uses $ at start.
- Assigning a variable doesn't require $ at start.
- * is used for matching string of characters
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Design Compiler Introduction</summary>
                <ul>
                    <li>
                        <details>
                            <summary>PART 1: Invoking DC Basic Setup </summary>
                            <p>Step 1</p>
                            <pre>
Go to work directory
<img width="272" alt="Screenshot 2024-05-29 at 11 10 10 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c1898944-c657-4367-9dfe-77669b0735ea">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Enable C Shell
<img width="266" alt="Screenshot 2024-05-29 at 11 15 11 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/218718b8-1f4c-4c5d-b3ab-d476a4f039e6">
                            </pre>          
                            <p>Step 3</p>
                            <pre>
Invoke DC using 'dc_shell'
<img width="326" alt="Screenshot 2024-05-29 at 11 16 44 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1ddf90d6-6063-4aba-9b78-d7a9130302d2">
<img width="1035" alt="Screenshot 2024-05-29 at 11 17 33 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5c5cb34f-43d4-459f-978e-eeef164e5dcb">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Read library
<img width="1095" alt="Screenshot 2024-05-30 at 12 39 11 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/18a875ce-7f44-4c99-ba0c-48f47da0254d">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Set target library
<img width="1198" alt="Screenshot 2024-05-29 at 11 38 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f3398dc4-f491-4523-b08d-801678c27e7a">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Set link library
<img width="1224" alt="Screenshot 2024-05-29 at 11 40 09 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1b3cacfd-f359-4f30-94e6-c39d9b9433f2">
Note: 
- This step is important to specify the said library for our design.
- '*' represents the library that is already loaded to DC. This is done to avoid overwriting of existing libraries.
- If the library was read and set after writing the netlist (Step 7), you can use 'link' after to link the library to the design
<img width="1314" alt="Screenshot 2024-05-29 at 11 59 30 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5d833966-4a25-4814-9021-4d700f848ccc">
                            </pre>
                            <p>Step 7</p>
                            <pre>
You can use echo to check locations of target library and link library
<img width="953" alt="Screenshot 2024-05-30 at 12 02 34 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/906bda39-e7b9-4c60-8c1f-4f25ee81a205">
                            </pre>
                            <p>Step 8</p>
                            <pre>
Read verilog
<img width="1300" alt="Screenshot 2024-05-29 at 11 45 27 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/313fb49e-f4b7-45f9-8ec6-f9dd2589476e">
Note:
- The register information tells us that the design is a 1-bit Flip Flop
                            </pre>
                            <p>Step 9</p>
                            <pre>
Compile the design
<img width="1112" alt="Screenshot 2024-05-30 at 12 08 13 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/188ec2ad-4474-4ced-9772-fcf4f292505b">
                            </pre>
                            <p>Step 10</p>
                            <pre>
Write verilog
<img width="485" alt="Screenshot 2024-05-29 at 11 51 13 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6e361556-5c2a-4e1a-a4e5-d71d50614840">
Note:
- -f refers to the format of the file to be written
                            </pre>
                            <p>Step 11</p>
                            <pre>
View the written netlist
<img width="263" alt="Screenshot 2024-05-29 at 11 53 29 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2711f662-f59a-4f7c-9c0d-cec9f95f8a1f">
<img width="622" alt="Screenshot 2024-05-30 at 12 11 10 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5b6be879-a9e0-469f-9f12-db9224510c5b">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 2: Intro to Design Vision</summary>
                            <p>Step 1</p>
                            <pre>
Enable C Shell
<img width="266" alt="Screenshot 2024-05-29 at 11 15 11 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/218718b8-1f4c-4c5d-b3ab-d476a4f039e6">
                            </pre>
                            <p>Step 2</p>
                            <pre>
Use 'design_vision' to laugh gui format of Design Compiler
<img width="358" alt="Screenshot 2024-05-30 at 12 33 34 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/f7241987-1b33-4b8a-8b02-c2eefe976a03">
<img width="800" alt="Screenshot 2024-05-30 at 12 34 34 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6cf70b0e-b2ab-4b47-9f17-c9246d91e070">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Write .ddc in dc_shell
<img width="334" alt="Screenshot 2024-05-30 at 12 44 08 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/0c1efd7b-1df6-441d-80e4-a1db95c0c52c">
                            </pre>
                            <p>Step 4</p>
                            <pre>
In design_vision, run 'start_gui'
<img width="230" alt="Screenshot 2024-05-30 at 12 46 58 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/55918560-bb8c-4560-b7c9-809843f7e67b">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Read ddc in Design Vision GUI
<img width="980" alt="Screenshot 2024-05-30 at 12 50 39 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/264a0f84-f367-4811-ad4a-83a2177edd5d">
                            </pre>
                            <p>Step 6</p>
                            <pre>
Open the Schematic View of the design
<img width="766" alt="Screenshot 2024-05-30 at 12 56 46 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/337b99c6-7f60-4fe5-ad1d-a2d50cfed1da">
<img width="1414" alt="Screenshot 2024-05-30 at 12 57 35 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7abb8a0e-d20c-4343-afa8-2d5f69250e49">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Double-Click on the module to view the standard cells
<img width="1129" alt="Screenshot 2024-05-30 at 12 58 19 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/57cd7f17-18ac-442b-b67e-aeaa5adbd67c">
                            </pre>
                        </details>
                    </li>
                    <li>
                        <details>
                            <summary>PART 3: Design Compiler Synopsys Setup</summary>
                            <p>Step 1</p>
                            <pre>
Use gvim to open a new file
<img width="434" alt="Screenshot 2024-05-30 at 1 14 02 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4597f1e5-0d35-463d-a313-980bab39beb2">
                            </pre>          
                            <p>Step 2</p>
                            <pre>
Add the following to the file and save
<img width="891" alt="Screenshot 2024-05-30 at 1 15 36 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3e6ab3e5-6963-4874-9eb0-0d7564bc6280">
                            </pre>
                            <p>Step 3</p>
                            <pre>
Enable C Shell
<img width="266" alt="Screenshot 2024-05-29 at 11 15 11 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/218718b8-1f4c-4c5d-b3ab-d476a4f039e6">
                            </pre>
                            <p>Step 4</p>
                            <pre>
Invoke DC using 'dc_shell'
<img width="326" alt="Screenshot 2024-05-29 at 11 16 44 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1ddf90d6-6063-4aba-9b78-d7a9130302d2">
<img width="1035" alt="Screenshot 2024-05-29 at 11 17 33 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5c5cb34f-43d4-459f-978e-eeef164e5dcb">
                            </pre>
                            <p>Step 5</p>
                            <pre>
Run echo to check target library
<img width="789" alt="Screenshot 2024-05-30 at 1 17 14 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7334fef5-3a9f-4c4c-b3af-9f9563294a71">
Note:
- Notice that the target library is already set without having to run read_db
                            </pre>
                            <p>Step 6</p>
                            <pre>
Open the Schematic View of the design
<img width="766" alt="Screenshot 2024-05-30 at 12 56 46 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/337b99c6-7f60-4fe5-ad1d-a2d50cfed1da">
<img width="1414" alt="Screenshot 2024-05-30 at 12 57 35 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/7abb8a0e-d20c-4343-afa8-2d5f69250e49">
                            </pre>
                            <p>Step 7</p>
                            <pre>
Double-Click on the module to view the standard cells
<img width="1129" alt="Screenshot 2024-05-30 at 12 58 19 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/57cd7f17-18ac-442b-b67e-aeaa5adbd67c">
                            </pre>
                        </details>
                    </li>
                </ul>
            </details>
        </li>
        <li>
            <details>
                <summary>TCL Scripting Lab</summary>
                <p>Step 1: Basic Commands</p>
                <pre>
Run the following commands to understand how to initialize and view variables
'set i 0' For setting a variable i to a value 0 
'echo $i' For checking value of i
'incr i' For incrementing the value of i
<img width="165" alt="Screenshot 2024-05-31 at 1 30 09 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5c2790b3-6439-4163-a2ef-c8e348a1a911">
                </pre>
                <p>Step 2: Run 'For' Loop</p>
                <pre>
Notice the error due to incorrect syntax,
<img width="427" alt="Screenshot 2024-05-31 at 1 28 53 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6b152b5f-6e95-4961-97fb-d9983f72a0b5">
The correct syntax is:
<img width="401" alt="Screenshot 2024-05-31 at 1 37 41 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6fa010df-12d3-48d4-91f3-50752522f535">
The output is:
<img width="28" alt="Screenshot 2024-05-31 at 1 37 48 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/1149a596-263b-4e3a-9441-38c32a635812">
                </pre>
                <p>Step 3: Run 'While' Loop</p>
                <pre>
Notice the error due to incorrect syntax,
<img width="463" alt="Screenshot 2024-05-31 at 1 43 55 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/892ca95e-bb43-4ec7-99f9-b718cce488a5">
The correct syntax is:
<img width="249" alt="Screenshot 2024-05-31 at 1 44 52 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c2707c00-1988-4b32-9232-896b241bdbbe">
The output is:
<img width="28" alt="Screenshot 2024-05-31 at 1 37 48 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/2ef02fea-58cb-4b61-93d2-349c767fbf09">
                </pre>
                <p>Step 3: Incrementing a variable</p>
                <pre>
Another way to increment a value other than the method shown in Step 1 & 2:
<img width="253" alt="Screenshot 2024-05-31 at 1 49 16 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets//daebf341-0464-4561-8155-4dde2c892758">
You can verify it by checking the output:
<img width="24" alt="Screenshot 2024-05-31 at 1 49 45 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/98fb4c55-3777-4b0b-9a5c-de4fa8bf4942">
                </pre>
                <p>Step 4: Creating a list</p>
                <pre>
Create a list using set command.
<img width="382" alt="Screenshot 2024-05-31 at 4 05 36 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/340a940d-ab8c-4371-b856-178be9744d3f">
                </pre>
                <p>Step 5: Looping through the list</p>
                <pre>
Instantiating my_var to each item in the list and printing it out until all the items from the list have been 
printed
<img width="28" alt="Screenshot 2024-05-31 at 1 37 48 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/3357d475-d5ce-4259-8b1b-d4d46a187593">
                </pre>
                <p>Step 6: Looping through a collection</p>
                <pre>
View all AND gates in .db file
<img width="1434" alt="Screenshot 2024-05-31 at 5 19 00 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c3209e08-df45-4b3f-bad6-dbfd31172127">
Instantiate my_var_name as the object name of my_var & print my_var_name
<img width="581" alt="Screenshot 2024-05-31 at 5 26 37 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/33e5965b-905e-4d76-b4b9-5fbfb71b18a7">
                </pre>
                <p>Step 7: Creating a TCL Script from DC</p>
                <pre>
Launch gvim from within DC
<img width="183" alt="Screenshot 2024-05-31 at 9 15 44 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9262935c-0634-49e9-b7ce-1362fc2365d4">
Press i to enter 'insert mode' and edit document with few TCL commands to test
<img width="1282" alt="Screenshot 2024-06-01 at 1 25 23 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ebbaa3d0-7f7a-4a55-a2e4-b18c1fed3bca">
Save file as 'myscript.tcl'
                </pre>
                <p>Step 8: Executing a TCL Script from DC</p>
                <pre>
Source the saved file
<img width="271" alt="Screenshot 2024-05-31 at 9 29 39 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6a4b7cf3-b6fd-4373-9667-6837f429c49f">
View that the output is as expected with all the commands added to myscript.tcl getting executed.
<img width="1440" alt="Screenshot 2024-06-01 at 1 26 22 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ecf5c13a-0396-40c4-8627-1ee0272699b9">
                </pre>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 6-->
<details>
    <summary>Day 7: Basics of STA (Exploring .libs)</summary>
    <ul>
        <li>
            <details>
                <summary>Timing .libs</summary>
                <p>Understanding the .lib settings</p>
                <pre>              
Open .lib using gvim to understand the settings
<img width="1440" alt="Screenshot 2024-06-03 at 7 53 58 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4de27d3a-0bde-4039-b548-a66950f794c6">
Notice the timing, voltage, power, current, resistance and capacitive units.
                </pre>
                <p>Max Transition</p>
                <pre>              
In a circuit such as the one below, output pin has a capacitance, each net has a capacitance, and input of each 
gate also has a capacitance. The load capacitance is the sum of all these capacitances. However, a larger 
capacitance gives rise to high delay which is not convenient. 
<img width="475" alt="Screenshot 2024-06-03 at 8 07 12 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/591fac3b-d8b0-4333-b21c-bd73d26aa319">
To solve this issue, we set a maximum capacitance. DC checks if a gate has a heavy load of capacitance (higher 
than the set capacitance) and breaks the net to create buffers to share the load in the following manner.
Point to note is that this limit set is a last resort scenario and this limit should never be met. 
<img width="256" alt="Screenshot 2024-06-03 at 8 21 01 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/33fd4053-2b51-4c77-b79f-283e5e09946a">
                </pre>
                <p>Delay Model Lookup Table</p>
                <pre>              
Delay is a function of input transition and output capacitance. For each cell, there's a table including delay 
information for each input transition and their corresponding output capacitances.
Design Compiler calculates the delay of a gate using the transition at input and output load. Using these values, 
the range of delay information is looked up from the lookup table and then they are interpolated to find the delay.
There are other such lookup tables for other parameters of a cell such as for power.
<img width="870" alt="Screenshot 2024-06-03 at 11 43 26 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9faa737d-bae0-4679-9b1a-91c08923d92e">
                </pre>
                <p>Comparing Cells</p>
                <pre>              
View the 2 AND Gates in gvim
<img width="1187" alt="Screenshot 2024-06-03 at 11 50 51 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6b5320e8-1b22-4191-bdf3-86ab9a09c7df">
You can see that the area in and2_2 is higher than the area in and2_0, implying that and2_2 is wider than and2_0 
and that delay in and2_0 is going to be more when compared to and2_2.
You can also observe that along with these comparisons, .lib also gives us information about its power pins 
(GND, nwell and pwell connections), leakage power, pin capacitance, max transition, direction of pins (input/output), 
falling power & rising power at various transitions, and timing information.
                </pre>
                <p>Unateness</p>
                <pre>              
Unateness describes the property where the output increses or decreases based on the change in inputs. These are 
categorized into three types:
- Positive Unateness:
                In this, when the input value increases, the output value either increases or stays the same. 
Similarly, when the input value decreases, the output value either decreases or stays the same. Ex: AND Gate, OR Gate, etc.
- Negative Unateness:
                In this, when the input value increases, the output value either decreases or stays the same. Similarly, 
when the input value decreases, the output value either increases or stays the same. Ex: NOT Gate, NAND Gate, NOR Gate, etc. 
- Non-Unate:
                In this, the change in input value doesn't determine the change in output value. Ex: XOR Gate, XNOR Gate.
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Exploring .libs</summary>
                <p>Understanding Flip Flops</p>
                <pre>

Name of Clock Pin of FF:
    'CLK_N' - Negative Edge Clock
    'CLK_P/CLK' - Positive Edge Clock

The Output Pin's (Q) timing type with respect to Clock Signal (CLK):
    'Rising Edge' - Denotes that Flip Flop is Positive Edge Triggered
    'Falling Edge' - Denotes that Flip Flop is Negative Edge Triggered
                </pre>
                <p>Understanding Latches</p>
                <pre>
Setup Time of Positive Latch is at the Negative Edge Clock

Setup Time of Negative Latch is at the Positive Edge Clock
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Exploring .libs (Querying the properties of .lib using DC Shell)</summary>
                <p>Step 1: Viewing all AND Gates in Library</p>
                <pre>
With the library loaded and assuming all AND Gates are named using and, use get_lib_cells to view all the 
AND Gates.
<img width="1429" alt="Screenshot 2024-06-11 at 9 13 48 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/c71cb5f8-6326-43e4-bd8a-551127a7ec6b">
                </pre>
                <p>Step 2: Viewing the gates one after the other instead of as a collection</p>
                <pre>
use foreach_in_collection and get_object_name to view the AND Gates one by one.
<img width="637" alt="Screenshot 2024-06-11 at 9 37 53 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/d605c087-e0cd-4977-bdb9-9a13b84622ef">
                </pre>
                <p>Step 3: Viewing the pins of a cell</p>
                <pre>
Use get_lib_pins to view the pins of any cell.
<img width="1426" alt="Screenshot 2024-06-11 at 9 43 57 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/74928568-f2a0-454c-8339-4611e6c62010">
                </pre>
                <p>Step 4: Viewing the direction of pins</p>
                <pre>
Use foreach_in_collection and get_lib_attribute to view the direction of pins.
<img width="1011" alt="Screenshot 2024-06-11 at 9 52 25 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/523e2afa-ecfc-432c-891d-a75122b9fa92">
                </pre>
                <p>Step 4: Viewing the functionality on output pin</p>
                <pre>
Use get_lib_attribute along with function to view the functionality of pins.
<img width="946" alt="Screenshot 2024-06-11 at 9 58 38 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/9ad5e61f-0663-485a-810d-c6c11cb9034d">
We can see that the functionality is an AND Gate as expected
                </pre>
                <p>Step 5: Viewing the output pin and its functionality for each cell in a list</p>
                <pre>
Creat a TCL script listing all the gates and to view output pins of each gate and their functionality.
<img width="442" alt="Screenshot 2024-06-11 at 10 17 36 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/de1522e9-61c3-41a1-87cc-fdc911366e22">
Source this script in dc_shell.
<img width="981" alt="Screenshot 2024-06-11 at 10 18 59 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/438f9567-3e05-4ee5-a443-6e5e06ad514a">
You can see the output pin of each gate along with their functionality.
                </pre>
                <p>Step 6: Other Attributes</p>
                <pre>
To view the area of a cell.
<img width="955" alt="Screenshot 2024-06-11 at 10 22 02 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/6b50059f-7b68-4572-80c5-c1f68ee76206">
To view the capacitance of a pin.
<img width="994" alt="Screenshot 2024-06-11 at 10 24 42 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/0bbe80c5-89ef-41bd-8d67-ba77e8d66fa0">
To view whether a pin is a clock signal.
<img width="991" alt="Screenshot 2024-06-11 at 10 26 06 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5cbbcedc-4afb-48e4-922e-9c098419b6d2">
To know whether there are any sequential cells in the library.
<img width="1429" alt="Screenshot 2024-06-11 at 10 28 22 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/4da4c3a2-5c3c-42fd-af3a-7d98d560d101">
To list all viewable attributes by dumping that information to a file 'a'.
<img width="313" alt="Screenshot 2024-06-11 at 10 30 46 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/01f93bc9-5423-40c9-b80d-9ee8f588c584">
<img width="646" alt="Screenshot 2024-06-11 at 10 31 25 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/64a02627-b485-4118-840e-d122eff72408">
                </pre>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 7-->
<details>
<summary>Day 11: Introduction to BabySoC</summary>
    <ul>
        <li>
            <details>
                <summary>What is SoC</summary>
                <pre>
- SoC is an integrated circuit which integrates most or all components of a computer system onto a single die chip. 
- SoC contains digital or analog components, memory interfaces, processors, input/output interfaces and other such 
components.
- SoC integrates all such components and ensures seamless working of these components together to work as a system.
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Structure of SnapDragon SoC</summary>
                <pre>
<img width="709" alt="Screenshot 2024-06-15 at 11 20 25 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/67d043a4-bcc8-4c40-9bf4-75d2e1598eb4">
- Snapdragon SoCs (by Qualcomm) contains a core processor that runs on ARM Architecture
- Uses Adreno GPU (Graphic Processing Unit) to handle graphic rendering and multimedia processing. Adreno GPUs are 
also designed by Qualcomm and their main application is for mobile and embedded applications.
- Snapdragon SoCs include Hexagon DSPs (Digital Signal Processors) to handle tasks such as audio/video encoding, 
image processing, sensor data processing, other such data processing tasks. Hexagon DSP is the DSP architecture of 
Qualcomm.
- A modem for cellular connectivity such as 4G LTE/5G networks, Wi-Fi, etc.
- Multimedia component is used for video encoding/decoding, multimedia playback and other multimedia tasks.
- Sensor Cores that control the sensors and their data.
- Camera Hardware Accelerators for video recording and other camera-related tasks.
- Display Hardware Accelerators for video-playback and other display tasks.
- Location Sensors that provide accurate location information and perform navigation related tasks. 
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Categories of SoC</summary>
                <pre>
There are 3 different categories:
- SoC built around microcontrollers.
- SoC built around microprocessors.
- Application Specific Integrated Circuits (ASICs)
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>SoC Design Flow</summary>
                <pre>
<img width="265" alt="Screenshot 2024-06-15 at 11 44 56 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/49986197-e15a-4292-b6fb-a60a7f6e6fb3">
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Intro to BabySoC</summary>
                <pre>
<img width="857" alt="Screenshot 2024-06-15 at 11 47 53 AM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/bca43a1d-f447-4108-8baa-4b87001dd96e">
BabySoC Components:
- RVMYTH: Simple RISCV-based CPU.
- PLL: Phased-Lock Loop is a control system that generates output signals used for sunchronizing purpose such as 
clock distribution.
- DAC: Digital to Analog Converter, as the name suggests, converts a digital signal to an analog signal. They enable 
the generation of digitally difined transmission signals used for communication.
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Intro to Modelling</summary>
                <pre>
- Input Signals are first fed into the BabySoC module that make the pll start generating the clock signal for the circuit
- This generated clock signal will make rvyth execute instructions to load register r17 with some values through various 
cycles
- DAC uses these values to provide the final output signal (OUT).                    
                </pre>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 11-->
<details>
    <summary>Day 12: BabySoC Modelling</summary>
    <ul>
        <li>
            <details>
                <summary>Modelling IP Cores</summary>
                <p>RVMYTH (RISCV based processor)</p>
                <pre>
- RISC stands for Reduced Instruction Set Computer as opposed to CISC (Complex Instruction Set Computer).
- It is an Instruction Set Architecture (ISA). 
- A simple one cycle CPU for RISC-V:
<img width="1012" alt="Screenshot 2024-06-15 at 12 40 03 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/ccd168ef-3a1e-484a-a97d-3a4ad531efe2">
-Pipelined Flow for RISC-V Processor Instructions:
<img width="865" alt="Screenshot 2024-06-15 at 12 42 08 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/76e0bd00-0856-4539-b6be-c7fe261e70dc">
                </pre>
                <p>Phased Locked Loop (PLL)</p>
                <pre>
- PLL is an electronic circuit with a voltage or voltage driven oscillator that matches the frequency of input signal. 
- Used to generate, stabilize, modulate and demodulate.
- Clock Signal is generated using Quartz crystal oscillators.
-These Quartz Crystal Oscillator would require to supply signal for a lot of blocks which can prove to cause delays due to long wires or different blocks would require different signal frequencies. In such oscillators, there occurs a ppm error which causes delay over time.
- To avoid such issues, we use a PLL that recieves the clock signal and adjusts it to the frequency it is expected to propogate.
- Components of a PLL:
    . Phase Detector: The change is crystal oscillator's phase is detected at the phase detector when the phase doesn't match that of the reference frequency. 
    . Loop Filter: Loop Filter generated a voltage signal that indicates the phase difference.
    . Voltage Controlled Oscillator: Based on the voltage recieved, it generates the clock signal that will be in the same phase as the reference frequency.
    . Frequency Divider: Used to reduce the frequency if required.
<img width="707" alt="Screenshot 2024-06-15 at 1 02 51 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/5807a110-f9f2-42e3-90af-5f3ee3cdf102">
                </pre>
                <p>Digital-to-Analog Converter</p>
                <pre>
- Converts a Digital signal to an Analog signal.
- Represented using binary codes.
- Types of DACs:
    . Weighted Resistor DAC:
        Produces an analog output by using binary weighted resistors in an inverting adder circuit.
<img width="493" alt="Screenshot 2024-06-15 at 1 09 10 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/30928319-9480-4758-8bb4-6d645fac5a6a">
    . R-2R Ladder: 
        Produces an analog output by using a R-2R ladder network in an inverting adder circuit.
<img width="673" alt="Screenshot 2024-06-15 at 1 12 08 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/8994fb05-fcb3-467a-8b60-d5c31d0fb3e8">
                </pre>
            </details>
        </li>
        <li>
            <details>
                <summary>Lab for Modelling BabySoC</summary>
                <p>Pre-Modelling Info:</p>
                <pre>
- HDL can be used for modelling and checking functionality using testbench for RVMYTH
- As DAC & PLL are analog systems, verilog can't be used to synthesize them. However, their functionality can be simulated in verilog using data-types such as real. This is done to verify its logical correctness.
- Verilog will be used to model, iverilog will be used to compile and simulate, and GTKWave will be used to see the waveforms of the design.
                </pre>
                <p>Tips on Modelling the Design</p>
                <pre>
- Avoid race conditions.
- Use optimized testbench for debugging.
- Create models that simulate faster.
- Use case sensitive behavior.
                </pre>
                <p>Installing Required Packages</p>
                <pre>
pip3 install pyyaml click sandpiper-saas
                </pre>
                <p>Cloning the VSDBabySoC Repository</p>
                <pre>
git clone https://github.com/manili/VSDBabySoC.git
                </pre>
                <p>Step 1: Translate .tlv to .v</p>
                <pre>
cd VSDBabySoC
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
                </pre>
                <p>Step 2: Load & Execute the Pre Synthesis Design</p>
                <pre>
Load:
iverilog -o output/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module
Execute:
./output/pre_synth_sim.out
<img width="1215" alt="Screenshot 2024-06-15 at 3 06 09 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/39431ce9-9f19-425a-bc43-5a597ff78061">
A .vcd file gets created
                </pre>
                <p>Step 3: Load the .vcd file to GTKWave to analyze behaviour</p>
                <pre>
gtkwave output/pre_synth_sim.vcd
<img width="577" alt="Screenshot 2024-06-15 at 3 08 50 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/b3058b10-6af4-46d2-89f9-27b08568dd51">
<img width="1440" alt="Screenshot 2024-06-15 at 3 09 47 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/d5c23930-b44c-4f0d-a994-23186ecd6a64">
Where,
CLK is the output signal from PLL and the input signal to RVMYTH
reset is the input signal to RVMYTH
OUT is the output signal of DAC and is the final output of VSDBabySoC
RV_TO_DAC[9:0] is the 10-bit output from RVMYTH
OUT is the output wire from DAC containing real analog values. To view this data, right-click on this signal and change the Analog type to 'Step' in Data Format.
<img width="1440" alt="Screenshot 2024-06-15 at 3 18 21 PM" src="https://github.com/c-dhanush-p/SFAL-VSD/assets/170220133/8def554c-4276-41c6-bf81-4fdc3844f2a8">
                </pre>
            </details>
        </li>
    </ul>
</details>
<!--End of Day 12-->
