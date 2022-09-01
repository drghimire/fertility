Step 1: Create Version Control System (Git and GitHub) Project in R
Step 1.1: Creating a repository in GitHub
	Logon to GitHub Account: https://github.com/drghimire
		Creditionals: drghimire/D@remas1@
	Create a newrepository "fertility"
		Step 1: Go to your repositories
		Step 2: Click "New"
		Step 3: Provide information as follows
			Repository name: fertility
			Description: Subnational Fertility Analysis
			Public/Private: Select Public or Private according to your choice. I prefer "Public"
			Initialize this repository with
				Check "Add a README file"
			Add .gitignore
				Select .gitignore template: R
			Choose a License
				Select GNU General Public License v3.0
			Click "Create repository"	
			Now your new repository created
		Step 4: In the newly created repository, select "Settings"
		Step 5: In the "Code and automation" section click "Pages"
			Under the "Build and deployment", under "source" select "Deploy from a Branch"
			Under the "Build and deployment", under "branch", use the "None" or "Branch" dropdown menu and select a publishing source.
				I prefer: branch as "Main", and publishing source as /docs.
			Click "Save" button.
		Step 6: Your site is ready to be published at: https://drghimire.github.io/fertility/

Step 1.2: Creating a R Project Using Git Version Control
	- Step 1: Open RStudio
	- Step 2: Clieck File -> New Project -> Version Control -> Git
		- Provide Git Repository URL (As created in Step 1.1): https://github.com/drghimire/articles
		- Project Directory Name: articles
		- Create Project As Subdirectory of: "C:\Users\dghimire\nexus\articles"
	- Then Click -> Create Project
	- Open R Project file -> "C:\Users\dghimire\research\articles\fertility\fertility.Rproj"

Step 1.3: Turn off Jekyll
	- This bit is only necessary if you plan to use GitHub Pages for publishing your website. We need to tell GitHub Pages to bypass using Jekyll to build your site. 
	  Jekyll works behind the scenes in GitHub Pages as a static site generator. Turning it off ensures that later down the line we won’t run into problems with 
	  including formulas, equations, and folders that start with an _ underscore, should we decide to do that.
	- We complete this step by adding a single empty file named .nojekyll to your project root directory by running the following in the console:
	> file.create(".nojekyll")
	- This is a hidden file, so don’t worry if you don’t see it in your Files pane after it’s been created.

Step 2: Making Folder Structure
 - project ~ Root directory which has several projects sub-directory
 - projectxx ~ unique project name used for working directory, which contains following sub-directories
	- analysis ~ R script files for exploratory and predictive Data Analysis
	- docs ~ contains output of the article, i.e, "dhruba-fertility" in PDF format.
	- endmatter ~
	- figures ~ figures produced during data exploration
	- frontmatter ~
	- latex ~
	- mainmatter ~ R markdown files used for reproduciable research (articles/reports/books/...)
	- maps ~ maps produced during data exploration
	- refdata ~ reference datasets other than censuses and surveys
	- references ~
	- tidydata ~ cleaned datasets from rawdata
	# Additional Folders, When Necessary!!
	- rawdata ~ primary datasets collected from surveys (household, community) and research (quantitative or qualitative)
	- tidying ~ syntax files used to clean the datasets including labels
	- geodata ~ spatial datasets used to visualize information in maps

Example, in R software environment:
 R> /articles/datasets => articles is a sub directory of the root directory.
 R> articles/datasets => articles is a sub-directory of the current working directory.
 The working directory is the directory where the program automatically looks for files and other directories, unless you tell it to look elsewhere. 
 It is also where it will save files.

Step 3: Create a Skeleton Project from bookdown package 
bookdown:::bookdown_skeleton(getwd())	# will create a skeleton project in your current working directory.

Then the following set of files will be created.
--------	
_bookdown.yml
_output,yml
01-intro.Rmd
02-cross-refs.Rmd
03-parts.Rmd
04-citations.Rmd 
05-blocks.Rmd
06-share.Rmd
07-references.Rmd
book.bib
index.Rmd
preamble.tex
README.md
style.css
fertility.Rproj
--------

Step 4: Rename the above newly created files (if necessary) as follows
ch1-introduction.Rmd
ch2-review.Rmd
ch3-methods.Rmd
ch4-results.Rmd
ch5-discussions.Rmd
ch6-conclusions.Rmd
ch7-references.Rmd
references.bib
================================================================================

Step 5: Update YAML in index.Rmd, _bookdown.yml, and _output.yml

_bookdown.yml
----------------------------
book_filename: "fertility"
delete_merged_file: true
rmd_subdir: "mainmatter"
rmd_files:
  - index.Rmd
  - ch1-introduction.Rmd
  - ch2-review.Rmd
  - ch3-methods.Rmd
  - ch4-results.Rmd
  - ch5-discussions.Rmd
  - ch6-conclusions.Rmd
  - ch7-references.Rmd
  - appendics.Rmd
output_dir: "docs"
language:
  ui:
    chapter_name: "Chapter "
new_session: "yes"
----------------------------

_output.yml
---------------------------
