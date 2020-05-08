# <ins>RNA-Seq Quantification Using the EM-Aglorithm </ins>


> Implements the Full-EM algorithm for transcript quantification from RNA-aligments
> Takes in a transcript/alignment file (formatted properly below) and returns estimated
> read-counts for each transcript in the transcriptome.

### Dependencies
* [Python 3.7](https://www.python.org/downloads/)
* [Numpy](http://www.numpy.org/)
* [Numba](https://pypi.org/project/numba/) (Speed-up expensive EM-Steps)
* [SciPy](https://www.scipy.org/)

### <ins>Execution</ins>
```
$ cd data/ 
$ ./squant.py squant --in <input-file> --out <output-file>
```

### <ins>Input Data Format</ins>
```
number_of_transcripts:int
<transcript_record_1>
<transcript_record_2>
...
<transcript_record_m>
<alignment_block_for_read_1>
<alignment_block_for_read_2>
...
<alignment_block_for_read_n>
```

##### where a transcript record is of the form
```
transcript_name:string <tab> transcript_length:int
```
##### and an alignment block is of the form
```
number_of_alignments_for_read:int
aln1_txp:string <tab> aln1_ori:string <tab> aln1_pos:int <tab> aln1_alignment_prob:double
aln2_txp:string <tab> aln2_ori:string <tab> aln2_pos:int <tab> aln2_alignment_prob:double
...
alnk_txp:string <tab> alnk_ori:string <tab> alnk_pos:int <tab> alnk_alignment_prob:double
```

### <ins>Structure</ins>
    EM
    ├── LICENSE
    ├── report.pdf                     (write-up of results, difficulties, and design)
    ├── README                   
    └── data
        ├── squant.py                   (reads user inputs)
        ├── EM.py                       (algorithm in use)
        ├── alignments.small.cmsc423    (sample input)
        ├── true_counts_small.tsv       (true-counts of sample input)
        └── quants.tsv                  (sample output)

#### <ins> Future Goals </ins>
* Improve storage of effective length computations
* More accurate convergence values to reflect more accurate read-estimations (within 10<sup>-4</sup>)