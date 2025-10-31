# Ledger-Safe-Backup - POC

Problem:
Ledger HW wallet has a 24-word master passphrase. This passphrase should never be entered 
into a computer, to keep it safe. But at the same time, it should be backed up securely.
The backup should be in the form of shares, where m out of n shares is sufficient for recovery.

## Backup
- Set up a secure computing environment.
- Create a one-time pad (OTP).
- Create a checksum for the OTP.
- Using SLIP39, convert the OTP into shares.
- Write down the OTP, the checksum and the SLIP39 shares on a piece of paper.
- Print out auxiliary tables: xor_table.txt, ascii_hex.txt
- Turn off computer. From now on, work manually.
- Compute the encrypted passphrase, by manually XORing Ledger Passphrase with the OTP.
- Create shares. Every share contains the entire encrypted passphrase and a SLIP39 share.
- Verify the correctness of computation by performing a complete restore process.
- Store the shares in safes of relatives/attorneys/banks.

See the details at ./doc/ledger_safe_backup_example.txt

## Restore
- Collect the required number of shares.
- Set up a secure computing environment.
- Using SLIP39 combine, compute the OTP from the shares.
- Compute the checksum of the OTP and compare it with checksum on shares.
- Write down the OTP on a piece of paper.
- Print out aux tables: xor_table.txt, ascii_hex.txt, and bip-39/english.txt
- Turn off the computer. From now on, work manually.
- Compute the decrypted passphrase using the auxiliary tables.
- Enter the passphrase into a Ledger HW wallet.
- Restore your accounts and verify addresses and balances.

See the details at ./doc/ledger_safe_restore_example.txt

