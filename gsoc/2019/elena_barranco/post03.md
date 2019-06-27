# Improvement in the search of Interfaces


Until now, we just had the parseCDSL file to extract the information from the CDSL file and organize it into a component structure and to check if certain syntactic errors were written. After carrying out some test, we could check that this file was able to:  
  
- Detect if the keywords are written correctly (import, component, communication, etc.).  
- Detect if symbols are missing or left over (keys, semicolons).  
- Detect strange characters between different blocks.  
- Check that the imported interfaces exist in the directory.  
  
Looking at the results we found two main problems:  
  
- All the semantic part was not developed.  
- The way the program searched interface files was not correct. We must consider that every interface could need several files to work properly, and every file could be used by several interfaces. Further, some interface names are different from the file they need. All these point were not taken into consideration.
  
To solve these issues we have created a new file called "parseGUI.py" and we had to modify the existing "parseCDSL.py". The following methods have been added:  
  
-  get_interfaces_names() and load_all_interfaces() to load a dictionary with the name of the interface as key and the files it needs as values.  
-  check_file() to manage the file and errors.
-  get_files_from_interface() and get_interface_from_files() to load the corresponding files or interfaces.  
  
This main features are now developed. However, we need to restructure the second file to adapt it to the graphical interface, so this is our main task at the moment.  
  
At the same time, we are investigating about the possible frameworks and tools necessary to implement the features that we planned for the graphical interface.
