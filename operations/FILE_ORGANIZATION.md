# File Organization (in Google Drive)

## Purpose

The intention of this standard is to have one obvious folder that any file belongs in, in Google Drive. We want to minimize the cases where there is ambiguity on where to save or retreive a file.

## Scope

We list a standard folder structure for Google Drive


## Folder Structure on Google Drive

### General Guidelines
  * Our work should be organized based on how how it's used. For example, artwork will typically need an editable copy for developers.
  * The goal is to be able to find the things we need quickly. Things we use more often should take fewer clicks.
  * Make sure your work is stored in a way that is convenient for those who will be using it.
  * When a file is no longer needed, outdated, or otherwise more likely to confuse than help, move it to a folder named _archive in the same directory.
  * If an additional folder is needed, create the additional folder and name it according to the naming structure.
### Standard Folders

  * When creating a new project in Google Drive, copy the template linked [HERE](https://drive.google.com/drive/u/0/folders/19uOpYepddtD_fsheccNiAdTOPYYaAymg?ddrp=1)

It is based on Felipe's folder design schema (attached) and this article: https://pixeldreams.com/blog/best-practices-folder-structure/

![Countable Web Production, File Organization Tree](https://github.com/fepirata/final-exam-special-topics/blob/master/public/cwp_file_organization_tree_v01.jpg?raw=true)

| Folder  | What Goes Here | Description |
| ------------- | ------------- | ------------- |
| `/clients/<client slug>` | projects folders for this client. | [official client slug](https://docs.google.com/spreadsheets/d/11IvCJCtw0iD4vWEOY_tNMvpUnte2eb1Z3exMMtevIzk/edit#gid=279543225) |
| `/clients/<client slug>/<project slug>` | projects folders for this client. | [official client slug](https://docs.google.com/spreadsheets/d/11IvCJCtw0iD4vWEOY_tNMvpUnte2eb1Z3exMMtevIzk/edit#gid=279543225) |
| `/clients/<client slug>/<project slug>/01_preproduction` | these are inputs to the project that existed beforehand. |  |
| `/clients/<client slug>/<project slug>/02_design` | raw project files designers work on. | |
| `/clients/<client slug>/<project slug>/03_reviews` | exported work to show the client. | Recommended: Adobe XD links, saved in a Google Doc |
| `/clients/<client slug>/<project slug>/04_assets` | Sliced outputs for developers to take. | PNG and SVG files, separated so they can be positioned dynamimcally |
| `/clients/<client slug>/<project slug>/05_feedback` | New data and information gained as part of the project | Usability tests | 

## Naming Convention

### Folders
The naming convention for folder have the following structure:

![Countable Web Production, Naming Structure guide for folders](
https://github.com/fepirata/final-exam-special-topics/blob/master/public/cwp_naming_guide_folder_v03.jpg?raw=true)

### Files

The files follow a similar structure, the main difference is that files have versioning section in the end of the name:

![Countable Web Production, Naming Structure guide for files](
https://github.com/fepirata/final-exam-special-topics/blob/master/public/cwp_naming_guide_file_v01.jpg?raw=true)

### Guidelines for naming structure

* Replace spaces and dashes by underlines. <b>E.g.: cpw-donut icon => cwp_donut_icon</b>
* Always try to use short desccriptions unless is necessary to be more descriptive.
* Be consistent with your own naming structure. <b>E.g.: if you have a series of icons, don't name them: cwp_icon_pizza, cwp_burger_icon, cwp_hotdog. Instead of that, keep one pattern: cwp_pizza_icon, cwp_burger_icon, cwp_hotdog_icon.</b>

### Guidelines for folder structure

Sometimes is necessary to create additional folders, because of that a simple series of questions were made to help you to decided if you need or not an additional folder:
* Are there 10+ files and it makes sense to nest them into other folders? <b>Create a folder</b>
* Do the files have really distinct content, i.e., doesn't make sense to keep to files together? <b>Create a folder</b>
* Do you need to update a project with a complete new version? <b>Create a folder</b>
* Does the project is small and focused? e.g.: an single page project. <b>Do NOT create a folder</b>


### Nice-to-Have when you organize the folder structure

* There's no rule for uppercase or lowercase words, but if you are in doubt, go for lowercase.
* The versioning is not mandatory for all the files, like documents which most part of the times there's just one version of each file. However, if a second version is created, it needs to be named with the versioning section in the end.
* the five main folders follow a color structure, which visually helps us to guide through the folders. Is good to keep the color pattern every time is possible.
![Countable Web Production, folder color example](https://github.com/fepirata/final-exam-special-topics/blob/master/public/cwp_file_structure_folder_color_example.png)

### Example: Countable Marketing Folder

TODO: make this follow the convention fully.

https://drive.google.com/drive/folders/1iPhpEg1RuEz_ki4yNgzSOg9Z257Mpa7x?usp=sharing

All the old files are in there, but they've been organized into the following categories:
1. cwp_logo: in this folder exists our most up-to-date logo, its styleguide, and an _archive folder which houses all previous versions.
2. cwp_marketingassets: this folder has a lot of content - any individual assets that have been created for marketing purposes (business cards, social media profile images and banners, brochures, signage, video, team bios, CV, proposals, etc) AND their working files.
3. cwp_marketing: this folder includes a folder for our blog and a folder for various tradeshows and other marketing events.
4. cwp_website: another big one!  This folder includes all of countable.ca's web design files, content strategy, and assets, including sliced images and the logo files specifically used for the website.


