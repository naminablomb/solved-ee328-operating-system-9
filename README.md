Download Link: https://assignmentchef.com/product/solved-ee328-operating-system-9
<br>
<h1>Banker’s Algorithm</h1>

<h2>1 PROBLEM</h2>

<h3>1.1 DESCRIPTION</h3>

WriteaproblemthatrealizetheresourceallocationanddeadlockavoidancealgorithmBanker’s Algorithm. You can see the detail in the end of chapter 7 of <em>OPERATING SYSTEM CONCEPTS WITH JAVA (Eighth Edition)</em>, page 344.

<h2>2 ALGORITHM</h2>

<h3>2.1 RESOURCE TYPES</h3>

Several data structures must be maintained to implement the banker’s algorithm. These data structuresencodethestateoftheresource-allocationsystem. Weneedthefollowingdatastructures, where n is the number of processes in the system and m is the number of resource types:

<ul>

 <li><strong>Available</strong></li>

</ul>

A vector of length m indicates the number of available resources of each type. If <em>Available[j] </em>equals k, then k instances of resource type <em>R<sub>j </sub></em>are available.

<ul>

 <li><strong>Max</strong></li>

</ul>

An <em>n ×m </em>matrix defines the maximum demand of each process. If <em>Max[i][j] </em>equals k, then process <em>P<sub>i </sub></em>may request at most k instances of resource type <em>R<sub>j</sub></em>.

<ul>

 <li><strong>Allocation</strong></li>

</ul>

An <em>n×m </em>matrix defines the number of resources of each type currently allocated to each process. If <em>Allocation[i][j] </em>equals k, then process <em>P<sub>i </sub></em>is currently allocated k instances of resource type <em>R<sub>j</sub></em>.

<ul>

 <li><strong>Need</strong></li>

</ul>

An <em>n × m </em>matrix indicates the remaining resource need of each process. If <em>Need[i][j] </em>equals k, then process <em>P<sub>i </sub></em>may need k more instances of resource type <em>R<sub>j </sub></em>to complete its task. Note that <em>Need</em>[<em>i</em>][<em>j</em>] <em>= Max</em>[<em>i</em>][<em>j</em>]<em>− Allocation</em>[<em>i</em>][<em>j</em>].

<h3>2.2 SAFETY ALGORITHM</h3>

<ol>

 <li>Let Work and Finish be vectors of length m and n, respectively. Initialize <em>Work = Available </em>and <em>Finish[i] = false for i = 0, 1, …, n – 1</em>.</li>

 <li>Find an index i such that both

  <ol>

   <li><em>Finish[i] == false</em></li>

   <li><em>Need<sub>i </sub>≤Work</em></li>

  </ol></li>

</ol>

If no such i exists, go to step 4.

<ol start="3">

 <li><em>Work =Work + Allocation<sub>i</sub></em></li>

</ol>

<em>Finish[i] = true </em>Go to step 2.

<ol start="4">

 <li>If <em>Finishi[i] == true </em>for all i, then the system is in a safe state.</li>

</ol>

<h3>2.3 RESOURCE-REQUEST ALGORITHM</h3>

Let <em>Request<sub>i </sub></em>be the request vector for process <em>P<sub>i</sub></em>. If <em>Request<sub>i </sub>== k</em>, then process <em>P<sub>i </sub></em>wants k instancesofresourcetype<em>R<sub>j</sub></em>. Whenarequestforresourcesismadebyprocess<em>P<sub>i</sub></em>, thefollowing actions are taken:

<ol>

 <li>If <em>Request<sub>i </sub>≤ Need<sub>i</sub></em>, go to step 2. Otherwise, raise an error condition, since the process has exceeded its maximum claim.</li>

 <li>If <em>Request<sub>i </sub>≤ Available</em>, go to step 3. Otherwise, <em>P<sub>i </sub></em>must wait, since the resources are not available.</li>

 <li>Have the system pretend to have allocated the requested resources to process <em>P<sub>i </sub></em>by modifying the state as follows:</li>

</ol>

<em>Available = Available −Request<sub>i</sub></em>

<em>Allocation<sub>i </sub>= Allocation<sub>i </sub>+Request<sub>i</sub></em>

<em>Need<sub>i </sub>= Need<sub>i </sub>−Request<sub>i</sub></em>

Iftheresultingresource-allocationstateissafe, thetransactioniscompleted, andprocess <em>P<sub>i </sub></em>is allocated its resources. However, if the new state is unsafe, then <em>P<sub>i </sub></em>must wait for <em>Request<sub>i</sub></em>, and the old resource-allocation state is restored.

<h3>2.4 IMPLEMENTATION</h3>

The program requires a txt file to read in matrix <em>Max </em>and the initial <em>Allocation </em>matrix is a zero matrix. The user is required to input a formatted txt file and the <em>Available </em>vector like

<em>java TestHarness &lt; input f ile &gt; </em>10 5 7

to execute the algorithm.

Then the program will ask the user to input a command iteratively. The user can use “status” to check current matrices an “exit” to quit the program. In order to request or release resources the user have to obey the format:

[<em>request || release</em>] <em>&lt; customer </em># <em>&gt; &lt;resource </em>#1 <em>&gt; &lt;</em>#2 <em>&gt; &lt;</em>#3 <em>&gt;</em>

And the result will be returned in the command line window.

<h2>3 RESULTS</h2>

<h3>3.1 ENVIRONMENT</h3>

<ul>

 <li>Windows 10</li>

 <li>Java Development Kit 1.8.0_131</li>

 <li>Eclipse</li>

</ul>

3.2 SCREENSHOTS OF THE RESULT

We use command line to compile and execute the program. The result is shown in Fig. 3.1.

<h3>3.3 THOUGHTS</h3>

The given interface helps me a lot when finishing this project. In this way the code becomes more standardized and neat.

Figure 3.1: Screenshot of Banker’s Algorithm