# The computer and its operating systems

## Computer

Even though most bioinformaticians work on a variety of software packages for data analysis, efficient design and use of those software programs is not possible without understanding the properties of the underlying machine. In the next picture, we show a computer as seen by an user. The user interacts with it using a keyboard and a monitor, but the real action takes place in the large featureless box.

How does the computing machine process user's requests? The question is best answered by taking a look at the circuitry inside a computer. A simplified description of the circuitry focusses on two components - hard-drive and motherboard. The hard-drive is a cylindrical unit that stores all data from users, whereas the motherboard contains chips to perform computing. From time to time, data are pulled from hard-drive into the motherboard, analyzed and then the results are sent back to hard-drive for permanent storage.

Within the motherboard, the user sees a replica of the same pattern in the form of memory (RAM) and processor. The memory is the place for temporary storage of data brought in from the hard-drive, whereas the processor performs the computing. If an user is allowed to look inside the processor, he would identify smaller fractal pattern of the same structure in terms of cache memory and a computing block called arithmethc and logical unit(ALU). Modern multi-core processors take the pattern one step further by incorporating cache inside each core in addition to the global cache memory of the processor. Finally, the ALU itself is designed with registers for holding transient data and core logical block for number crunching.


When you see this repetition of storage and processing units at various scales, you can conceptually think about the computing machine as the solar system. The ALU (shown in black) sits at the center to perform all computing, while the hard drive is located at the farthest point from the 'sun'. In that context, the computing exercise is a repetition of dragging data from the hard drive to the ALU and sending back results to hard-drive for permanent storage. Suppose an user wants to add 2 numbers - 5 and 7. The numbers are stored in the hard drive, which is far, far away from the ALU. To add them once, it may make sense to carry the numbers to ALU, do the addition, and send the result 12 back to the hard drive. If the addition is immediately followed by another addition of 3 to the sum of 5 and 7, 12 needs to be again brought back from the hard drive all the way to ALU. Then, after the addition of 3, the result is sent to the hard drive again. That is not efficient at all, because the communication between the hard drive and motherboard is very slow. Therefore, the goal of all computer algorithms is to minimize the total time spent by various numbers to move between places by making intelligent use of temporary storages like RAM, cache and registers. Naturally, an algorithm that is deemed good for a slow hard drive may not be the best, if the same hard-disk is replaced with an expensive but faster SSD drive.




Understanding hardware infrastructure requires different analytical mindset than designing software programs. Algorithms are abstractions of the underlying computing system and are usually presented in a mathematical language. In contrast, hardware is described in physical terms, and all factors like physical location, type of connections, speed, etc. come into consideration in modeling performance gain through hardware replacement.

In the hardware world, the best way to visualize a complex data-intensive analysis is by making analogy with flow of water. During the course of computing, data flows from its original location through millions of intelligent pipes and channels, and gets morphed into the output. A carefully crafted solution removes barriers and creates as many parallel channels as possible, so that the data can flow very rapidly to its final form.

For example, the RAM is a lot closer to ALU and the programmer can reduce the time required for moving numbers back and forth between hard drive and ALU by temporarily copying them into the RAM. On the other hand, RAM is expensive it is not possible to get enough space as the hard drive. So, RAM needs to be used efficiently and that is where clever algorithm and data structure help.

RAM is still not fast enough and the programming speed can be further increased by adding more expensive cache memory closer to the ALU. However, cache being expensive is smaller in size than RAM and can carry even a smaller amount of data. The registers within the CPU are the fastest and can be cleverly used to speed up the processing dramatically. However, the registers hold very small amount of data and the coding to optimize their use becomes very difficult. So, most programmers leave it to the compiler to optimize that part.

Overall, one can make his code efficient by trying to visualize the entire process of movement of data between hard disk, main memory, caches, registers and back to disk and thinking about how his algorithm operates within that framework.



No matter in what language a software program is written, ultimately it is converted to the hardware language of 0s and 1s and the computing problem is solved at the hardware level. Therefore, having a mental picture of hardware is necessary to design efficient algorithms. Good programmers tend to understand their hardware well, and many of them prefer C/C++, because those languages provide the closest abstraction of hardware.

The best way to understand how a program works is by having a mental picture data flow through various pieces of hardware. Unlike sofrware programs, computing hardware is infinitely parallizable. The best way to visualize hardware is to think about flow of water. During a computing task, your data flows from its point of origin through various barriers and computing elements, get modified and finally get saved as results of calculation.

Here is the simple picture of hardware. At first, raw reads sit in the hard-drive. When a program processes the reads, data gets pulled from hard-drive to memory. During every calculation, it goes through the processor and memory blocks are updated. Periodically, or at the end of calculation, data gets written in hard-drive.





Think about a car. You can have a driver's view.
or you can see it from inside the engine.

If you only know the car from the driver's view, you do not know what is going on inside.

Similarly, the computer that you see in front of you is just an interface. The real computer looks like -
the attached figure.
It has RAM, processor and a harddisk.

Getting back to the computer, you can think about it as a giant calculator.
The processor is very similar to the buttons you press on calculator. There is not much difference. RAM is like the memory of calculator, but much bigger. However, RAM deletes everything, when you turn the machine off. The harddisk is where data gets stored for good.
Then why do we need RAM? It is because the hard-drive is very slow in operation.
I say all this, because the computer programs hide the hardware details, but to do the task well, you will need to have some conceptual understanding of the machine.



## Operating system

Your computer is a machine made of hardware components like processor, memory and hard-disk. Those hardware components can only 
understand the language of 0s and 1s. Therefore, dealing with the computer becomes very tedious, and an operating system is an 
abstraction created to help people work on their computers easily.

Linux is an operating system. What does an operating system do? An operating system is an abstraction created to help people work on their computers easily.

Given that operating system is an abstraction, a computer can have many different operating systems including linux (a type of UNIX), windows, Mac OSX (a type of UNIX), etc. to operate the same set of hardware.

Our cloud server has only linux installed. You have to run programs in it by accessing the server remotely (log in) and completing tasks through text-based commands.

