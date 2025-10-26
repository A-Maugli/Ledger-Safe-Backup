# Ledger Safe Backup - example

## Write a DVD with the image of a safe OS.
E.g. for Tails, see instructions here: 
https://tails.net/install/index.en.html

Burning Tails on a DVD,
https://tails.net/install/dvd/index.en.html

## Boot Tails from DVD

## Open a terminal window, generate OTP
```
otp=`openssl rand -hex 96`
echo $otp
59843046e83c15d8da13db0b6c35296baa92a8043434d88e435d0e58c699bfb726084050b79b8a17f466326e485b848b48675356a2d38bb05d20f0132ba1fdff52f4a861546d59013e527f301ccbf9044ad7618038437ff65615b3df4636aad5

# Generate SHA256 of OTP 
echo -n $otp | sha256sum
5df397e0fdfc5707acc7d63f22a5609cdf01eb5995944bc5f4e07afc9dc09758  -

# Generate SLIP39 words
See at https://iancoleman.io/slip39/

Master secret
59843046e83c15d8da13db0b6c35296baa92a8043434d88e435d0e58c699bfb726084050b79b8a17f466326e485b848b48675356a2d38bb05d20f0132ba1fdff52f4a861546d59013e527f301ccbf9044ad7618038437ff65615b3df4636aad5

Total shares 3

Threshold 2

Shares
predator away acrobat leader alpha iris society density large prisoner likely angel prayer evidence eclipse sidewalk island club busy genuine species credit alarm beard decorate eraser rescue diploma hesitate garbage drift enlarge modify photo rapids snapshot theory flip include making presence swimming husky mother system shaft exclude medical machine either guard slow valuable scene email rumor crucial similar legs review estimate aluminum webcam length canyon medical arena quick cards surface flea staff adorn medical ending morning kidney practice umbrella holy smirk evoke human pumps

predator away beard leader dining float olympic pulse timber ambition wrote ranked source ceiling square impact smell fiscal pecan avoid sunlight twin easy finger withdraw lilac terminal purchase unwrap lungs bulge prepare iris headset ounce elevator example thorn omit observe security revenue duke punish example tofu vintage tactics artwork meaning sister class jury identify building emerald group tenant video force ordinary hand galaxy numerous surface taste making flip rapids hairy flea cylinder slap salon building that pajamas weapon envy fatal gasoline smith spit agency

predator away ceramic leader category cover evening device escape weapon blanket greatest syndrome orbit hairy bulb leader scroll academic presence adequate quarter terminal course playoff slap amount dress guitar trouble briefing declare campus coding ting visitor wildlife dough scramble brother dress cards literary home window mother dramatic cubic leaf scandal desktop radar clay ranked merit justice purchase package health impulse timely should sweater bishop fact deadline gums scared shelter penalty desert desktop friendly blanket mixed juice scared aviation shrimp acne both destroy check negative
```

## Write down OTP to a piece of paper:
```
OTP:
59843046 e83c15d8 da13db0b 6c35296b 
aa92a804 3434d88e 435d0e58 c699bfb7 
26084050 b79b8a17 f466326e 485b848b 
48675356 a2d38bb0 5d20f013 2ba1fdff 
52f4a861 546d5901 3e527f30 1ccbf904 
4ad76180 38437ff6 5615b3df 4636aad5

First 8 char of SHA256(OTP), i.e. checksum(OTP):
59843046e

SLIP39 
Total shares 3
Threshold 2

Shares
predator away acrobat leader alpha iris society density large prisoner likely angel prayer evidence eclipse sidewalk island club busy genuine species credit alarm beard decorate eraser rescue diploma hesitate garbage drift enlarge modify photo rapids snapshot theory flip include making presence swimming husky mother system shaft exclude medical machine either guard slow valuable scene email rumor crucial similar legs review estimate aluminum webcam length canyon medical arena quick cards surface flea staff adorn medical ending morning kidney practice umbrella holy smirk evoke human pumps

predator away beard leader dining float olympic pulse timber ambition wrote ranked source ceiling square impact smell fiscal pecan avoid sunlight twin easy finger withdraw lilac terminal purchase unwrap lungs bulge prepare iris headset ounce elevator example thorn omit observe security revenue duke punish example tofu vintage tactics artwork meaning sister class jury identify building emerald group tenant video force ordinary hand galaxy numerous surface taste making flip rapids hairy flea cylinder slap salon building that pajamas weapon envy fatal gasoline smith spit agency

predator away ceramic leader category cover evening device escape weapon blanket greatest syndrome orbit hairy bulb leader scroll academic presence adequate quarter terminal course playoff slap amount dress guitar trouble briefing declare campus coding ting visitor wildlife dough scramble brother dress cards literary home window mother dramatic cubic leaf scandal desktop radar clay ranked merit justice purchase package health impulse timely should sweater bishop fact deadline gums scared shelter penalty desert desktop friendly blanket mixed juice scared aviation shrimp acne both destroy check negative
```

