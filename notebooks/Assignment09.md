# Assignment09 

# Continuing CoV analysis

1. Copy individual lines of code needed from 1-sequence-stats.md

2. Add a vector for headers

```julia
using BISC195Bioinformatics
using Statistics
parsedfile = parse_fasta("/Users/anika/Desktop/BISC195/CoV2Analysis/data/cov-sequences.fasta");
headers = parsedfile[1];
sequences = parsedfile[2];
lengths = map(length, sequences);
```

3. Use the minimum() and maximum() functions to find the length of the shortest and longest coronavirus genome in your dataset.

```julia
minimum(lengths)
#29013
maximum(lengths)
#30484
```

4. Do the values make sense, given the mean length?

    Mean length = 29847.432790224033 --> min and max make sense

