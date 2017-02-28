# genrandom
A C program to generate random data using several random models, with parameterized non uniformities and flexible output formats.

Usage: genrandom [-bsvh] [-x <bits>] [-y <bits>] [-z <bits>] [-c <generate length>] [-m <|pure(default)|sums|biased|correlated|normal|file>] [-l <left_stepsize>] [-r <right_stepsize>] [--stepnoise=<noise on step>] [--bias=<bias>] [--correlation=<correlation>] [--mean=<normal mean>] [--variance=<normal variance>] [-o <output_filename>] [-j <j filename>] [-i <input filename>] [-f <hex|binary|01>] [-k <1K_Blocks>] [-w [8|16|32|64|128]]

Generate random bits with configurable non-uniformities.
  Author: David Johnston, dj@deadhat.com

  -m, --model=<pure(default)|sums|biased|correlated|lcg||normal|file>   Select random source model

Step Update Metastable Source model (-m sums) Options

  -l, --left=<left_stepsize>     stepsize when moving left as a fraction of sigma_m.
  -r, --right=<right_stepsize>   stepsize when moving right as a fraction of sigma_m.
  --stepnoise=<noise on step>    variance of the noise on stepsize. e.g. 0.00001.

Biased model (-m biased) Options

  --bias=<bias>                  bias as a number between 0.0 and 1.0. Only for biased model

Correlated model (-m correlated) Options

  --correlation=<correlation>    correlation with previous bit as a number between -1.0 and 1.0. Only for correlation model

Normal model (-m normal) Options

  --mean=<normal mean>           mean of the normally distributed data. Only for normal model
  --variance=<normal variance>   variance of the normally distributed data

Linear Congruential Generator model (-m lcg) Options

  --lgc_a=<LCG multipler term>  Positive integer less than lcg_m
  --lgc_c=<LCG additive term>   Positive integer less than lcg_m
  --lgc_m=<LCG modulo term>     Positive integer defining size of the group
  --lgc_truncate=<lower bits to truncate>     Positive integer
  --lgc_outbits=<Number of bits per output>     Positive integer

General Options

  -x, --xor=<bits>               XOR 'bits' of entropy together for each output bit
  -y, --xmin=<bits>              Provides the start of a range of XOR ratios to be chosen at random per sample
  -z, --xmax=<bits>              Provides the end of a range of XOR ratios to be chosen at random per sample
  -s, --seed                     seed the internal RNG with /dev/random
  -c, --cmax=<generate length>   number of PRNG generates before a reseed
  -v, --verbose                  output the parameters

File Options

  -o <output_filename>           output file
  -j, --jfile=<j filename>       filename to push source model internal state to
  -i, --infile=<input filename>       filename of entropy file for file model
  -f, --informat=<hex|binary|01>       Format of input file. hex=Ascii hex(default), 4 bit per hex character. binary=raw binary. 01=ascii binary. Non valid characters are ignored
  -k, --blocks=<1K_Blocks>       size of output in kilobytes

Output Format Options

  -b, --binary                   output in raw binary format
  -w, --width=[1...256]       Byte per line of output

The most important option of all

  -h, --help                     print this help and exit