## Switch off computer. The following computations SHOULD BE done manually.
```
E.g.
Ledger passphrase:
word1:	poem 
word2:	surprise
word3:	require
word4:	opinion
word5:	rent 
word6:	uncle 
word7: 	dwarf 
word8: 	mammal 
word9: 	episode 
word10: flame 
word11: build 
word12: hammer 
word13:	material 
word14: twice 
word15:	rural 
word16: doll 
word17: rival 
word18: suggest 
word19:	sick 
word20:	dynamic 
word21:	popular 
word22: clinic 
word23:	napkin 
word24:	style
```

## Prepare for passphrase encryption
```
OTP1: 59843046
OTP2: e83c15d8
OTP3: da13db0b
OTP4: 6c35296b
OTP5: aa92a804 
OTP6: 3434d88e
OTP7: 435d0e58
OTP8: c699bfb7
OTP9: 26084050
OTP10:b79b8a17
OTP11:f466326e
OTP12:485b848b
OTP13:48675356
OTP14:a2d38bb0
OTP15:5d20f013
OTP16:2ba1fdff
OTP17:52f4a861
OTP18:546d5901
OTP19:3e527f30
OTP20:1ccbf904
OTP21:4ad76180
OTP22:38437ff6
OTP23:5615b3df
OTP24:4636aad5
```

## Compute encrypted passphrase MANUALLY, using ascii_hex table and xor table
```
		char	hex
word1:	poem  	70 6f 65 6d
OTP1:			59 84 30 46
enc(word1):		29 eb 55 2b

word2:	surp	73 75 72 70
OTP2:			e8 3c 15 d8
enc(word2):		9b 49 67 a8

word3:	requ	72 65 71 75
OTP3:			da 13 db 0b
enc(word3):		a8 76 aa 7e

word4: 	opin	6f 70 69 6e
OTP4:			6c 35 29 6b
enc(word4):		03 45 40 05

word 5:	rent	72 65 6e 74
OTP5:			aa 92 a8 04 
enc(word5):		d8 f7 c6 70	

word 6:	uncl	75 6e 63 6c
OTP6:			34 34 d8 8e
enc(word6):		41 5a bb e2

word 7: dwar	64 77 61 72
OTP7:			43 5d 0e 58
enc(word7):		27 2a 6f 2a	

word 8: mamm	6d 61 6d 6d
OTP8:			c6 99 bf b7
enc(word8):		ab f8 d2 da

word 9: epis	65 70 69 73
OTP9:			26 08 40 50
enc(word9):		43 78 29 23

word10: flam	66 6c 61 6d
OTP10:			b7 9b 8a 17
enc(word10):	d1 f7 eb 7a

word11: buil	62 75 69 6c
OTP11:			f4 66 32 6e
enc(word11):	96 13 5b 02

word12: hamm	68 61 6d 6d
OTP12:			48 5b 84 8b
enc(word12):	20 3a e9 e6

word13:	mate	6d 61 74 65
OTP13:			48 67 53 56
enc(word13):	25 06 27 33

word14: twic	74 77 69 63
OTP14:			a2 d3 8b b0
enc(word14):	d6 a4 e2 d3

word15:	rura	72 75 72 61
OTP15:			5d 20 f0 13
enc(word15):	2f 55 82 72

word16: doll 	64 6f 6c 6c 
OTP16:			2b a1 fd ff
enc(word16):	4f ce 91 93

word17: riva	72 69 76 61
OTP17:			52 f4 a8 61
enc(word17):	20 9d de 00

word18: sugg	73 75 67 67
OTP18:			54 6d 59 01
enc(word18):	27 18 3e 66

word19:	sick 	73 69 63 6b
OTP19:			3e 52 7f 30
enc(word19):	4d 3b 1c 5b

word20:	dyna	64 79 6e 61
OTP20:			1c cb f9 04
enc(word20):	78 b2 97 65

word21:	popu	70 6f 70 75
OTP21:			4a d7 61 80
enc(word21):	3a b8 11 f5

word22: clin	63 6c 69 6e
OTP22:			38 43 7f f6
enc(word22):	5b 2f 16 98

word23:	napk	6e 61 70 6b
OTP23:			56 15 b3 df
enc(word23):	38 74 c3 b4

word24:	styl	73 74 79 6c
OTP24:			46 36 aa d5
enc(word24):	35 42 d3 b9
```

