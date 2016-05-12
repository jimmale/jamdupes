# jamdupes

###Introduction
jamdupes is a tool for finding duplicate files, inspired by [fdupes](https://github.com/adrianlopezroche/fdupes),
with added features and speed improvements.

###Speed improvements?
Yes. Speed improvements. On my Raspberry Pi with USB hard drives, I observed the following:
```bash
$ time fdupes -R -S -n ~/files/ > /dev/null

real    2557m7.013s
user    1413m21.272s
sys     355m14.684s

$ time jamdupes -R -S -n ~/files/ > /dev/null

real    330m23.645s
user    133m30.824s
sys     37m45.276s
```

It took 5.5 hours instead of 42.6 hours. That's a 87% reduction!

###Okay, but how?
1. Sort files into buckets based on their size. The OS can calculate the size of files quickly, or maybe the data might be in RAM already!
2. Since any file that is unique in its filesize is clearly not a duplicate, you can safely ignore it and not hash it.
3. For really big files, hash the first few megabytes. Only hash the whole file if the first few megabytes match. 
This reflects the reality that headers and metadata are often at the beginning of a file. (Except for ZIP archives)


###Added features?
Coming soon. See Issue tracker. 


###Prerequisites
python 3 (tested on Python 3.4.2 on armhf Linux and Python 3.5.1 on Darwin x86_64)


###Licence
BSD-3
