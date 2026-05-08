# PA-11

Topological Sort
Problem Context

In class, we discussed how to implement topological sort on graphs represented using adjacency lists. In this programming assignment , you will implement topological sort on graphs represented using "real" adjacency matrixes.

Additionally, your implementation will use a MinPriorityQueue to track which vertexes should be added next (instead of Stack or Queue). This ensures a deterministic order across implementations (e.g., there is only one possible topological sort).

More specifically, you will need to implement the following methods:

has_cycle(): Runs modified DFS from every vertex to check for cycles. Returns True if the graph contains a cycle, False otherwise.

get_incoming_edge_count(): Takes in a vertex index and the remaining edges in the graph. Returns the number of edges incoming to the vertex.

topological_sort(): Returns a list of Vertex objects indicating the topological sort for the graph. Must use a MinPriorityQueue.

You may add helper methods as needed.

Input

The input file topological.in includes a text representation of a graph in the following format:

The first line indicates the number of vertexes in the graph

Subsequent lines indicates the label for each vertex, one line per vertex

After the vertexes, the next line indicates the number of edges in the graph

Subsequent lines are formatted as follows: [from_vertex_label] [to_vertex_label] 

You may assume that the input file is formatted correctly (e.g., no duplicate vertexes/edges, only existing vertexes included in edges).

Output

The output file topological.out shows the corresponding output to the sample input file.

Note that if the graph contains a cycle, your code should produce output that says so, and should not perform a topological sort.

Approach

Feel free to reference In-Class Activity 24 and zyBooks Chapter 23.13 for how topological sort is implemented for graphs represented using adjacency lists. Feel free to reference In-Class Activity 23 for how depth-first search should be modified to implement cycle detection.

Try mapping out how the methods used to access graphs using adjacency lists can be translated into methods used to access graphs using adjacency matrixes. However, note that the adjacency matrix representation used here actually uses a 2D Python list.

Read through the provided implementation of the adjacency matrix and note the differences from the adjacency matrix covered in class as well as the differences from the adjacency list representation.

How is a graph created from the input file?

How does add_vertex() work?

How does add_edge() work?

How are edges represented in the new adjacency matrix?

Is the from_vertex along the rows or the columns?

Is the to_vertex along the rows or the columns?

To get a vertexes outgoing edges, should you get a row or a column?

To get a vertexes incoming edges, should you get a row or a column?

To check for a cycle, note that depth-first search needs some substantial modifications. Because DFS returns a traversal, it is not sufficient to check for a revisited node. Remember that a cycle is a path where the starting vertex is the same as the end vertex. Given a DFS traversal from a starting vertex, how can you tell if DFS has found a valid cycle back to an already visited vertex?

There are many options for implementing cycle detection, some easier to work with than others. We recommend using these guiding questions to help design your implementation:

We need to be able to track whether a Vertex object is unvisited, visiting, or traversed. Will you add this information as an attribute to the Vertex object or will you track this information as the modified DFS algorithm runs?

Both recursion and iteration work here. Which one makes more sense to you?

When should we change a Vertex object from unvisited to visiting? When should we change a Vertex object from visiting to traversed?

If I see a Vertex marked as unvisited, is there a cycle? If I see a Vertex marked as visiting, is there a cycle? If I see a Vertex marked as traversed, is there a cycle? 

Starter Code

The starter code includes a complete main() method. We have also provided a helper __str__() method in Vertex to help print the topological sort.

Notice how the main method includes a debug flag. When set to True, notice how your program will use the topological.in file as the input, which you can use to write custom test cases. When set to False, the program will use stdin. Make sure to set debug to False when submitting as the grading scripts will pass inputs through stdin.

Take note of the code style used in the starter file. We will apply a similar rubric (see below) when manually assessing code style.

Grading

Grading scripts (automated): 70/100 points. The test cases will test your code against different graphs.

Code review: 30/100 points. TAs will complete a manual code review for each assignment, similar to how a Team Lead would complete a code review in a professional setting. TAs will also complete a technical requirements review in addition to a code style review.

Please refer to the following code style guidelines for this assignment: 15/100 points

Readability: Descriptive variable and method names, no unused code, no commented out code, and proper indentation.

Documentation: One comment per added/modified method describing the input, output, and purpose of the function. Optional additional comments describing high level purpose of each step within a method.

Organization: Lines of code are less than 100 characters long, methods have one primary purpose, logical structure to approach.

Please refer to the following technical requirements for this assignment: 15/100 points

Implementation uses adjacency matrix representation of graphs.

Implementation uses MinPriorityQueue to track Vertex objects.

Cycle detection uses modified version of depth-first search on every vertex.
