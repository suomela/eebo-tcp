Tools for processing EEBO TCP
=============================

Setup
-----

    git submodule update --init --recursive
    make -C xml

Make sure all TCP XML files are available in the subdirectory `tcp-xml`:

    mkdir tcp-xml
    cd tcp-xml
    sh ../tcp-texts/graball.sh

Install GNU coreutils and pcre from homebrew:

    brew install coreutils pcre


Listing EEBO texts
------------------

All freely available files:

    ./list-eebo-tcp

All freely available files with a well-defined date in the 1600s:

    ./list-eebo-tcp 1600 1699

Output:

    A00002
    A00008
    A00011
    A00012
    ...

Get file names:

    ./list-eebo-tcp-files 1600 1699

Output:

    tcp-xml/A00002.xml
    tcp-xml/A00008.xml
    tcp-xml/A00011.xml
    tcp-xml/A00012.xml
    ...

All freely available files with a well-defined date in the 1600s,
with 1 to 8 pages:

    ./list-eebo-tcp 1600 1699 1 8


Processing EEBO texts
---------------------

Get plaintext version of one file:

    xml/xml-plaintext TEI/text tcp-xml/A12074.xml

Extract words:

    ./words tcp-xml/A12074.xml

Most common words:

    ./words tcp-xml/A12074.xml | ./top-words | head -20

Get plaintext version of all texts from 1600-1609:

    ./list-eebo-tcp-files 1600 1609 | xargs xml/xml-plaintext TEI/text

Most common words of all texts from 1600-1609:

    ./list-eebo-tcp-files 1600 1609 | xargs ./words | ./top-words | head -20
