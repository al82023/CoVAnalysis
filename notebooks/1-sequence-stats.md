# Mean and Standard Deviation of Lengths and GC Content of Coronavirus Genomes

## I downloaded coronavirus genomes from NCBI (see `data/data.md` for more details).

## I specified that I am using the `BISCBioinformatics` and `Statistics` packages, as those are both used in the analysis.

```julia
using BISC195Bioinformatics
using Statistics
```

## I copied the `meanandstdoflengthandgc` function (from Assignment 6).

This function takes a path to a file as an argument and returns the mean and standard deviation of the lengths and gc content of the sequences in the given file.

The function executes the following:

1. parse the file, assigning the result to `parsedfile`

2. assign the array of sequences returned to `sequences`

3. calculate the length of each sequence by mapping the `length` function onto each element of `sequences`, assigning the result to `lengths`

4. calculate the mean and standard deviation of `lengths`, assigning the results to `meanlength` and `stdlength` respectively

5. calculate the gc content of each sequence by mapping the `gc_content` function onto each element of `sequences`, assigning the result to `gc`

6. calculate the mean and standard deviation of `gc`, assigning the results to `meangc` and `stdgc` respectively

7. return a Tuple consisting of `meanlength`, `stdlength`, `meangc`, and `stdgc`

```julia
function meanandstdoflengthandgc(path)
    parsedfile = parse_fasta(path)
    sequences = parsedfile[2]
    lengths = map(length, sequences)
    meanlength = mean(lengths)
    stdlength = std(lengths)
    gc = map(gc_content, sequences)
    meangc = mean(gc)
    stdgc = std(gc)
    return (meanlength, stdlength, meangc, stdgc)
end
```

## I tested the functions used in `meanandstdoflengthandgc` to confirm there functionality.

The only functions used in `meanandstdoflengthandgc` that are not in the Base or Statistics are `parse_fasta` and `gc_content`.

`gc_content` that works on `LongDNASeq` like in this function is defined in `BioSequences` which is used in `BISC195Bioinformatics`, and thus is also already tested.

`parse_fasta` was tested successfully in Assignment 6.

## I executed the `meanandstdoflengthandgc` function on the file of coronavirus genomes.

```julia
meanandstdoflengthandgc("/Users/anika/Desktop/BISC195/CoV2Analysis/data/cov-sequences.fasta")
#(29847.432790224033, 91.60454439709665, 0.38306657229009633, 0.00946565855451385)
```