### The Traveler Project
The Traveler project is an integrated graph visualization system for asynchronous multi-task execution. It uses OTF2 trace data generated from a program
 execution on Phylanx, parses them, and represents them in different interactive views. Phylanx is a general purpose computation system of distributed arrays
  to enhance operations over large-scale distributed system. It is an actively-developed system to provide the benefits of distributed resources for data
   scientists. Phylanx first translates the code into PhySL, an intermediate representation in a domain-specific functional language. The function calls
   , control flow operations, data operations, and blocks found in the PhySL representation are referred to as primitives. These primitives are translated to
    tasks in the HPX, a C++ standard library and asynchronous tasking runtime. The dependencies of each primitive are the arguments it needs to execute
     (which may be other primitives), data access operations, or any other constraints on variables the primitive uses.
     
### Traveler System Organization
![Traveler System Architecture](https://github.com/sayefsakin/695C-spring-20-notes/blob/master/misc_figures/traveler-architecture.png "Traveler System Architecture")

The Traveler project follows MVC (model-view-controller) design pattern for developing the user interface, partitioning programming logic, and
 backend data handling. While logic and components for the frontend (view and controller) are written on javascript and presented on an interactive web
 -interface, the logic for backend (model) data structure, handling, parsing, storing, querying are mostly written on python. An intermediate object model
  ([LinekdState.js](https://github.com/hdc-arizona/traveler-integrated/blob/c80304293e60d380989ae1b4ba9c63416f64875f/static/models/LinkedState.js#L4)) is
   used on the frontend to speedup data handling.
   
#### Backend
The backend tasks of the project is divided into two sub-tasks: bundling ([bundle.py](https://github.com/hdc-arizona/traveler-integrated/blob/master/bundle.py)) and serving ([serve.py](https://github.com/hdc-arizona/traveler-integrated/blob/master/serve.py)).

1. Bundling

The bundling allows users to load different OTF2 traces, dumps from phylanx runs, individual trees, performance CSV files, python sourcecodes, PhySL
 representations, etc. The following command can be used to bundle the trace data,
 
 ```shell script
./bundle.py --otf2 data/lra_csv_2019-12-05/OTF2_archive/APEX.otf2 --label "LRATestRunupdated"
```

This OTF2 trace data was generated from a linear regression execution on Phylanx system. The OTF2 trace data can be printed using otf2-print command and read
 using less on unix environment from the root directory of the project.
 
 ```shell script
otf2-print data/lra_csv_2019-12-05/OTF2_archive/APEX.otf2 | less -S
```

![Sample print from the OTF2 trace data](https://github.com/sayefsakin/695C-spring-20-notes/blob/master/misc_figures/sample-otf2-print.PNG "Sample print of the OTF2 trace data")

This represents a sample print of the OTF2 trace data. In this trace file, each row contains the following attributes:
- Event (Categorical) : {ENTER, LEAVE, METRIC} Indicating the arrival (ENTER) and departure (LEAVE) event of a particular primitive and relevant metric
 (METRIC) values for the preceding rows event. The metric is various performance data like CPU cycles, cache misses, memory available, etc.
- Location (Categorical) : The hardware core number starting from 1,2,. . . , etc. - where the actual processing executed.
- Timestamp (Quantitative) : Actual temporal data in nanoseconds.
- Additional Attributes : This column contains some additional categorical attributes like GUID; parent GUID; primitive name; metric id, name, value, etc.
