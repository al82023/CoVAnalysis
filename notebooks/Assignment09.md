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

## Identifying outliers

1. Use the Plots package to create a histogram of your coronavirus genome lengths.

2. Remove the legend and add more descriptive axis labels to this plot

```julia
using Plots
histogram(lengths, legend = false, xaxis = "Genome Lengths", yaxis = "Frequency")
```

3. Filter sequences to remove any that have a length of less than 25k bases

    Find the index of all the sequences that are less than 25K bases long, then remove the items at those indices from the sequence vector and the headers vector and the lengths vector.

```julia
lessthan25k = findall(x->x<25000, lengths);
deleteat!(headers, lessthan25k);
deleteat!(sequences, lessthan25k);
deleteat!(lengths, lessthan25k);
```

4. Ensure that min of the sequence length is actually > 25k bases and that sequence and header vectors have the same length

```julia
minimum(lengths)
#29013
@assert length(headers) == length(sequences)
```

## Plot the result

1. Create a new histogram that shows the distribution of filtered sequences, using the same methods as above

```julia
histogram(lengths, legend = false, xaxis = "Genome Lengths", yaxis = "Frequency")
```