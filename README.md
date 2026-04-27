# Digital Forensics-EnCase Image Analysis
This repository documents a full digital forensic investigation conducted on a NIST CFReDS forensic test image. The project follows real-world forensic methodology including evidence acquisition, hash verification, chain of custody logging, artifact recovery using Autopsy and Sleuth Kit, and a formal written examination report.
The image included a worksheet with questions that are intended in guiding the investigation along. The website tasks the user with performing a full forensic analysis to attempt to uncover the activities performed by the user of the system.
I will be using the worksheet for guidance and employing my own methods of finding the answer to the question as well as explaining the tools and methedologies along the way. The analysis will include recovery of deleted files, keyword searches, and a timeline creation. Any hidden files and executables will be identified.
Here is the link to the forensic test image used:

https://cfreds.nist.gov/all/DFIR_AB/ForensicsImageTestimage

****

## Chain Of Custody Log

In a real life forensics investigation, the first step would be to collect the evidence and alongside it would be to start a chain of custody form. A chain of custody is the written record of who had an evidence item, when they had it, where it was stored, and why it was handled. This helps demonstrate the evidence was maintained under controlled conditions from collection up to the presentation.

For this project I will be using a template from Elite Digital Forensic:
https://elitedigitalforensics.com/free-chain-of-custody-form-computer/

I will be filling this form before beginning with the investigation


Here is the folder format on my external drive
CaseName\
	evidence\
		original_image.dd -- will not be touching this original copy
	working\
		copy_image.dd -- only work from this copy
	hashes\
		hashes.txt -- MD5 + SHA256 of original
	autopsy_case\
		CaseName.aut -- autopsy case file
		CaseName\ -- the autopsy generated data
	reports\
		chain-of-custody\
			2020JimmWilson-Chain-of-Custody -- chain of custody log for the case
		email-headers\
			email.eml -- any raw email headers are kept here
		evidence-inventory\
			evidence doc -- any original evidence extracts are kept here
		evidence-notes\
			evidence.md -- individual notes for each piece of evidence kept here
		image-evidence\
			originals\
				original.jpg -- original image jpg for metadata
			screenshots\
				screenshot.jpg -- screenshots for personal reference
			working-copies\
				originalcopy.jpg -- copy of orginal to examine
		case_notes.txt
		evidence_report.pdf
		
For note taking I will be using Obsidian under the reports folder and creating md files for any important evidence any screenshots will also be added there.

The Following Steps were taken:
1. Evidence Aquisition
	* The disk image that was downloaded was already in E01 format
	* verified integrity using MD5/SHA-1 hashes
	![[Screenshot 2026-04-08 201108.png]]
	* I will store this hash in the hashes folder under hashes.txt
	* Now I will be storing a copy of the image under the working folder and checking the hash for integrity and it should match with current hash we have stored.
	![[Screenshot 2026-04-15 193900.png|643]]
In this image we can see that the hashes are the same so now we can get started with working on finding any evidence and information from this disk image.

Additionally under the /evidence-inventory folder there is an excel file that was extracted from autopsy that contains a log of all the evidence along with its metadata and the hashes for each piece of evidence extracted.

2. Analysis in Autopsy:
	* Loaded image into Autopsy
Autopsy sort any files into separate section under the data artifacts. This makes the analysis a lot simpler when if you know what you are looking for whether it is email messages or the recycle bin. This makes it easier as you dont have to go through the folders individually.

![[Pasted image 20260427105108.png]]

When going through the emails and other files autopsy has the feature of being able to tag items for later review. There are a number of tags such as being able to put them under "notable", "followup", "bookmark", or you can create your own personal tags along with adding comments.
I decided with going through the files in the disk image and finding anything that seemed to be suspicious and could be used for evidednce and tagged them as notable. I would go through these files later on and analyze them individually and take notes on the evidence.
Here is an example of the note format I kept for each piece of evidence:
![[Pasted image 20260427113545.png]]

Once I finished collecting notes and evidence I put together a report on the evidence a report in markdown file format in order to be able to make editing a lot more simple. I used this document as a draft and produced a final report for the case.
