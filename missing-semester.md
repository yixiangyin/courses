# Data wrangling
[video](https://www.youtube.com/watch?time_continue=17&v=sz_dsktIjt4&feature=emb_logo) 

## sed - a stream editor 
> Terrible programming langauage except for replacement  
s/a/b/: substitue a with b
\* is 0 or more
\+ is 1 or more
? means zeor or 1
. is any char
[] : range
| : choice
g suffix: globally, the default is once
^ match from the start of the line
$ match the end of the line
() indicate capture graph
* refer to them by \[number of capture group] (start by 1)
## mis
* regex is greedy. Suffix with ? makes it non-greedy
* with -E option to use modern syntax
* match per line

## other tools
 - sort 
 - uniq -c
 - wc -l -> count line
 - awk '{print $2}'
     - column processor
- paste -sd,
- bc - calculator
```timestamp 
 34:41
 ```
- R - programming language
- gnuplot
- xargs
- ffmpeg
- convert - image manipulation program
- feh - image viewer

## exercise
1. [x] 
2. [x] 
- Find the number of words (in /usr/share/dict/words) that contain at least three `a`s and don’t have a `'s` ending. (assume case insensitivity)
Command:   
`cat /usr/share/dict/words | grep -v "'s" | awk '$1 ~ /^.*(a|A).*(a|A).*(a|A).*$/' | sed -E 's/^.*(..)$/\1/I' | wc -l  
`
Answer: 7596  
- What are the three most common last two letters of those words? 
Command:  

`cat /usr/share/dict/words | tr "[:upper:]" "[:lower:]"| grep -v "'s$" | awk '$1 ~ /^.*(a).*(a).*(a).*$/' | sed -E 's/^.*(..)$/\1/' | sort | uniq -c | sort -nk1,1 | tail -n3`
Answer:   

| last two letters | frequency |
| ---------------- | --------- |
| al               | 1039      |
| ia               | 814       |
| an               | 763       |

- How many of those two-letter combinations are there?
Command: `cat /usr/share/dict/words | tr "[:upper:]" "[:lower:]"| grep -v "'s$" | awk '$1 ~ /^.*(a).*(a).*(a).*$/' | sed -E 's/^.*(..)$/\1/' | sort | uniq | wc -l`  
Answer: 156   
- And for a challenge: which combinations do not occur?
`26*26-156 = 520`  
We expect 520 combinations do not occur.
```
#!/bin/bash
for i in {a..z};do
 for j in {a..z};do
    echo  "$i$j"
 done
done
```
`./all.sh > all.txt`  
`cat /usr/share/dict/words | tr "[:upper:]" "[:lower:]"| grep -v "'s$" | awk '$1 ~ /^.*(a).*(a).*(a).*$/' | sed -E 's/^.*(..)$/\1/' | sort | uniq > occurance.txt`   
`diff --minimal <(cat occurance.txt) <(cat all.txt) | grep -E "^>.*" | wc -l`    

3. [ ] 
4. [ ] 
## log 
- [x] lecture

