- What are you trying to do? Articulate your objectives using absolutely no jargon.

I will analyze different aspects of manipulating scalable time series and try to develop convenient data structure for storing, modifying, querying, and fetching the time series data without compromising the execution performance. 
The time series data consists of program execution information on different nodes of an HPC system. Enter and leave events depict the beginning and end of a program/process execution respectively. Each event has associated performance metric values (CPU rate, cache, buffers, etc.). To visualize these execution events along with the performance metrics, an effective data structure is required for handling this information. Typically, this dataset becomes too large to fit in main memory for longer running program execution and performance becomes slower as the dataset grows. Therefore, the intended data structure should be dynamic enough to handle in-memory and out-of-memory information; and optimized enough to handle faster as well as frequent queries over the dataset without compromising user interaction over the frontend visualization.


- How is it done today, and what are the limits of current practice?

Phylanx, a general-purpose computation system of distributed arrays to enhance operations over large-scale distributed system, is an actively developed system to provide the benefits of distributed resources for data scientists. The Traveler project is an integrated graph visualization system for asynchronous multi-task execution. It uses OTF2 trace data generated from Phylanx execution, parse them, and represent them in different interactive views. Each line from the OTF2 trace file is being analyzed, parsed, stored, and later provided to the frontend for visualizing. These parsed data are stored in a hashmap and the key of the hashmap is further stored on interval-tree. 
Limits of the current implementation:
Main data resides on a separate hashmap. An interval-tree stores the keys of the hashmap. Therefore, each query hash double overhead, first search on the interval-tree and then on the hashmap. 
For fetching filtered data, multiple interval-trees are used for each node location and metric. Which leads to redundant storing of same information.
Due to the redundancy, the data size grows exponentially and overwhelms the main memory.
The data has some dependency information (parent-child relation). Current implementation only stores next neighbor information, which forces manual trace-back to get to know common parent (on linear complexity).
Most of the data resides on secondary storage, which leads to higher overheads for fetching data.
No coherent caching or pre-fetching mechanism. 
Performance of each query reduces as the data size grows.

- What's new in your approach and why do you think it will be successful?

I’ll start my research study on Summed-area table and Fenwick tree, and investigate their applicability into the Traveler. The basic idea behind summed-area table is to do cumulative sum of consecutive indexes and store only the sum rather than the actual value. Then values related to a range of indexes could be determined by subtracting the value at the end-index from the start-index (line for 1D data, rectangle for 2D data). Rather than storing summation of consecutive indexes, The Fenwick tree stores sum of previous log(c)th index, where ‘c’ being the current index. 
This approach will speedup data fetching query from O(n log(n)) to O(n).
- Who cares? If you're successful, what difference will it make?
My intended design for the data structure will enhance the performance of the Traveler project which in turn will be beneficial directly for the Phylanx developers. I will also try to propose a generalized version of the data structure for handling big data on HPC systems in general. 

- What are the risks and the payoffs?

Finding out a suitable alternative to interval-tree suited with the problem domain in literature will be the first challenge. Also, mechanisms used in relevant fields need to be explored and proper investigation should be conducted on assessing the possibility of utilizing those mechanisms with some tuning or tweaking. In this case, defining the factors, on which the tweaking should be made, will be crucial to make those approaches adaptable to the problem domain.
Lastly, the intendent design might not outperform the existing implementation. Since, the existing implementation is already exploiting a well optimized interval-tree, outperforming its performance will be a great challenge.
Even if an alternate data structure couldn’t be found, incites gathered from this research will help to propose some optimization, in terms of performance speed-up, over the existing implementation. 

- How long will it take?

4 months (expected)

- What are the midterm and final "exams" to check for success?

#####Project Milestone One:

A concrete data and task definition will be made. Depending on that definition, an exhaustive and comprehensive literature study will be conducted. More than one data structure will be chosen for experimentation. A theoretical performance study will be done to assess their adaptability to the problem domain and applicability with relevant factors will be determined. 

#####Project Milestone Two (Midterm):

Depending on the outcome of the previous milestone, a full stack implementation (visualization on the frontend and data structure with relevant data handling procedures on backend) will be created.

#####Project Milestone Three:

A list of performance measurement metric will be determined. Relevant scripts or tools will be implemented to generate the performance data. A preliminary performance data will be collected, and depending on the measured data, more tweaking on the design will be done or some other techniques will be explored if necessary. 

#####Project Milestone Four (Final):

A comprehensive analysis on the performance data will be conveyed compared to the current implementation. More generalized implementation of the data structure will be proposed. A full report of the project, as a whole, will be provided.


