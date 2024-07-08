# Expyriment documentation source
Used to build online documentation via CI at http://docs.expyriment.org.

## How to build manually (requires the unix `make` command)
1. Clone this repository
2. Clone [expyriment source](https://github.com/expyriment/expyriment)
3. To build the HTML documentation, run  
  ```make html EXPYRIMENT_PATH=<path-to-expyriment-source>```  
  where `<path-to-expyriment-source>` is a (relative or absolute) path to the cloned expyriment source from step 2
4. Find the built html files in the directory __build/html_

