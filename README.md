# library-tagger
Collects and tags pdfs spread across the filesystem to remove duplicates and increase utility.

## Rationale
Every project has a collection of PDFs.
Closely related projects overlap PDFs, wasting space.
Even carefully curated PDFs in this context are either:

- Dropped into a giant folder organized by author/year
- Split across subfolders denoting topic (e.g. `logic`) but topics are task-specific and debatable

The purpose of this project is to collect PDFs across a filesystem and perform the following operations:

1. Rename the PDF by

    a. Extracting Author/Title/Year using [GROBID](https://github.com/kermitt2/grobid)
    
    b. Renaming the file [in TagSpaces style](https://docs.tagspaces.org/tagging#file-tagging-based-on-filename) with
    
    - FirstAuthorLastName~Year Title1 Title2 Title3 (where these are non stop words) followed by
    
    - [Tag1 ... TagN].pdf where TagX is
    
      - Each directory of the PDF's current file path
      - Author lastnames of the PDF
      - Keywords of the PDF
      - Year of the PDF
      - Title words of the PDF (stopwords removed)
      - Eventually it would be good for this to include all my publications that cite this paper

2. Move the PDF to a common folder, e.g. `/z/aolney/library`

3. Deposit a symbolic link in the present directory with the old name linking to the new file

At this point only a subset of [TagSpaces features](https://docs.tagspaces.org/userinterface.htm) will be needed to organize/search PDFs. 
