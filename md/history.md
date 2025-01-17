<img src="pic.jpg" alt="Good Photo of Me" width="200" class="left"/>
Hello, my name is Jean-Baptiste Besnard and I'm a computer scientist. I work mainly on parallel systems with a focus on runtime and profiling aspects. 



# At the Beginning...

My interest in computers dates back to my childhood, I've started on an IBM PC with an 8088 and Windows 3.1. I was among the ones leaving the "Turbo button" always on -- why not doing so? I started programming on Quick Basic around the age of 10, there I discovered my taste for blue backgrounds and learned that the PC speaker was able to generate unbearable noises. Followingly, I did some C++ with Borland C++ IDE. I then pursued under Windows and developed in Visual Basic some tiny projects, a vocal assistant leveraging the Microsoft Assistant API (mine had the Merlin skin). Then I did some dumb projects such as a Mail Bomber (it valued me a personal call from my ISP, I promised not to do it again). After, I switched to Linux around 15 years old, started to learn C, Bash, System administration (by first breaking several systems!). My first Distro was a Mandrake as it was a French one and that it was integrated enough to be usable "out of the box". At that times I got interested in parallelism and deployed a small OpenMosix cluster.

# Studies and Engineering School

I pursued scientific studies and implemented a few projects such as a code breaker for mono-alphabetical substitution using both statistical analysis and word patterns, it was done in PHP MySQL (do not ask why). This project included steganography to hide text in images. Meanwhile, I practiced Casio Basic intensively to take advantage of my Graph 100. I then entered mathematics preparatory school (CPGE PCSI) for two years before starting my engineering school at <a href="http://isen-brest.fr/">ISEN Brest</a>. I made a real-time hand and face tracking project in C++ based on the OpenCV library and parallelized in OpenMP. It relied on skin color segmentation and apriori knowledge of the body shape. I also made a Bayesian classifier able to sort objects captured on a webcam given morphological and color attributes. I spent four months developing a <a href="https://en.wikipedia.org/wiki/DVB-T">DVB-T</a> parser in C to debug video playback problems, during this same training I also had a small commit in VLC and was sensitized to Open-Source development. In 2010, I obtained an engineering degree Networking and Telecommunication major with a background in electronics.

# Ph. D Thesis on Performance Tools

The same year I started working at CEA in a work-study program I developed performance monitoring tools for HPC clusters. At this time I discovered the <a href="http://malp.hpcframework.com/">Multi-Processor Computing (MPC)</a> runtime and got familiar with profiling concepts and tools. I first wrote a tracing tool using OTF1 and observed the limitations of the format relatively to threads. I then developed my own trace format, the <a href="https://www.vi-hps.org/cms/upload/material/tw09/vi-hps-tw09-MPC_Trace_Library.pdf">MPC Trace Library</a>. It used a binary storage and hierarchical auto-numbering of ranks (OTF1 had an ASCII state machine) through a breadth-first search. Post-Mortem traces were processed in parallel using a callback-oriented trace reader and the final output was PDFs describing the parallel execution.

My thesis began with the development of new analysis aimed at massively parallel applications. By relying on our trace format and parallel analyzer, we generated profiling reports (in PDF) for several production-grade applications. Nonetheless, when the number of files was approaching the number of nodes (4370 on Tera 100), we observed a severe performance penalty, encouraging us to rethink our instrumentation-analysis coupling. Indeed, file-system being a shared resource subject to contention, it is crucial to preserve it. Our bet was then not to use the file-system at all, preserving in the meantime the parallelism between instrumentation and analysis. Moreover, we were then able to dimension the analysis such as it maximizes the bisection bandwidth. Thanks to this mechanism, we instrumented applications at the scale of ten thousands of cores, manipulating data volumes in hundreds of Tera-Bytes. It shall be noted that this approach led to higher cumulative bandwidth than the file-system (98.5 GB/sec for 2560 analysis process). By dedicating cores to the on-line processing of performance events, we avoided the storage of temporary trace data, focusing only on the final result. These features were regrouped in the <a href="http://malp.hpcframework.com/">MALP tool-suite</a>.


# PostDoc as Research Engineer

After my thesis, I joined the Exascale Computing research laboratory to pursue the development of my tool.
My work consisted in the industrialization of MALP which had to move from the proof of concept to an integrated tool. We had to partially rewrite some features while integrating others. We also developed a new web interface in place of previous LaTex (or PDF) reports. The web approach allowed us to propose richer interactions with measurements (now stored in JSON) with for example 3D visualizations (WebGL with three.js). Moreover, in order to speed up analysis module development, MALP relied on its own template engine, gathering the HTML layout and both client and server side Javascript in the same source file (using Node.JS). Eventually, laboratory partnerships allowed us to test MALP over representative applications from aeronautics and chemistry in order to get a better understanding of user’s need, confirming some advantages of MALP over other tools.

# Expert in High-Performance Computing

I've been the first employee of the ParaTools SAS office in France, I've been in charge of fulfilling statements of work close to research subjects.

Below is a list of subjects I've dealt with, enriched with a short description:

- I started with developments in the MPC MPI runtime and integrated MPI-IO support by porting the ROMIO source code;
- I reworked the datatype engine in the MPI runtime to provide support at the 3.1 level. In particular, I've extracted datatypes' footprints to factorize datatypes with ref-counting, indifferently from their generating function;
- I then worked on the network part implementing configurable multi-rail in the runtime, configured through an XML file;
- On compiler side, I worked on privatization and developed a compiler pass in gcc to support edge-cases in the privatization of variables (initialization chains), a process which enabled reliable compile-time transformation to run code in user-level threads;
- I've implemented the full RDMA support inside the MPC runtime. It is based on a modular structure integrated into the multi-rail engine. It also includes, emulated calls on top of active messages and shared-memory (and same node) optimizations;
- I've worked on collective operation algorithms in shared-memory context to be able to extract parallelism while maximizing local processing for collective operations. This work was extended to node-local collectives through shared-memory segments;
- I've integrated container support in the pcocc orchestrator both inside pods (using a Go agent) and natively using rootless containers. To do so I relied on the OCI image format both exporting and importing in native Python.


This work was mainly targetted at updating the support for the MPI standard in the MPC MPI runtime.

Due to the small size of the company my responsibilities also included general operations, communication and some administrative tasks. The company hired two new collaborators and I've then been promoted to a position including a management role.


# Manager and Technical Leader (Current)

As the company grown with new hiring it was necessary to structure it slightly more hierarchically. My responsibilities then included the management and timely delivery of work for a small team. Meanwhile, administrative work and the writing, reporting, and conduct of research project also became one of my attributions. I've also pursued developments as a consultant. In particular, I've participated in the development of an orchestrator for virtual machines by developing a virtualization agent (in python, Go and GRPC). Followingly, I've implemented OCI container support in this hypervisor by deploying support for execution in both Pods and Rootless environments -- leveraging existing tools and runtimes. ParaTools also founded (with four other partners) a working group in the MPI Forum (home of the MPI standard) dealing with hardware topology. I've been in charge of participating to this group led by INRIA Bordeaux, and which goal is to produce valuable hardware abstractions to target next HPC architectures.