## Write down shares on a separate piece of paper
### Share1
```
  Header
    secret_owner: "Maugli",
    secret_checksum: "5df397e0",
    creation_date: "20251025T2212",
    total_shares: 3,
    treshold: 2

  Encrypted_passpharse:  
    enc(word1):		29 eb 55 2b
    enc(word2):		9b 49 67 a8
    enc(word3):		a8 76 aa 7e
    enc(word4):		03 45 40 05
    enc(word5):		d8 f7 c6 70
    enc(word6):		41 5a bb e2
    enc(word7):		27 2a 6f 2a	
    enc(word8):		ab f8 d2 da
    enc(word9):		43 78 29 23
    enc(word10):	d1 f7 eb 7a
    enc(word11):	96 13 5b 02
    enc(word12):	20 3a e9 e6
    enc(word13):	25 06 27 33
    enc(word14):	d6 a4 e2 d3
    enc(word15):	2f 55 82 72
    enc(word16):	4f ce 91 93
    enc(word17):	20 9d de 00
    enc(word18):	27 18 3e 66
    enc(word19):	4d 3b 1c 5b
    enc(word20):	78 b2 97 65
    enc(word21):	3a b8 11 f5
    enc(word22):	5b 2f 16 98
    enc(word23):	38 74 c3 b4
    enc(word24):	35 42 d3 b9

  OTP_share:
	seq_no: 1,
	words: predator away acrobat leader alpha iris society density large prisoner likely angel prayer evidence eclipse sidewalk island club busy genuine species credit alarm beard decorate eraser rescue diploma hesitate garbage drift enlarge modify photo rapids snapshot theory flip include making presence swimming husky mother system shaft exclude medical machine either guard slow valuable scene email rumor crucial similar legs review estimate aluminum webcam length canyon medical arena quick cards surface flea staff adorn medical ending morning kidney practice umbrella holy smirk evoke human pumps
```

### Share2 
```
  Header
    secret_owner: "Maugli",
    secret_checksum: "5df397e0",
    creation_date: "20251025T2212",
    total_shares: 3,
    treshold: 2

  Encrypted_passpharse:  
    enc(word1):		29 eb 55 2b
    enc(word2):		9b 49 67 a8
    enc(word3):		a8 76 aa 7e
    enc(word4):		03 45 40 05
    enc(word5):		d8 f7 c6 70
    enc(word6):		41 5a bb e2
    enc(word7):		27 2a 6f 2a	
    enc(word8):		ab f8 d2 da
    enc(word9):		43 78 29 23
    enc(word10):	d1 f7 eb 7a
    enc(word11):	96 13 5b 02
    enc(word12):	20 3a e9 e6
    enc(word13):	25 06 27 33
    enc(word14):	d6 a4 e2 d3
    enc(word15):	2f 55 82 72
    enc(word16):	4f ce 91 93
    enc(word17):	20 9d de 00
    enc(word18):	27 18 3e 66
    enc(word19):	4d 3b 1c 5b
    enc(word20):	78 b2 97 65
    enc(word21):	3a b8 11 f5
    enc(word22):	5b 2f 16 98
    enc(word23):	38 74 c3 b4
    enc(word24):	35 42 d3 b9

  OTP_share:
	seq_no: 2,
	words: predator away beard leader dining float olympic pulse timber ambition wrote ranked source ceiling square impact smell fiscal pecan avoid sunlight twin easy finger withdraw lilac terminal purchase unwrap lungs bulge prepare iris headset ounce elevator example thorn omit observe security revenue duke punish example tofu vintage tactics artwork meaning sister class jury identify building emerald group tenant video force ordinary hand galaxy numerous surface taste making flip rapids hairy flea cylinder slap salon building that pajamas weapon envy fatal gasoline smith spit agency
```
### Share3
```
  Header
    secret_owner: "Maugli",
    secret_checksum: "5df397e0",
    creation_date: "20251025T2212",
    total_shares: 3,
    treshold: 2

  Encrypted_passpharse:  
    enc(word1):		29 eb 55 2b
    enc(word2):		9b 49 67 a8
    enc(word3):		a8 76 aa 7e
    enc(word4):		03 45 40 05
    enc(word5):		d8 f7 c6 70
    enc(word6):		41 5a bb e2
    enc(word7):		27 2a 6f 2a	
    enc(word8):		ab f8 d2 da
    enc(word9):		43 78 29 23
    enc(word10):	d1 f7 eb 7a
    enc(word11):	96 13 5b 02
    enc(word12):	20 3a e9 e6
    enc(word13):	25 06 27 33
    enc(word14):	d6 a4 e2 d3
    enc(word15):	2f 55 82 72
    enc(word16):	4f ce 91 93
    enc(word17):	20 9d de 00
    enc(word18):	27 18 3e 66
    enc(word19):	4d 3b 1c 5b
    enc(word20):	78 b2 97 65
    enc(word21):	3a b8 11 f5
    enc(word22):	5b 2f 16 98
    enc(word23):	38 74 c3 b4
    enc(word24):	35 42 d3 b9

  OTP_share:
	seq_no: 3,
	words: predator away ceramic leader category cover evening device escape weapon blanket greatest syndrome orbit hairy bulb leader scroll academic presence adequate quarter terminal course playoff slap amount dress guitar trouble briefing declare campus coding ting visitor wildlife dough scramble brother dress cards literary home window mother dramatic cubic leaf scandal desktop radar clay ranked merit justice purchase package health impulse timely should sweater bishop fact deadline gums scared shelter penalty desert desktop friendly blanket mixed juice scared aviation shrimp acne both destroy check negative
```

## Execute "Ledger safe restore" procedure, to see that you can restore Ledger master passphrase.

## Store the shares in a safe way before distribution.

## "Burn" every piece of paper used for computation, except the shares.