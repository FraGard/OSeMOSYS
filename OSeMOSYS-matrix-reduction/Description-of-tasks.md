![SE4ALL logo](https://github.com/KTH-dESA/OSeMOSYS/blob/master/OSeMOSYS-matrix-reduction/SE4ALL.png "")

[**Back to the challenge page**](http://bit.ly/2erQwcY)

Challenge

Objectives of the #SE4All Challenge:

The task

Datasets

Deliverables

## Challenge:

**We challenge you to** **reduce the size and generation time of the Linear Programming (LP) matrix generated by OSeMOSYS.**

**Deadline: 18 December, 2016**

## Objectives of the #SE4All Challenge:

We challenge you to reformulate the OSeMOSYS code with the following objectives:

- The matrix of constraints generated by the program must include only combinations of &#39;Technologies&#39; and &#39;Fuels&#39; for which there are user-defined connections;
- The time for generating the matrix and solving the optimisation must be reduced at least by around 75%;
- An elegant, fully documented and understandable formulation of the new code and a Change Log of the difference with the old code must be produced.

## The task:

Please follow the following steps in preparation of your submission:

**1) OSeMOSYS and documentation -**  Information about its ethos and structure can be found in the first [publication](http://www.sciencedirect.com/science/article/pii/S0301421511004897) featuring the model, dating to 2011. In line with Open Source modelling guidelines, the model documentation is always provided as (1) a plain english description, (2) an algebraic formulation and (3) the code formulation. The user manual, version history and information related to its application and its community can be found on the website [http://www.osemosys.org/](http://www.osemosys.org/). A collection of downloadable versions of OSeMOSYS can also be found in a github [repository](https://github.com/KTH-dESA/OSeMOSYS).

**2) Run OSeMOSYS with two case studies -**  OSeMOSYS can be run through the command prompt. For detailed information on how to run a simulation, please refer to the [user manual](http://users.osemosys.org/uploads/1/8/5/0/18504136/new-website_osemosys_manual_-_working_with_text_files_-_2015-11-05.pdf), Section 3.

The following steps must be followed when running the simulations:

- **Close all the running applications before starting the simulation.**

- For comparability of results, use [**GLPK v4.55**](https://sourceforge.net/projects/winglpk/files/winglpk/GLPK-4.55/winglpk-4.55.zip/download) as a solver;
- As a model, use the version of OSeMOSYS provided in the section &#39;Datasets&#39; ( **osemosys\_modelfile.txt** ).
- For the simulation, you are provided with the datafiles of two case studies: 1) **utopia.txt** - A small and fast test case study you may use to perform quick tests when changing the code 2) **country\_casestudy.txt** - representing a real 3-countries case study developed at KTH-dESA. The final results you deliver must be from this case study, for us to be able to verify the performance improvement. Links to both files are in section &#39;Datasets&#39;.
- Add the command to print the output .txt file and call it: **results\_countrycasestudy.txt**.
- During the computation, record from the command prompt the matrix generation time, the original and pre-solved LP matrix dimension (rows, columns and number of non-zeros), the optimisation time and the memory used.
- Provide both the **results\_countrycasestudy.txt** output file and the **SelectedResults.csv** file generated by the computation (both are generated is the same GLPK folder as the model file, data file and solver are).

**3) Modify OSeMOSYS -** Change the code of **osemosys\_modelfile.txt** in such way that the solver is able to generate equations only for the Technologies and Fuels having user-specified connection and reduce the sparsity of the LP matrix.

Notice that in the constraint equations the set of Technologies is indexed as **&#39;t&#39;** , the one of Fuels as **&#39;f&#39;**. The user-specified connections between them are defined through the parameters **InputActivityRatio** and **OutputActivityRatio** in the datafiles of the case studies. Find more information about these parameters in the [user manual](http://users.osemosys.org/uploads/1/8/5/0/18504136/new-website_osemosys_manual_-_working_with_text_files_-_2015-11-05.pdf).

**4) Write Change Log -** Write a Change Log for your code modification. The Change Log must be written as a .doc/.docx file. It must be formatted in the same way as the [Change Log](http://users.osemosys.org/uploads/1/8/5/0/18504136/change_log_2016_08_01.pdf) available on OSeMOSYS website and contain the following information:

- Name of the new version of the code;
- Name of the author(s);
- Concise description of the main changes with respect to the older version;
- Code formulation of the previous and the new equations, highlighting in both, in bold characters, what has been changed.

**5) Write readme file.** This must include:

  1. instructions on how the new code works (including description in English and algebraic formulation) and how to use it;
  2. the times needed to generate the LP matrix and to solve the optimisation;
  3. the original and pre-solved LP matrix dimension (rows, columns and number of non-zeros);
  4. the RAM and the processor specifications of the computer used;

## Datasets

The following documents are necessary to complete the challenge:

- **Osemosys\_modelfile.txt:** The code of OSeMOSYS (in GNU MathProg language);
- **Country\_casestudy.txt:** The datafile of the country case study which collects all the numerical inputs to run the simulations. Your results shall be evaluated on this case study. Please submit your solution using this case study;
- **Utopia.txt:** A test case study based on an imaginary country, Utopia. You may use this case study to perform quick tests (runs in few seconds). Do not submit your submission using this case study.

Download the datasets from the KTH GitHub repository [**here**](https://github.com/KTH-dESA/OSeMOSYS/tree/master/OSeMOSYS-matrix-reduction).

## Deliverables

The solutions should be submitted through Unite Ideas platform (&quot;Propose a Solution&quot; at the bottom of the [#SE4All Unite Ideas challenge page](http://ow.ly/N00z305HNej)). Participants should deliver their solution as a link to their github repository.

**Participants&#39; workspace should include:**

1) The OSeMOSYS new code written in GNU MathProg, named osemosys\__dateofsubmission_;

2) The Change Log in the same format as specified in section &#39;Task&#39; above, reporting changes with respect to the model osemosys\_temba;

3) The results\_countrycasestudy.txt and SelectedResults.csv files of the results of the simulations using the new code and country\_casestudy.txt;

4) The readme file.



**Good luck!**
