# Ledger Safe Restore

## Collect required number of shares, e.g. Share2 and Share3

### Share2 
```
  Header
    secret_owner: "Maugli",
    secret_checksum: "5df397e0",
    creation_date: "20251025T2212",
    total_shares: 3,
    treshold: 2

  Encrypted_passphrase:  
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

  Encrypted_passphrase:  
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

## Optional: burn secure OS image on DVD (e.g. Tails)

Burning Tails on a DVD, see at https://tails.net/install/dvd/index.en.html

## Boot Tails from DVD

## Compute OTP from SLIP39 shares

see at https://iancoleman.io/slip39/

```
Combine 
  Shares
  
predator away beard leader dining float olympic pulse timber ambition wrote ranked source ceiling square impact smell fiscal pecan avoid sunlight twin easy finger withdraw lilac terminal purchase unwrap lungs bulge prepare iris headset ounce elevator example thorn omit observe security revenue duke punish example tofu vintage tactics artwork meaning sister class jury identify building emerald group tenant video force ordinary hand galaxy numerous surface taste making flip rapids hairy flea cylinder slap salon building that pajamas weapon envy fatal gasoline smith spit agency

predator away ceramic leader category cover evening device escape weapon blanket greatest syndrome orbit hairy bulb leader scroll academic presence adequate quarter terminal course playoff slap amount dress guitar trouble briefing declare campus coding ting visitor wildlife dough scramble brother dress cards literary home window mother dramatic cubic leaf scandal desktop radar clay ranked merit justice purchase package health impulse timely should sweater bishop fact deadline gums scared shelter penalty desert desktop friendly blanket mixed juice scared aviation shrimp acne both destroy check negative

Master Secret
59843046e83c15d8da13db0b6c35296baa92a8043434d88e435d0e58c699bfb726084050b79b8a17f466326e485b848b48675356a2d38bb05d20f0132ba1fdff52f4a861546d59013e527f301ccbf9044ad7618038437ff65615b3df4636aad5
```

## Generate SHA256 of OTP
```
otp=59843046e83c15d8da13db0b6c35296baa92a8043434d88e435d0e58c699bfb726084050b79b8a17f466326e485b848b48675356a2d38bb05d20f0132ba1fdff52f4a861546d59013e527f301ccbf9044ad7618038437ff65615b3df4636aad5
echo -n $otp | sha256sum
5df397e0fdfc5707acc7d63f22a5609cdf01eb5995944bc5f4e07afc9dc09758  -
```

## Compare first 8 chars with share checksum

If different: FATAL ERROR, passphrase cannot be recovered

## Write down the Master Secret on a piece of paper
```
OTP1:	59843046 
OTP2:	e83c15d8
OTP3:	da13db0b
OTP4:	6c35296b 
OTP5:	aa92a804
OTP6:	3434d88e
OTP7:	435d0e58
OTP8:	c699bfb7 
OTP9:	26084050
OTP10:	b79b8a17
OTP11:	f466326e 
OTP12:	485b848b 
OTP13:	48675356 
OTP14:	a2d38bb0 
OTP15:	5d20f013 
OTP16:	2ba1fdff 
OTP17:	52f4a861 
OTP18:	546d5901 
OTP19:	3e527f30 
OTP20:	1ccbf904 
OTP21:	4ad76180 
OTP22:	38437ff6 
OTP23:	5615b3df 
OTP24:	4636aad5
```

## Switch off the computer

The following computations MUST be done manually, on a piece of paper,
using the xor_table.txt and ascii_hex_table.txt and word4_word_table.txt
Print the tables and use them independently from a computer.

```
Passphrase
    enc(word1):		29 eb 55 2b
	OTP1:			59 84 30 46
	word1:			70 6f 65 6d => poem
	
    enc(word2):		9b 49 67 a8
	OTP2:			e8 3c 15 d8
	word2:			73 75 72 70 => surp => surprise
	
    enc(word3):		a8 76 aa 7e
	OTP3:			da 13 db 0b
	word3:			72 65 71 75 => requ => require
    
	enc(word4):		03 45 40 05
	OTP4:			6c 35 29 6b
	word4:			6f 70 69 6e => opin => opinion
	
    enc(word5):		d8 f7 c6 70
	OTP5:			aa 92 a8 04
	word5:			72 65 6e 74 => rent
	
    enc(word6):		41 5a bb e2
	OTP6:			34 34 d8 8e
	word6:			75 6e 63 6c => uncl => uncle
	
    enc(word7):		27 2a 6f 2a	
	OTP7:			43 5d 0e 58
	word7:			64 77 61 72 => dwar => dwarf
	
    enc(word8):		ab f8 d2 da
	OTP8:			c6 99 bf b7
    word8:			6d 61 6d 6d => mamm => mammal
	
    enc(word9):		43 78 29 23
	OTP9:			26 08 40 50
	word9:			65 70 69 73 => epis => episode
	
    enc(word10):	d1 f7 eb 7a
	OTP10:			b7 9b 8a 17
	word10:			66 6c 61 6d => flam => flame
	
    enc(word11):	96 13 5b 02
	OTP11:			f4 66 32 6e
	word11:			62 75 69 6c => buil => build
	
    enc(word12):	20 3a e9 e6
	OTP12:			48 5b 84 8b
    word12:			68 61 6d 6d => hamm => hammer
	
    enc(word13):	25 06 27 33
	OTP13:			48 67 53 56
	word13:			6d 61 74 65 => mate => material
	
    enc(word14):	d6 a4 e2 d3
	OTP14:			a2 d3 8b b0
	word14:			74 77 69 63 => twic => twice
	
    enc(word15):	2f 55 82 72
	OTP15:			5d 20 f0 13
	word15:			72 75 72 61 => rura => rural
	
    enc(word16):	4f ce 91 93
	OTP16:			2b a1 fd ff
	word16:			64 6f 6c 6c => doll
	
    enc(word17):	20 9d de 00
	OTP17:			52 f4 a8 61 
	word17:			72 69 76 61 => riva => rival
	
    enc(word18):	27 18 3e 66
	OTP18:			54 6d 59 01
	word18:			73 75 67 67 => sugg => suggest
	
    enc(word19):	4d 3b 1c 5b
	OTP19:			3e 52 7f 30
    word19:			73 69 63 6b => sick
	
    enc(word20):	78 b2 97 65
	OTP20:			1c cb f9 04
	word20:			64 79 6e 61 => dyna => dynamic
	
    enc(word21):	3a b8 11 f5
	OTP21:			4a d7 61 80
	word21:			70 6f 70 75 => popu => popular
	
    enc(word22):	5b 2f 16 98
	OTP22:			38 43 7f f6
	word22:			63 6c 69 6e => clin => clinic
	
    enc(word23):	38 74 c3 b4
	OTP23:			56 15 b3 df
	word23:			6e 61 70 6c => napk => napkin
	
    enc(word24):	35 42 d3 b9
	OTP24:			46 36 aa d5
	word24:			73 74 79 6c => styl => style
```

## Write down Ledger master passhprase on a Recovery Sheet
```
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

# Recover Ledger 
From the Recovery Sheet, enter Master Passhprase to a Ledger HW wallet.

Verify the generated addresses and account balances.

## Tidying up

Ddestroy (for example, burn) all papers used for manual work, including Recovery Sheet, if it was a 
"Ledger Safe Backup" check operation.

Keep the Recovery Sheet, if it was a "Ledger Restore from Shares" operation.
And consider
- generating a new secret on another Ledger, 
- moving account balances to new addresses, 
- starting a Ledger Secure Backup for new secret.