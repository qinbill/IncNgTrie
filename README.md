# IncNgTrie

This is the source code repository for our paper published in VLDB 2014.

## Paper Title: Efficient Error-tolerant Query Autocompletion

## Authors: Chuan Xiao, Jianbin Qin, Wei Wang, Yoshiharu Ishikawa, Koji Tsuda, Kunihiko Sadakane

## Abstract

Query autocompletion is an important feature saving users many keystrokes from typing the entire query. In this paper we study the problem of query autocompletion that tolerates errors in users' input using edit distance constraints. Previous approaches index data strings in a trie, and continuously maintain all the prefixes of data strings whose edit distance from the query are within the threshold. The major inherent problem is that the number of such prefixes is huge for the first few characters of the query and is exponential in the alphabet size. This results in slow query response even if the entire query approximately matches only few prefixes.

In this paper, we propose a novel neighborhood generationbased algorithm, IncNGTrie, which can achieve up to two orders of magnitude speedup over existing methods for the error-tolerant query autocompletion problem. Our proposed algorithm only maintains a small set of active nodes, thus saving both space and time to process the query. We also study efficient duplicate removal which is a core problem in fetching query answers. In addition, we propose optimization techniques to reduce our index size, as well as discussions on several extensions to our method. The efficiency of our method is demonstrated against existing methods through extensive experiments on real datasets.


## Citation:
```
@article{DBLP:journals/pvldb/XiaoQ0ITS13,
  author    = {Chuan Xiao and
               Jianbin Qin and
	       Wei Wang and
	       Yoshiharu Ishikawa and
	       Koji Tsuda and
	       Kunihiko Sadakane},
  title     = {Efficient Error-tolerant Query Autocompletion},
  journal   = {{PVLDB}},
  volume    = {6},
  number    = {6},
  pages     = {373--384},
  year      = {2013},
  url       = {http://www.vldb.org/pvldb/vol6/p373-xiao.pdf},
  timestamp = {Wed, 04 Sep 2013 08:33:42 +0200},
  biburl    = {http://dblp.org/rec/bib/journals/pvldb/XiaoQ0ITS13},
  bibsource = {dblp computer science bibliography, http://dblp.org}
  	}
```

## Usage:

This source code has been tested and compiled on a Ubuntu 16.4LTS OS. It requires to install libssl and libcrypto. Please install it through: 
```
~$ sudo apt-get install openssl libssl-dev
```

Then run:
```
make
```

Only one binary will generate: searcher
```
$ ./searcher 
Need input file name
usage: -t <Max Edit Distance>
       -a <Algorithm,  fastss default >
          fastss is using fastss algorithm 
       -d <Data File>
       -c <Trie Type, MapTrie Default>
          map    is using MapTrie 
          vec    is using VectorTrie 
          bro    is using BrotherTrie 
       -p print active nodes
       -k process query by one.
       -s stupid fatching.
       -i interactive mode
       -f no result fetch at end.
       -s fetch results one character by one
Version: 0.0.1.0_PROD
```

To run the test, you need query file and data file. both file are text files that contains strings per line. the current version is not optimized for strings too long. For best performance, please keep the string length within 15 characters. 

A simple example:
```
$ ./searcher -t 3 -a fastss -d data_file.txt -c map < inputfile.txt

```



