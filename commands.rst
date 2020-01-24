
.. _commands:

Commands
========

.. toctree::
   :hidden:


Major Commnads
--------------

Usage:  python RNASeqPIPE.py <command> <arguments>

.. code-block:: none

    Command                      Description   
    
    prepareProject               Creates a project folder for storing the analysis results  
    rawReadsQC                   Raw Reads Quality Assessment using FASTQC tool  
    preProcessSamples            Process Raw Reads using BBDUK
    
    denovoTransAssemble          Denovo Assembly of Prokaryotic and Eukaryotic Transcripts
    quantifyAssembledTranscripts Quantify denovo assembled transcripts using Salmon 
    clusterContigs               Clustred Assembled transcripts based on equivalence class
    denovoDEA                    denovo transcriptome assembly based differential expression analysis
    
    mapReadsToGenome             Map RNASeq reads to the genome (organismName.fna) of the organism
    genomeGuidedTransAssembly    Genome Guided Transcript Assembly using Trinity 
    mapReadToGGTansript          Map RNASeq reads to the assembled transcriptome using genome-guided approach
    clusterGGTranscripts         Clustred assembled transcripts using genome-guided approach
    genomeGuidedDEA              Genome guided transcriptome differential expression analysis

    quantifyTranscripts          Quantify transcripts using salmon (or) kallisto
    transcriptomeBasedDEA        Transcriptome based differential expression analysis

    mapReads                     Align cleaned RNASeqs reads to genome fasta (.fna) file
    generateCounts               Generates gene counts from .bam files using featureCount tool
    genomeBasedDEA               Genome alignment based differential expression analysis



Prepare project
---------------

.. code-block:: none

    python RNASeqPIPE.py prepareProject <arguments>

    arguments               type      description

    --projectName           string    Name of the project used for storing the analysis
                                      results. Name should not contain any spaces or special
                                      characters. 
                                      Example: MyProject

    --sampleMetadataFile    string    Tab deleminated file which contains the name
                                      of the biological condition associated with each
                                      sample.

                                      Example: halomicronema_target.txt

                                      lable                 samples               conditions
                                      hexcentricum_s1_rep1  hexcentricum_s1_rep1  Control 
                                      hexcentricum_s1_rep2  hexcentricum_s1_rep2  Control
                                      hexcentricum_s2_rep1  hexcentricum_s2_rep1  Treated
                                      hexcentricum_s2_rep2  hexcentricum_s2_rep2  Treated 

    --sampleHeader          string    Header name of the sample-name column of sampleMetadataFile
                                      Example: samples

    --groupHeader           string    Header name of the sample-group column of sampleMetadataFile 

    --refCondName           string    Name of the reference condition of sampleMetadataFile
                                      Example: Control


Raw samples quality assessment
------------------------------

.. code-block:: none

    python RNASeqPIPE.py rawReadsQC <arguments>
    
    arguments               type      description
      
    --projectName           string    Name of the project used for storing the analysis
                                      results. Name should not contain any spaces or special
                                      characters. 
                                      Example: MyProject

    --readType              string    Sequencing read type
                                      Example: single or paired



Raw samples quality control
------------------------------

.. code-block:: none                                      

    python RNASeqPIPE.py preProcessSamples <arguments>
    
    arguments               type      description
      
    --projectName           string    Name of the project used for storing the analysis
                                      results. Name should not contain any spaces or special
                                      characters. 
                                      Example: MyProject

    --readType              string    Sequencing read type
                                      Example: single or paired

    --bbduk-Xms             int       Initial Java heap size in GB 
                                      Example: 10

    --bbduk-Xmx             int       Maximum Java heap size in GB
                                      Example: 40

    --bbduk-cpu             int       Number of threads to be used
                                      Example: 12

    --bbduk-kmer            int       Kmer length used for finding contaminants
                                      Examle: 13                                  

    --bbduk-minL            int       Minimum read length after trimming
                                      Example: 50

    --bbduk-trimF           int       Number of bases to be trimmed from the front of the read
                                      Example: 5

    --bbduk-trimT           int       Number of bases to be trimmed from the end of the read
                                      Example: 5

    --bbduk-minAQ           int       Minimum average quality of reads
                                      Reads with average quality (after trimming) below 
                                      this will be discarded
                                      Example: 15

    --bbduk-minGC           float     Minimum GC content threshold
                                      Discard reads with GC content below minGC
                                      Example: 0.1 

    --bbduk-maxGC           float     Maximum GC content  threshold
                                      Discard reads with GC content below minGC
                                      Example: 0.99 








