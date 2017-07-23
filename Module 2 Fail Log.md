# Module 2 Fail Log 

## Exercise 1 - The Dream Case

- Read the instruction from the HIST3814O workbook

-Opened DH box from my browser - would not open, did not know why 

- Tried opening up the DH box using the link provided in Module 1, exercise 2, still did not work

- Re read some of the instructions for Module 1, exercise 2 and noticed it mentioned the Carleton VPN

Checked to see if I was connected and discovered I was not 

I then conected to the Carleton VPN and tried DH box again, it worked 

Once my DH box was open, I continued with the steps in the exercise.

I decided to use the Commwealth War Graves Commission as my database. 

I searched for my surname Barker, in the first world war and received a huge amount of data. 

I decided the refine my search, so I chose Barker, First World War, United Kingdom and Navy. I was happy with those results.

I downloaded them to my hardrive. 

I then returned to my DH Box and opened Nano text editor.

I made a record of what I searched, the URL of the search and the results. 

I downloaded that file to my hardrive and uploaded to my gitbut repository. 


## Module 2 Exercise, 2 - Wget

I started by doing Ian Milligan's Automated Downloading with Wget tutorial.

I skipped to step 2 because I already have Wget on my DH Box.

In Wget, I made a new directory by doing mkdir wget-activehistory 

I then did cd wget-activehistory to get to the new directory 

then did wget http://activehistory.ca/papers/

I took the file I created from File Manager and downloaded a copy to my hardrive

I then uploaded it to Gitbut 

I then went back to the workbook and read the next steps.

I opended my DH box again and put in  $ mkdir equity

I got an error code, it said command not found. I tried again this time copy/pasting directly from the workbook.

It worked.

I did then put $ cd equity.

Then $ pwd

Then wget http://collections.banq.qc.ca:8008/jrn03/equity/src/ -A "*188*".txt -nc -r --no-parent -nd –w 2 --limit-rate=20k

It took a long time for DH Box to process the last command. I am not sure I got the outcome that was desired.

I downloaded a copy from file manager and uploaded it to my Github.

I need to consult my peers outcomes to see if we have produced the same work. 


## Module 2, Exercise 4 - APIs

I started off by reading the instructions in the workbook 

I opended and signed in to my DH box.

Opened Command line and input $ sudo apt-get install jq -y

Then $ mkdir m2e4

Then $ cd m2e4

Then $ pwd

Then $ touch canadiana.sh

Then $ nano canadiana.sh

Then I copy pasted this into the nano, it is an edited version of Ian Milligans API example: #! /bin/bash

pages=$(curl 'http://search.canadiana.ca/search?q=ottawa*&field=&so=score&df=1914&dt=1918&fmt=json' | jq '.pages')

# this goes into the results and reads the value of 'pages' in each one of them.
# it then tells us how many pages we're going to have.

echo "Pages:"$pages

# this says 'for each one of these pages, download the 'key' value on each page'

for i in $(seq 1 $pages)
do
        curl 'http://search.canadiana.ca/search/'${i}'?q=montenegr*&field=&so=score&df=1914&dt=1918&fmt=json' | jq '.docs[] | {key}' >> results.txt
done

# the next two lines take the results.txt file that is quite messy and clean it up. I'll try to explain what they all mean. Basically, tr deletes a given character - so we delete quotation marks "\"" (the slash tells the computer not to treat the quotation mark as a computer code, but as a quotation mark itself), to erase spaces, and to find the phrase "key:" and delete it too.

sed -e 's/\"key\": \"//g' results.txt | tr -d "\"" | tr -d "{" | tr -d "}" | tr -s " " | sed '/^\s*$/d' | tr -d ' ' > cleanlist.txt
# this adds a prefix and a suffix.

awk '$0="search.canadiana.ca/view/"$0' cleanlist.txt| awk '{print $0 "/1?r=0&s=1&fmt=json&api_text=1"}' > urlstograb.txt

# then if we want we can take those URLs and output them all to a big text file for analysis.

wget -i urlstograb.txt -O output.txt

Then ctrl+x to save & exit

Before running the program, I put $ chmod 755 canadiana.sh

Then $ ./canadiana.sh

I then saved a copy of my work to my hardrive and uploaded it to my Github.

## Module 2, Exercise 5 

- I started by making a new Twitter account. 

-Then went to https://apps.twitter.com/ 

-New apps and followed the steps on the site

- I then went on the ‘keys and access tokens’ tab

-I wrote down the data requested from the tab: the consumer key, consumer secret, access token and access token secret

- I then went to my DH Box and selected the command line

- I put in $ pip install twarc

- Then $ twarc configure

-$ twarc search canada150 > search.json

- From there, I got the error code : 401 Client Error Authorization Required for URL. It seems like the search did not work.

-Decided to ask for help before continuing.
