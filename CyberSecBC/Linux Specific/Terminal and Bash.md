0 bandit0
1 NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL
2 rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
3 aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
4 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe
5 lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR
6 P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
7 z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
8 TESKZC0XvTetK0S9xNwm25STk5iWrBvP
9 EN632PlfYiZbn3PhVK3XOGSlNInNE00t
10 truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
11 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
12 JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
13 wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
14 ssh key/ fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
15  jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
16 JQttfApK4SeyHwDlI9SXGR50qclOAil1
17 ssh
18 hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg
19 awhqfNnAbc1naukrpqDYcF95h7HoMTrC
20 VxCazJaVykI6W36BkBU0mJTCM8rR95XT
21 NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
22 WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
23 QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
24 VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar
25 p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d
26 c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1
27 YnQpBuifNMas1hcUFk70ZmqkhUU2EuaS
28 AVanL161y9rsbcJIsFHuw35rjaOM19nR
29 tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S
30 xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS
31 OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt
32 rmCBvG56y58BXzv98yZGdO7ATVL5dW8y
33 $0

Day 3

`awk`
	: use on log record containing data points seperated consistently by commas.
![[Pasted image 20220912223401.png]]
format = -F"delimiter" '{ print values you want printed }'
awk -F " " '{ print $1 $2 }'

^^^^ prints the first two fields of the log file which seperates data points with a space ^^^^

sed
	: data from two sources are not coinciding. When analyzing the case of someone making a successful log in attempt one source says Logged_in and one says access_accepted

we want to change access_accepted to Logged_in

![](en-cache://tokenKey%3D%22AuthToken%3AUser%3A232435070%22+7e69fedd-7821-9d81-e17f-64e93f5e293c+3b48d4345424c221e4c4eda6a57d8559+https://www.evernote.com/shard/s699/res/2a740b88-7087-347a-2c02-f655fbce1ef8)

for the above example we would use sed s/access_accepted/Logged_in/
![[Pasted image 20220912223454.png]]
Intro to shell scripting
	nano file.sh
		Format
			#!/bin/bash
			shell commands
			shell commands
			shell commands
Make executable and run
`chmod +x file.sh`
`./file.sh` 

Passing arguments into scripts
	$1 is the argument indicator in the script
```bash
./file.sh $1 $2 # the $values are denoted in the script and appended to the command on run to use in sequential order.
```
