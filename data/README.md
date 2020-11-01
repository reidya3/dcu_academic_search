# Details:

| file/folder  | description |
|---:|:---|
| SOC_Researchers.csv | A CSV file containing a list of lecturers, their doras pages, their google scholar profile pages, and their  orcid's. |
SOC_Researchers.csv | A CSV file containing a list of lecturers, their doras pages, their google scholar profile pages, their  orcid's and their name format that appears on doras. |
| Doras SOC | A  folder containing a CSV file that is containing the scraped paper details of the [school of computing](http://doras.dcu.ie/view/groups/groups2a.html) section of the doras website. |
|Doras publications | A folder containing CSV files of each of the researchers scraped doras profile details. |
| Google Scholar Publications | A folder containing  CSV files of each of the researchers scraped google scholar profile details. | 
| Missing Publications | A folder containing files which consist  of  publications that are not on doras  or on google scholar and their corresponding mismatches.  |
| Individual Missing Publications | A folder containing files which consist  of  publications that are not on  a researcher's doras page and blications that are not on  a researcher's google scholar page |
| Neo4j | A folder containing files which were needed to create the neo4j database. The process is detailed in the collaborations notebook!|


## Finding missing publications.
For finding the missing publications, I used the standard Levenshtein distance similarity ratio, regular expressions and performed empirical analysis. I had to specify specific thresholds for certain researchers, however, the majority were set at  a default (90). However, there were some rogue publications that were above such a threshold but still dissimilar. I hardcoded such files into  a csv file called mismatches_not_on_doras or  mismatches_not_on_google_scholar. This may a problem for future iterations. I tried other methods such as  the cosine similarity ratio using word n-gram, character n-grams and ‘char_wb’( which creates character n-grams only from text inside word boundaries; n-grams at the edges of words are padded with space) to try and catch the rogue publications .  However, none provided a  clear threshold  for which I  could separate the rogues from the similar publications and in some cases, the cosine similarity ratio did not find the nearest title!
Example: The google scholar  title was "Computer Vision for Lifelogging: Characterizing Everyday Activities Based on Visual Semantics" the nearest title on doras was actually "Computer Vision for Lifelogging" . However, the cosine similarity ratio suggested "Characterizing everyday activities from visual lifelogs based on enhancing concept representation." as the nearest title. So, in the end, I abandoned using the cosine  similarity ratio.

## Explanation of the columns in Doras SOC:
| Column name | description |
|---:|:---|
| Author list | The author's formatted similar to the way it is presented on the doras website.|
| Full name | The author's name formatted as  first name and  surname without a comma seperating the two names. |
| Authors and Orcid  | Authors that have an orcid and their id. |
| Authors without a orcid   | Authors that do not  have a orcid |
| Year  | Year of each  publication. |
| Publication title | The title of each publication |
| Conf/Journal Details  | Details about the publication. |
| ISBN | The ISBN number of the publication. |
| ISSN  | The ISSN number of the publication. |
| Item Type |Item type of the publication. |
| Event Type | Event where the publication was showcased. |
| Refereed | Referred |
| Date of award | The date at which a PhD or other thesis was awarded. |
| Supervisor(s) | Supervisors of the publication |
| Uncontrolled Keywords | Uncontrolled keywords of the publication |
| Subject | The subjects touched on by the paper |
| DCU Faculties and Centres | The DCU Faculties and Centres involved |
| Use License | The use license of the publication. |
| ID Code | The ID code of the publication. |
| Deposited On | The date and person who entered the publication into the doras system. |
| Published in | Details about the conference or journal |
| Publisher | The publisher |
| Official URL | The url of the publication |
| Copyright information | Copyright information | 
| Funders | The funders of the publication |
| Additional Information | Additional information associated with the publicaton |
| Tweets | The number of treates earned by the publication |
| Mendeley Readers | The number of Mendeley Readers  garned by the publication | 

## Explanation of the columns in Doras publications:
**Same columns** as Doras SOC but with an additional column research name detailing the researcher's name.




## Issues with SOC_Researchers.csv:

 - **Stephen Blott**  doesn't have a google scholar link or an orcid.
 - **Charlie Daly** doesn't have  a doras link or an orcid
 - **Brian Davis** doesn't have  a google scholar link or an orcid.
 - **Mark Humphrys** doesn't have a google scholar link, doras link or an orcid.
 - **Musfira Jilani** doesn't have a doras link or an orcid.
 - **Jane Kernan** doesn't have a google scholar link or an orcid.
 - **John McKenna** doesn't have a doras link or an orcid.
 - **Alessandra Mileo** doesn't have a google scholar link.
 - **Nivedha Nagarajan** doesn't have a google scholar link, doras link or an orcid.
 - **Dongyun Nie** doesn't have a google scholar link or an orcid.
 - **Darragh O'Brien** doesn't have an orcid.
 - **Mark Roantree**  doesn't have an orcid.
 - **Brian Stone** doesn't have a google scholar link, doras link or an orcid.
 - **Irina Tal** doesn't have an orcid.
 - **Jagadeeswaran Thangaraj** doesn't have a doras link.
 - **Renaat Verbruggen** doesn't have a google scholar link, doras link or an orcid.
 - **Ray Walshe** doesn't have an orcid.

 ## Issues with doras:

 Different naming formats between the people's section of the [school of computing website](https://www.computing.dcu.ie/people/Academic%20Lecturing) and doras. Examples:  (Paul M. Clarke, Paul Clarke), (Tomas Ward, Tomás E. Ward), (Darragh Ó'Brien, Darragh O'Brien).

Some of the orcid's associated  with the authors were incorrect. Examples: The first paper on Cathal Gurrins doras page leads you to a person named "Hyowon Lee". The last paper of Brian Davis doras page leads you to Kevin McGuinness.

**Both** David Sinclair and Jagadeeswaran Thangaraj orcid's were not listed on doras but can be found.

On Monica Ward's doras page, the first paper does not have her credited as an author.

Generally, if a person had the first letter of their middle name in their name format, the google scholar profile would not show up. However, this was resolved by removing this.

For these reasons, I gathered SOC_Researchers.csv manually.




