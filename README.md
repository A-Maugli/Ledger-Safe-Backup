# Ledger-Safe-Backup

Problem:
Ledger HW wallet has a 24-word master passphrase. This passphrase should never be entered 
into a computer, to keep it safe. But at the same time it should be backed up securely.
The backup should be in the form of shares, where m out of n shares is enough for recovery.

## Backup
- Set up a secure computing environment
- Create a One Time Pad (OTP)
- Using SHA256SUM, create checksum for the One Time Pad
- Using SLIP39, convert the One Time Pad into shares
- Write down the One Time Pad, the checksum and the SLIP39 shares on a piece of paper
- Print out auxiliary tables: xor, ascii_hex
- Turn off computer. From now on, work manually.
- Compute encrypted passphrase, by manually computing Ledger Passprase XOR OTP
- Create shares. Every share contains the entire encrypted passphrase, and a SLIP39 share
- Check the correctness of computation by executing a complete restore process
- Store the shares inb safes of relatives/attonies/banks.
See the details at ./doc/ledger_safe_backup_example.txt

## Restore
- Collect the required number of shares
- Set up a secure computing environment
- Using Slip39 combine, compute the OTP from the shares
- Compute SHA256SUM of the OTP, compare with checksum on shares
- Write down OTP on a piece of paper
- Print out aux tables: xor, ascii_hex, word4_word
- Switch off computer. From now on, work manually.
- Compute decrypted passphrase, using the aux tables
- Enter the passphrase into a Ledger HW wallet
- Restore your accounts, check addresses and balances.
See the details at ./doc/ledger_safe_restore_example.txt


	
