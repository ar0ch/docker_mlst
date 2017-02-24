FROM debian:testing
MAINTAINER ap13@sanger.ac.uk

RUN apt-get update -qq && apt-get install -y git wget samtools bedtools bwa gcc autoconf make python-pip unzip 

RUN pip install stringMLST 

RUN pip install pyfaidx 

RUN cd /stringMLST && \
    stringMLST.py --getMLST --species salmonella-enterica -P /stringMLST/datasets/Salmonella_enterica/SE -k 35 && \
    stringMLST.py --getMLST --species campylobacter-jejuni -P /stringMLST/datasets/Campylobacter_jejuni/CJ -k 35 && \
    stringMLST.py --getMLST --species listeria -P /stringMLST/datasets/Listeria_monocytogenes/LM -k 35 && \
    stringMLST.py --getMLST --species ecoli1 -P /stringMLST/datasets/Escherichia_coli_1/EC -k 35 

WORKDIR /data

#cd /data/stringMLST && ls -rt | grep timing | xargs -L 1 cat  | paste - - - - | awk '{print $2}' | sed 's/s//gi' | sed 's/0m//gi'
