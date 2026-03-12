# tFAW - Four Activate Window

### Definition
* A rolling time window in which no more than **four ACT commands** may occur.

### Question it answers
* How many row activations can happen within a short interval?

### Why it exists physically
* Even if each ACT individually obeys **tRRD**, too many ACTs clustered together still create excessive current demand.
* tFAW limits the total density of recent activations.

### Importance
* It protects against **activation clustering**.

### Violation meaning (DV/Debug)
* If a fifth ACT falls inside the same rolling window, activation rate is too aggressive.

### Quick picture
```text
ACT1   ACT2   ACT3   ACT4        ACT5
|------------- tFAW ------------|
ACT5 must not make 5 ACTs inside this window
```

### Related notes
* [[ACT opens a row into the row buffer|ACT]]
* [[DDR-Timing-tRRD|tRRD]]
* [[DDR - DRAM array hierarchy|Bank]]
