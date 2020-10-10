<!--- [![Rawsec's CyberSecurity Inventory](https://inventory.rawsec.ml/img/badges/Rawsec-inventoried-FF5050_flat.svg)](https://inventory.rawsec.ml/) -->
![[Version 2.2](https://github.com/R3nt0n)](http://img.shields.io/badge/version-v2.2-orange.svg)
![[Python 3.8](https://github.com/R3nt0n)](http://img.shields.io/badge/python-3.8-blue.svg)
![[GPL-3.0 License](https://github.com/R3nt0n)](https://img.shields.io/badge/license-GPL%203.0-brightgreen.svg)
![[Date](https://github.com/R3nt0n)](http://img.shields.io/badge/date-06/05/2018-yellow.svg)
![[Last update](https://github.com/R3nt0n)](http://img.shields.io/badge/updated-10/10/2020-purple.svg)



# Bopscrk
Bopscrk (**Before Outset PaSsword CRacKing**) is a tool to generate smart and powerful wordlists.

Included in **<a href="https://blackarch.org/">BlackArch Linux</a>** pentesting distribution and **<a href="https://inventory.rawsec.ml/">Rawsec's Cybersecurity Inventory</a>** since August 2019.  
  
<p align="center"><img src="https://github.com/R3nt0n/bopscrk/blob/master/img/example.gif" /></p>
  

The first idea was inspired by **Cupp** and **Crunch**. We could say that bopscrk is a wordlist generator **situated between them**, taking the best of each one. The challenge was try to apply the Cupp's idea to more generic-situations and amplify the shoot-range of the resultant wordlist, without loosing this custom-wordlist-profiler feature. 
 

## Requirements
+ **Python 3** (the other branch keeps Python 2.7 legacy support)
+ *optional requirements*:
  + To use *lyricpass module*:  
    `pip install lib/lyricpass/requirements.txt`

## Usage
```

  -h, --help         show this help message and exit
  -i, --interactive  interactive mode, the script will ask you about target
  -w                 words to combine comma-separated (non-interactive mode)
  --min              min length for the words to generate (default: 4)
  --max              max length for the words to generate (default: 32)
  -c, --case         enable case transformations
  -l, --leet         enable leet transformations
  -n                 max amount of words to combine each time (default: 2)
  -a , --artists     artists to search song lyrics (comma-separated)
  -x , --exclude     exclude all the words included in other wordlists
                     (several wordlists should be comma-separated)
  -o , --output      output file to save the wordlist (default: tmp.txt)


```
 
## How it works
+ You have to **provide** some **words** which will act as a **base**.
+ The tool will generate **all possible combinations** between them.
+ To generate more combinations, it will add some **common separators** (e.g. "-", "_", "."), **random numbers** and **special chars**.
+ You can enable **leet** and **case transforms** to increase your chances.
+ If you enable **lyricpass mode**, the tool will ask you about **artists** and it will download all his **songs' lyrics**. Each line will be added as a new word. By default, artist names and a word formed by the initial of word on each phrase, will be added too.
+ You can provide **wordlists** that you already tried against the target in order **to exclude** all this words from the resultant wordlist (`-x`).
  
### Tips  
+ Fields can be left **empty**.
+ You **can use accentuation** in your words.
+ In the others field you can write **several words comma-separated**. *Example*: 2C,Flipper.
+ Using the **non-interactive mode**, you should provide years in the long and short way (1970,70) to get the same result than the interactive mode.
+ You have to be careful with **-n** argument. If you set a big value, it could result in **too huge wordlists**. I recommend values between 2 and 5.
+ To provide **several artist names** through command line you should provides it **comma-separated**. *Example*: `-a johndoe,johnsmith`
+ To provide **artist names with spaces** through command line you should provides it **quotes-enclosed**. *Example*: `-a "john doe,john smith"`

### Lyricpass 
This feature is based in a modified version of a [tool](https://github.com/initstring/lyricpass) developed originally by [initstring](https://github.com/initstring/). The changes are made to integrate input and output's tool with bopscrk.

It will retrieve all lyrics from all songs which belongs to artists that you provide. As this feature can make the wordlist grow too much, **by default it will store each phrase reduced to its initials** (which will be transformed later if you have activated leet and case transforms). As one of the main methods to use lyrics as a password is to take just initials, It should be usually enough.


### Advanced usage

#### Custom transforms using cfg file
[...] Coming soon [...]

#### Weighted-words system
[...] Coming soon [...]

## Changelist
+ `2.2 version notes (10/10/2020)`  
  + The **lyricpass** integration have been **updated to run with last version released by initstring**
  + `--lyrics-all` option removed         
+ `2.1 version notes (11/07/2020)`  
  + Fixing **min and max length bug**  
+ `2.0/1.5 version notes (17/06/2020)`  
  + **PYTHON 3 NOW IS SUPPORTED**: master branch moves to Python 3. Secondary branch keeps Python 2.7 legacy support    
+ `0-1.2(beta) version notes`  
  + **EXCLUDE WORDLISTS**: speed improvement using multithreaded exclusions  
  + **NEW FEATURE**: lyrics searching related to artists increase the wordlist chances


## TO-DO list
  + Implement **weighted-words system**.
  + Allow to create **advanced custom transforms** trough a **configuration file**.
+ **Lyricpass** integration was upgraded to last version released by initstring, but still needs some tweaks to speed up the search process (I would appreciate any help).


## Legal disclaimer
This tool is created for the sole purpose of security awareness and education, it should not be used against systems that you do not have permission to test/attack. The author is not responsible for misuse or for any damage that you may cause. You agree that you use this software at your own risk.
