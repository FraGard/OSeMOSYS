Jonas Hörsch


Table of Contents
─────────────────

1 Explanation
2 Instructions
3 Running times
4 Dimensions
5 RAM/CPU
6 Changelog


1 Explanation
═════════════

  Using a simple pattern of generating parametric sets from the huge
  data-specified connection tensors, one can cut down the model
  generation time considerably. That means one builds a set

    set MODExTECHNOLOGYperFUELout{f in FUEL} within MODE_OF_OPERATION
       cross TECHNOLOGY := {m in MODE_OF_OPERATION, t in TECHNOLOGY :
       exists{r in REGION, y in YEAR} OutputActivityRatio[r,t,f,m,y] <>
       0};

  which holds all mode and technology combinations that are allowed for
  a given fuel by the choices in user-specified
  OutputActivityRatio. Then the often appearing set

  {m in MODE_OF_OPERATION, t in TECHNOLOGY, l in TIMESLICE:
  OutputActivityRatio[r,t,f,m,y] <>0}

  can be directly replaced by

  {(m,t) in MODExTECHNOLOGYperFUELout[f]}

  without any loss of generality but a noticeable speed improvement.

  The same holds for the MODE, TECHNOLOGY and STORAGE, EMISSION
  interplay and the way that TIMESLICEs are assigned to SEASON, DAYTIME
  and DAILYTIMEBRACKET.

  Since there is not a single constraint or variable that depends on the
  sparse FUEL, STORAGE and EMISSION to MODE, TECHNOLOGY combinations
  (sums don't really affect the matrix size), i don't see much hope in
  reducing the matrix size, unless one can also expect a sparse relation
  of the REGION, TECHNOLOGY dimensions.

  Finally by finding all the allowed combinations between TECHNOLOGY and
  MODE_OF_OPERATION, by

  set MODEperTECHNOLOGY{t in TECHNOLOGY} within MODE_OF_OPERATION := {m
      in MODE_OF_OPERATION : (exists {f in FUEL} (m, t) in
      MODExTECHNOLOGYperFUELout[f] union MODExTECHNOLOGYperFUELin[f]) or
      (exists {s in STORAGE} (m, t) in MODExTECHNOLOGYperSTORAGEto[s]
      union MODExTECHNOLOGYperSTORAGEfrom[s]) or (exists {e in EMISSION}
      (m, t) in MODExTECHNOLOGYperEMISSION[e])};

  and replacing all occurrences of MODE_OF_OPERATION with
  MODEperTECHNOLOGY[t], one can save a few more seconds of the matrix
  generation time and reduce the matrix of the optimization problem by a
  tiny bit since the RateOfActivity variable shrinks by approximately a
  third.


2 Instructions
══════════════

  I only changed the model file. So the usage instructions are the ones
  of the original osemosys code.


3 Running times
═══════════════

  Generating the LP matrix takes 44s.  Solution process takes 30
  minutes.


4 Dimensions
════════════

  • original: 324833 rows, 226096 columns, 3382958 non-zeros
  • presolved: 146678 rows, 132575 columns, 2078374 non-zeros


5 RAM/CPU
═════════

  8GB RAM and 4 cores Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz


6 Changelog
═══════════

  I am not providing a Changelog at this stage, since I would rather
  discuss the solution first, improve the set names and discuss whether
  improving the data file would not be a cleaner solution.
