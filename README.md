# 
# COP5615 - Project 1

 To mine, hash bitcoins and display only those containing desired number of leading zeroes. 
 
 &nbsp;






### Team Members

 - Sri Borra (4407-0286)
 - Tarunchandra Narahari (5675-1165)
 
 &nbsp;

  
### Outline

 In this project, we have implemented 2 models. All the models perform tasks by spawning worker actors that work parallelly.

 **Model 1: Parallelism** 

 _bitcoin.erl on Single Machine_ 
 
 - All actors are intended to spawn in a single machine using this approach.
 - It requests input from the user for the number of leading zeroes and the number of systems. 
 - The boss actor divides the input, creates, and assigns worker actors to subtasks.
 - Worker actors do the tasks simultaneously and deliver the finish message to the boss actor.
 &nbsp;

 **Model 2: Parallelism on Distributed Systems** 

 _server.erl and client.erl on Two Machines_ 
 -

 - Through division, remote connection, and timely message passing, this paradigm is intended to spawn actors in two machines.
 - The server runs before the remote system (also known as the client), which creates half actors at each end as it waits for the server to pass the input (number of leading zeroes with the number of systems = 2)
 - The boss actor at the server side splits the input and creates and distributes subtasks to worker actors on both systems.
 - Worker actors run concurrently on both platforms and send end messages when the task is finished.
 - The boss actor is implemented so that half the actors are formed at the server (server.erl) and client (client.erl) side.


 &nbsp;


### Steps to run in VSCode Terminal

 Case 1: To display the results in model 1, we simply run the bitcoin.erl file by running the command: **_c(bitcoin)._**
 
 Case 2: In order to get results for distributed model, the steps are as listed below.

 - Run **_client.erl_** on the client system.
 - When the remote system is listening (ready to receive inputs), enter **_server.erl_** at the server side.

 **Note:** In both cases, users are prompted to enter two values viz; the number of leading zeroes and the number of systems they wish to incorporate (1 or 2).
 
 &nbsp;

### Observations
 - Size of the work unit that we determined results in the best performance for our implementation was approximately _1000000_. The number of subtasks given to each actor is 2 in our program. 
 
 - The result of running our program for input 4 zeroes is as shown below: ![output_4](https://user-images.githubusercontent.com/54497878/192125187-fb99f417-ce98-499f-96bd-92e98d967619.jpeg)

 - Running time and CPU time for the above occurrence was noticed to be _2483ms_ and _5703ms_ respectively. On average, the CPU : Real-time ratio is approximately 4:1.
 - The implementation is as follows:  ![single_imp](https://user-images.githubusercontent.com/54497878/192125503-93e6ee87-87eb-48a4-b261-1bf0ac4d1da4.jpeg)

 
 - The lower the value of number of leading zeroes, the higher the CPU : Real-time ratio (for one leading zero) as illustrated below. ![Snapshot_cpuratio7](https://lh5.googleusercontent.com/B5xjhMS2To9nNvQwMMjlUPmtjL-brJYcwRFckyEdnPuqKbUVzz25JJy1_fvlhecEJoBVOXiH1Zm0UoOclMsYW2xdtvIL_Ej4KYU3gBVpJ7cPkJe4BsWmnxkk2VyVxU39xg=w1280)

 - Likewise, we observed that CPU time was 6 folds the real-time in case of two leading zeroes. For three and five leading zeroes, it was observed to be 4 and 2 respectively.

 - The coin with the most leading zeroes we managed to find was _7_. ![Most_zeros](https://user-images.githubusercontent.com/54497878/192125386-39915948-6761-4181-9dc9-b4e0a6d72829.jpeg)

 
 - The largest number of working machines we were able to run our code with was _2_. 
 
 &nbsp;

### Results
 
#### Distributed Implementation
  In distributed implementation, hashes are computed on both systems by half the actors. The following images depict the result of model 2 on two systems: ![distributed](https://user-images.githubusercontent.com/54497878/192125280-82a9dcc3-712d-4572-bc3c-52c89e92918c.jpeg)

 &nbsp;
 
![dist_imp](https://user-images.githubusercontent.com/54497878/192125291-a6b4186a-1ed7-437b-99fb-95574a425e53.jpeg)


