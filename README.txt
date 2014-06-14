

2014-June-13,14
Reed Wade
National Library of NZ -- Heritage Preserve Code Jam

PST files from Brian Opie

--

License: see accompanying LICENSE file.

--


Refs:

PST format -

    http://mobisocial.stanford.edu/muse/
    http://en.wikipedia.org/wiki/Personal_Storage_Table
    http://linuxblog.kieser.net/2010/09/converting-pst-files-to-linux-mbox.html

PST tools - 

    http://www.five-ten-sg.com/libpst/

Elastic Python module -

    http://elasticsearch-py.readthedocs.org/en/master/

--

PST tools installation on Ubuntu

To install:

    apt-get install pst-utils

provides these commands--

    lspst - lists content within a pst file
    readpst - converts/extracts content from files

--

PST extraction / conversion


To convert from pst file to a single mbox file:

    cd mbox
    readpst ../original-PST-files/atl.pst

this creates an mbox file called 'atl' in the current directory.

--

To create a collection of separate files per message along with their related attachments:

    cd separate
    mkdir atl
    readpst -S -o atl ../original-PST-files/atl.pst

----------------------------------------------------------------------

Injecting email content into Elastic search engine


Install Elastic Python module:

    pip install elasticsearch


Then, install elastic search engine (not described here).

Run the injector script (current version has hardcoded locations to look for
mbox files and presumes elastic is on local machine.

    bin/load_messages_into_elastic

--

Getting a CSV summary file of messages. This was used for the data vis Sarah made:

    bin/get_messages_metadata

creates a file in the current directory named 'out.csv'.

Needs further testing but seems to mostly work.

--

Known Bugs:

    - fails on certain charset encodings and skips injection of messages with at Thai content, probably others
    - needs a lot more testing to be sure

