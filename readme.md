## Distributed Operating Systems Project - 4 (Part 1):

# Group Members:
Raghuveer Sharma Saripalli - 5094-6752
Vangmayi Vydyula - 3549-3676

# Outline
The main aim of this project is to implement a Twitter clone engine and an Actor - model based client tester/simulator. 

# Pre-requisites:
•	Visual Studio code
•	.NET version 5.0.207
•	NuGet Akka.NET v1.4.25

# Language Used:
F#

# Input:
dotnet fsi twitter_engine.fsx
dotnet fsi twitter_simulator.fsx <server IP address> <server port> <number of clients>
1. server IP address – The IP address of the server is to be mentioned on the client terminal to be able to connect with it.
2. Server port – This is the port of the server machine where the engine is currently running
3. Number of clients – The number of clients the machine is to handle.


# Steps to compile and run
1. Unzip the Project 4 – Part 1 folder to retrieve the twitter_engine.fsx  and twitter_simulator.fsx  files.
2. Open these files using the VSCode (Visual Studio Code) editor
3. Open terminal and execute the command "dotnet fsi twitter_engine.fsx on the server machine.
4. Open terminal and execute the command “dotnet fsi twitter_simulator.fsx <server IP address> <server port> <number of clients>” on client machine where angular braces are to be filled by the user.
5. We will see the output tweets on the client terminal.


# What is working:
•	The project mainly consists of 2 components. 

•	The server: This is the side which handles all the requests from the client and distribute the work to various actors to perform different operations and send the final output back to the client. The operations performed by the server can be divided into further categories:

1.	Handling Requests: This section of the engine is handled by a procedure called the “Handle Requests”, which accepts all the requests from the client and distribute the work to various actors or specific functionalities depending on the type of request received. It also prints the figures and statistics after every 10000 requests.
2.	Handling Registration: This process is handled by a method called the “Handle Registration” which creates actors to perform actions such as login, logout and registration requests from the client. Each of these handlers have individual modules to help with the functionalities of the handler.
3.	Handling Followers: Handling followers involves functionalities such as adding followers to the client and sending a tweet to all of the client’s followers. These functions are carried out by the actors created by the “Handle followers” method. 
4.	 Handling Tweets: Tweet handling involves the functionalities of handling new tweets and retweets. Each of these functions are separately implemented in the “tweetFunctions” module which is carried out by the actors created by “Handle Tweets” function. This handler receives it’s input from the client through the request handler and it then creates actors based on the specific functionality it is supposed to perform.
5.	Parsing Tweets: This is a handler to parse the tweets, hashtag extraction, and handling mentions by other users. It creates actors to perform these functionalities.
6.	Main Handler: This is the main handler which glues all of the other handlers together. It gets all the tweets, mentions and hashtags and prints statistics for the required data.

•	The client: This is the simulator side of the code which makes all the requests and sends them to the server and then receives the requested data from the server. This section creates clients, performs functionalities such as registration, adding subscribers, sending the tweets etc. The aforementioned functions are performed by the simulator. The client is basically the user who can tweet, login, logout, register, follow, subscribe, get tweets. The simulator makes the client use the Zipf distribution to perform all these activities. 
-	Zipf distribution: Zipf distribution is basically a mathematical distribution that is used when there are multiple types of data to be studied. It establishes a relation between rank order and the frequency of occurrence of a statistic. So, in our case we observe that our clients are ranked in the order of 1 to N, where N is the number of clients. Each client makes 1/rank number of requests per millisecond to the server. Refer to the graph below for the zipf distribution results of the client activity being inversely proportional to the rank.
-	The program works such that for every 100 requests, we would get a login and a logout request.
-	One out of every 10 requests is a retweet.
-	Out of every 1000 requests we would have a get tweet and a mention.
-	These are the conditions specified in the client section of the code.



# Largest Network managed - 
Largest Network Managed – The largest number of clients managed was 2000. Testing above that would have given results but it would have taken more time. Further, we tried to connect the server with multiple client systems (3) and it worked well. 


# Note:
For the performance results, output screenshots and plot graphs, refer to Report.pdf in the same file.
"# DOS" 
