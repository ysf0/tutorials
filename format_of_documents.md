
# FORMAT/STANDARTS OF DOCUMENTS
All tutorials should follow all below standards.

## TEXT (CONTENT)
- Splitting any paragraph/text in to items is suggested. That makes easier to read and update the sentences.
- All explanations/sentences should be short and simple. Wikipedia's "Simple English" language can be taken reference.
- For above 2 rules [file:"agile_scrum.md"](https://github.com/ysf0/tutorials/blob/master/tutorials/agile_scrum.md) can be taken as reference example.

## MARKDOWN FILE
- Bold words should be defined with double underscore character (__). Normally Markdown allows using double star character (**) as well.
- Markdown allows HTML and CSS. However we don't use them. Because github.com and other sites ignore them.
- Do not use > for code blocks. Always prefer ``` even for single-line code.
- There are many Markdown languages (as it is explained on "Markdown" topic). In this project we use CommonMark which is being supported by github.com and VSCode as default.
- All files are in UTF-8 format. But do not use all UTF-8 supported characters. Test each character in different input UI components before use it. Because some characters (especially icons) are not supporting by many document viewers/editors. As an example ▇ (full box) character is supporting by many viewers/editors. But the length is different on different viewer/editor. Therefore prefer # instead of ▇.
- Each file should not be greater than 1 MB. Because of 2 following reasons:
  - Github.com does not show Markdown output (preview) files which are greater than 1 MB.
  - Better performance when editing and reading files (especially from mobile/tablets).

## REFERENCES (SOURCES)
- There may be missing informations (it will always be there anyway), but the accuracy of the available information is very important. If we are not sure about the accuracy of a sentence, it should be mentioned that we have no any sources related to it.
- The source of every simple sentence should not be specified to prevent the file to be big.
- Each URL (even they are not source of any content) should be archived/cached on "archive.is" and "web.archive.org". Also they should backup locally as PDF and HTML format. The details related to it source and the archiving date should be given in [file:"sources.yml"](https://github.com/ysf0/tutorials/blob/master/sources.yml) file.
- There is no reason to save PDF or image files in multiple formats. In those cases the reasons should be defined as "no_need_html_backup_of_pdf_or_image_files".
- The image files should be saved as PDF only.
- Source code or any other text output should saved also in multiple formats locally. Because in some cases text copying is buggy from PDF files. In this cases we may need HTML file.
- If the source file is video and the video player page does not contain any information, then the page should be defined as "video_only_and_no_other_information_to_backup" on [file:"sources.yml"](https://github.com/ysf0/tutorials/blob/master/sources.yml) file.
- If the source data is too big and it does not contain important data then it should not be backup locally. Those sources should be marked as "content_is_not_important_and_too_big".
- Some URL's can be archived with it's hastag (#). Therefore in case any source from "archive.is" or "web.archive.org" is being searched, proceeding with and without hashtag would be better. Also "http" and "https" combinations should be searched.

## READING TUTORIALS
- On mobile/tablet devices prefer a web browser to open any file (do not open the files with any text editor. It may freeze the UI).
- Do not export/convert files as PDF (A4) or any landscape file format. Because the tables does not fit on the page. The only stable format is "HTML" which supports landscape tables.

## TITLE FORMAT
- Abbreviations should have a prefix "abb-tr", "abb-eng". Abbreviations must be written in the title. That makes easier to search with keywords. But the prefixes are optional. Prefixes (such as "abb-eng") does not have to be added (if not necessary). 
  - Example-1: "app" is abbreviation of "application". This information is well known. 
  - Example-2: If the title has Greek characters then we don't need "gr" prefix.

  Valid title examples:

  - > eng:application (or abb-eng:app or tr:uygulama or gr:πρόγραμμα)
  
  - > application (or app or tr:uygulama or gr:πρόγραμμα)
  
  - > application (or app or tr:uygulama or πρόγραμμα)

- If an abbreviation is abbreviation of a proper name (independent of any language) it gets a prefix only: "abb". Example:

  > Kubernetes (or abb:K8s)

- If a title has an older synonym, it gets "old-name" prefix. Example:

  > Solaris (or old-name:SunOS)

  If a title has an older name, that means the term is proper name. And proper names are independent of any language. Therefor it does not get a language keyword (eng, tr, gr...).

- Any information about the title terminology should be written in the first sentence after the title.

- Title should contain exact synonym words. The words in the title should not have close meanings to each other. Otherwise it can be mentioned in the next line.

- In order to define the word within the paragraph, it needs to be defined same as in title format. Example: 

  > Firefox is an open source application (or abb-eng:app or tr:uygulama)
  
- Version lists/tables should have a title which suffixed with "version history". Example:

  - > "HTTP version history"
  - > "Android version history"
  
  This makes searching standardized.
