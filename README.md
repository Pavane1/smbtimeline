# smbtimeline
## An automated timeline for SMB Traffic
smbtimeline is a tool to produce a timeline out of SMB traffic. Inspired by the manually work of putting together an investigative timeline from SMB traffic, its purpose is to provide a timeline from a given pcap file. Particularly as Incident Response is about to focus on the right amount of details at the right time, smbtimeline provides an overview about the SMB traffic and not showing every possible bit of information but still enriching packets with useful details. In order to archive this goal, smbtimeline arranges not only SMB commands, but also important commands taken from protocols which utilize SMB as transport medium, in an easy to handle .csv file. 
### Supported RPC/DCE protocols transported by SMB
SAMR, LSAD, SRVS, WKST, WINREG, SCMR, ATSVC

## Usage
Option | Explanation
--- | ---
-f, --file \<PATH\> | Path to pcap file containing traffic to analyze, mandatory parameter
-2, --smb2 | SMB modus: create a timeline for SMB2 and SMB3 traffic, non-mandatory parameter, default active if no parameter for SMB modus is given.
-1, --smb1 | SMB modus: create a timeline for SMB1 traffic, non-mandatory parameter, default not active if no parameter for SMB modus is given.
-p, --protocol \<PATH\> | Path to protocol file, non-mandatory parameter, if not given no protocol will be written.
-e, --extended \<PATH\> | Path to file, non-mandatory parameter, if given a combined timeline in log2timeline format
-s, --strip | strip traffic and create a new pcap only containing smb traffic, see code or protocol in regards to used bpf (filter)
-n, --noclean | do not clean created tmp files
-h, --help | Prints this usage info and exits.

## Examples
```
# run smbtimeline against test.pcap, write a protocol into the file p.txt 
# and producing timelines for SMB Version1 and SMB Version 2 & 3, write log2timeline csv output to l2t.csv
python3 ./smbtimeline.py -1 -2 -p p.txt -e l2t.csv -f test.pcap

# run smbtimeline against test_large.pcap, do not clean up temp files, 
# strip traffic and produce a timeline for SMB Version 2 & 3
python3.exe ./smbtimeline.py --smb2 --noclean --strip --file test.large.pcap

# using defaults:
# run smbtimeline against test.pcap, write a protocol to protocol.txt 
# and produce a timeline for SMB Version 1 and SMB Version 2 & 3
python ./smbtimeline.py -f test.pcap
```

## Limitations
more to come

## License
* Free to use, reuse and redistribute for everyone.
* No Limitations.
* Of course attribution is always welcome but not mandatory.

## Bugs, Discussions, Feature requests, contact
* open an issue
* contact me via twitter: @b00010111
