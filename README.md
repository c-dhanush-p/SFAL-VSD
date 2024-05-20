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
  </details>
  
