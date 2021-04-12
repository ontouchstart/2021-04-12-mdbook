# From PDP-11 to the Web

## Data Processing

Troff was originated in the UNIX system running on PDP-11 computers. PDP stands form **Programmed Data Processor**. According to PDP11 Handbook,
> PDP-11 is Digital's answer to the demand for a modular system for real-time data acquisition, analysis and control.

**Data Processor** is a name for an era of computers designed for data processing instead of human communication. However, the word **Program** brings humans into the system. UNIX is an opertating system written by programmers for programmers first, data processing the second. Universal computing and flexibility of programming makes human-centric computing more powerful than data-centric data processing. 

On the other hand, the inventors of UNIX designed a beautiful data-centric workflow to mangage human activities efficiently with limited computing resources such as CPU, memory and storage.

Similar to the PDP-11 hardware systems that
> can handle a wide variety of real-time control applications -- each system being individually tailored from a comprehensive array of modular building blocks.

Troff is also a modular system that can handle a wide variety of programming tasks from a comprehensive array of software building blocks. The essence of UNIX philosophy is small programs doing specialized data processing jobs with synchronized data pipes. A troff pipeline takes text files written with pre-defined commands, macros, and contents as input, filtered with sequence of compilers that transform data from stages to stages. The final output would be the data that drive terminals, printers or typesetters. 

In the modern groff based system, the output can be PDF files instead of hardcopy output from the typestters.

Here is an example
```
{{ #include hello_troff/hello }}
```

This command will generate the [PDF output](hello_troff/hello.pdf)
```
groff -Tpdf -ms hello > hello.pdf
```

We can put it in a `Makefile`
```
{{ #include hello_troff/Makefile}}
```

This *make-driven* pipeline of generating output files from input files is a typical UNIX workflow. And we can say UNIX is a maker's computing system. With modern software terminonlogy, we usually call it *build system*. 

From human interactivity standpoint, this is a *reader/writer* creative pattern that plays a big role in the history of civilization. In this pattern, reading is *input*, writing is *output*. Depends on which side of the pipe `|`, the same data can be input or output. We write something so that it can be read; we read so that we can have something to write about.

This read/write pattern is also very resource efficient. A single human being can write text that can be read by millions of people. And a person can read very efficiently with enough education and concentration. On the machine side, the original basic PDP-11/20 has
> 4,096 words or read/write memory

It can handle a large system like troff because with the pipeline, each module only consume small amount of memory before the task is passed to the next one. There is no much memory used to run system that does nothing but waiting for user interaction. UNIX pipelines have no loops.   

## Read–Eval–Print Loop (REPL) and Client/Server

In principle we can start a computer, process the data, get the output and then shut it down. This is a batch processing mode. The next level of human interactivity is Read–Eval–Print Loop (REPL) in which the computer returns to waiting for user input after the job is done. In UNIX, interactive shells and editors are working in this way. REPL is a request-response pattern that works the same as in the client-server model. With light weight message data, REPL and request-response use little resources when waiting for user/client input. That is the reason that they can run in UNIX systems with limited resouces. 

## Graphical User Interface (GUI) and state management

The next break through in human computer interface is the invention of Graphical User Interface (GUI). GUI requires more resources to run and more complicated state management for control. Model–View–Controller (MVC) and Object-Oriented-Programming (OOP) are invented to fit this need. Traditional desktop operating systems like Microsoft Windows and Mac OS X as well as the **What You See Is What You Get (WYSIWYG)** applications built on top of them need more resources to run.

Modern web browsers are the most sophisticated general purpose GUI applications that runs on desktop computers as well as mobile devices. It runs both the client-server pattern for data I/O and Object Oriented Programming for state management and user interaction. With JavaScript and HTML/CSS render engines, programmer use [Web APIs](https://developer.mozilla.org/en-US/docs/Web/API) to implement rich user interface.

[mdBook](https://rust-lang.github.io/mdBook/index.html) is a command line tool that generate rich web pages, a 50 year journey from [troff](https://www.troff.org/).