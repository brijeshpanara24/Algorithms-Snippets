# Algorithms-Snippets
contains build systems (cpp build systems) and competitive coding algorithms snippet for sublime text 3.

# Intention
The main intention behind this repository is to help beginners in setting up cpp enviroment for competitive coding and making them familiar with build-systems and snippets to improve their coding speed.

Every competitive programmer faced one question at some point of time that which is best IDE which IDE use to do competitive programming.

Here is the answer, "Sublime Text 3" is one of the best IDE (might not best but definitely one of the best IDEs after all its all depends on coders choice), so here are some tricks in sublime text 3 for fast and efficient competitive programming. 

# Sublime Text 3 Download And Setup
* First of all check whether gcc/g++ compiler is installed in your machine or not, and if not then install it.
  
  For Linux - https://www.youtube.com/watch?v=mqHdXCMmOXM
  
  For Windows- https://www.youtube.com/watch?v=r3FJta3RD0s

* You can download sublime text 3 from https://www.sublimetext.com/3.

* To enable sidebar(sidebar show all open files/folders make navigation between files easy) go to
  
  view > sidebar > show sidebar

* To add folder to sidebar(after adding folder to sidebar, all files inside folder will be displayed in sidebar) go to
  
  project > Add folder to project > select folder

Adding Build Systems
===================

### Build System - 1 ###
 
* To compile and run cpp code from sublime text 3 itself on click of "ctrl+shift+B" we have to create build system.
  In this Build System cpp code will read input from file "input.txt" and will write output to file "output.txt".
  
  Here is the screenshot of how it will looks and works -
  ![](https://github.com/brijeshpanara24/Algorithms-Snippets/blob/master/screenshots/linux_cpp_1_without_error.png)
  ![](https://github.com/brijeshpanara24/Algorithms-Snippets/blob/master/screenshots/linux_cpp_1_with_error.png)
  
* First of all create two files named as "input.txt" and "output.txt" in current working directory(folder containing cpp file).

  **Note** - The cpp file you compile and run must be in same folder as both of this file else it will give error as build system will not found file to read input and write output of cpp code.

  To provide input to cpp code you have to write input in file "input.txt" and code will write output to "output.txt".
  To make it(providing input and reading output) easy, we will always keep "input.txt" and "output.txt" open as shown in above screenshots.
  To open such layout select
  * view > layout > columns: 3
  * view > groups > Max Columns: 2
  * Then open "input.txt" in upper right window and "output.txt" in lower right window and resize them according to your prefrences.
  
  I will suggest you to keep "input.txt" and "output.txt" always open in upper right and lower right windows while open your cpp code in left window and all your logic goes there.

* We are done with taking input and writing output now we have to write script to compile and run cpp code.
  
  * To create build system go to 
    
    Tools > Build System > New Build System 
  
  *
    * For Linux
      
      Copy paste given code and save it with name linux_cpp_1.sublime-build
      
      ```
      {
        "shell_cmd": "g++ \"${file}\" -o \"${file_path}/${file_base_name}\" && \"${file_path}/${file_base_name}\" <input.txt >output.txt",
        "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
        "working_dir": "${file_path}",
        "selector": "source.c, source.c++, source.cpp",
      }
      ```
    * For Windows
      
      Copy paste given code and save it with name windows_cpp.sublime-build
      
      ```
      {
        "cmd": ["g++.exe", "${file}", "-o", "${file_base_name}.exe", "&&" , "${file_base_name}.exe<input.txt>output.txt"],
        "shell":true,
        "working_dir":"$file_path",
        "selector": "source.c, source.c++, source.cxx, source.cpp", 
      }
      ```

  * To enable build system select
    
    * For Linux 
      
      Tools > Build System > linux_cpp_1
      
    * For windows
    
      Tools > Build System > windows_cpp

* To compile and run code, press "ctrl+shift+B".

### Build System - 2 (For Linux Only) ###
 
* To compile and run cpp code in terminal from sublime text 3 on click of "ctrl+shift+B" we have to create build system.
  
  Here is the screenshot of how it will looks and works -
  
  ![](https://github.com/brijeshpanara24/Algorithms-Snippets/blob/master/screenshots/linux_cpp_2_without_error.png)
  ![](https://github.com/brijeshpanara24/Algorithms-Snippets/blob/master/screenshots/linux_cpp_2_with_error.png)
  
  * To create build system select 

    Tools > Build System > New Build System 

  * copy paste given code and save it with name linux_cpp_2.sublime-build

    ```
    { 
      "cmd": ["g++", "$file", "-o", "${file_path}/${file_base_name}"], 
      "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$", 
      "working_dir": "${file_path}", 
      "selector": "source.c, source.c++, source.cxx, source.cpp", 
      "variants": 
      [ 
        { 
          "name": "Run", 
          "shell": true, 
          "cmd": ["gnome-terminal -e 'bash -c \"${file_path}/${file_base_name};echo;echo Press ENTER to continue; read line;exit; exec bash\"'"] 
        } 
      ] 
    }
    ```

  * To enable build system select

    Tools > Build System > linux_cpp_2

* To compile code 

  Press "ctrl+shift+B" and then select "linux_cpp_2".

  To run compiled code 

  Press "ctrl+shift+B" and then select "linux_cpp_2 - Run".
