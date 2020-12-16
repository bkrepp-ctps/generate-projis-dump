# generate-projis-dump

This repository is the historical archive of work done to extract data from the Massachusetts Department of Transportation's (MassDOT')
PROJIS (Project Information System) database by means of "scraping" data from HTML pages obtained by querying the PROJIS database
programmatically. As of about 2 years ago, this work became obsolete, as _programmatic_ access to the PROJIS database over the web
was no longer available - at least as best one can tell. The programmatic access was - at least apparently - an undocumented fature,
which was reverse-engineered by this author for the purpose of extracting information from the PROJIS database frequently, when
no other mechanism was available.

This repository consists of two sub-directories:
* first_version, and
* final_version

The contents of these are, respectively, the code for the first working version of the tool (which became known
as "The PROJIS Screen-scraper", and the final working verison of it. Both version of the tool make use of 
__version 3__ of the [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) library.
BeautifulSoup version 3 will become unsupported after December 31, 2020, so the code in this repository is something
of a relic. Nonetheless, it is useful as an illustration of how to use BeautifulSoup to programmatically extract
data from web pages that have both (1) a rather complex strucutre, and (2) which contain some invalid HTML.

The following extract from the header comments for the "PROJIS Screen-scraper" is worth quoting here:

```
__Module__: generate_projis_dump  
__INPUT__:  The HTML generated by the MassDOT PROJIS system for all projects in the Boston MPO area.  
__OUTPUT__: A CSV file, each record of which contains the attributes for one PROJIS project, extracted
        from the top-level HTML file as well as the HTML for the page containing detailed information
        for each project.

This module uses the BeautifulSoup library to handle reading, parsing, searching, etc. of the HTML.
BeautifulSoup is able to handle reading/parsing of mal-formed (as well-formed) HTML w/o crashing.
However, in cases where the input HTML is mal-formed, the ability of BeautifulSoup to search/navigate
the HTML is somewhat limited. There is at least one such case in the PROJIS HTML (see in-line comments,
below). In this case, we search/navigate through the HTML in question as raw text.
```

The following extract from the README.txt file that accompanied the installed version of the "PROJIS Screen-scraper" is also worth quoting:

```
The PROJIS "Screen Scraper" extracts information about all PROJIS projects in the Boston MPO area currently in the PROJIS database,
and writes it to an output CSV file. 

The main Python file is "generate_projis_dump.py"; the support library is "BeautifulSoup.py".

To run:
1. Open IDLE, then type
2. import generate_projis_dump
3. generate_projis_dump.generate_dump(output_file_name)

The output_file name parameter must be passed as a quoted string.  
If "" is passed for the output_file_name parm, the output file defaults to   
"./projis_dump_<month>_<day>_<year>.csv", e.g., "./projis_dump_11_25_2009.csv".  

No "input" parameter is required.
```

The __first_version__ subdirectory contains a file named __boston_mpo.html__ which are the saved results of _manually_ querying the PROJIS database for
all projects in the Boston MPO region on (approximately) November 25, 2009. It is useful as an example of the HTML parsed by the first version of this
screen-scraper.

Respectfully submitted,  
B. Krepp, attending metaphysician  
16 December 2020 A.D.
