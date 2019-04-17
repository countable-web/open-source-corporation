
# Storage

## Scope

This page should make it clear where all work is saved.

## Purpose

To enable anyone to find any file or asset, without having to ask the person who created it where it is. For example:
  * devs need to find sliced versions of assets
  * clients and other team members need to find mock-ups, and know which is latest, such as XD links.
  * artists need to find raw project files in order to be able to take over each others' work.

Every file we create should have one obvious place that it is stored. If there seem to be 2 or more options as to where a file is stored, we should clarify our process.

## List of Storage Locations

We should store things only in the places and ways described below.

| System  | What Goes Here | Who Has Access |
| ------------- | ------------- | ------------- |
| GitHub - this repo  | Document how and why we do things | Everyone in the world |
| GitHub | Open source code | Everyone in the world |
| Trello | Work requests, tasks. Never store work deliverables here, only links to Google Drive | The specific client and project staff |
| Bitbucket | Private source code | The specific client and project staff |
| Google Drive `/clients/<client slug>/<project slug>` folder | Private client files (such as artwork) | The specific client and project staff |
| [Google Drive `/team/` folder](https://drive.google.com/drive/folders/12iWzlcOP_qdFlVcM_U1yLVKB6IDq4Uvd) | Private company data (minimize this) | Our staff |
| [Google Drive `/public/` folder](https://drive.google.com/drive/folders/1Do2l9oaPHlyJ-J6w-BoGAvUmJjK1mDk3) | Any public assets (maximize this) | Everyone in the world |
| Google Drive (your own folders) | Never store anything here | You |
| Your local computer | No more than one day's work | You |

Never share work directly in slack by uploading it. Only share links to things stored in the correct place in Google Drive.

## Folder Structure on Google Drive

### General Guidelines
  * Our work should be organized based on how how it's used. For example, artwork will typically need an editable copy for developers.
  * The goal is to be able to find the things we need quickly. Things we use more often should take fewer clicks.
  * Make sure your work is stored in a way that is convenient for those who will be using it.
  * When a file is no longer needed, outdated, or otherwise more likley to confuse than help, move it to a folder named ARCH in the same directory.

### Standard Folders

#### Client Folders

In `/clients/`, we have a folder for each client, using an [official client slug](https://docs.google.com/spreadsheets/d/11IvCJCtw0iD4vWEOY_tNMvpUnte2eb1Z3exMMtevIzk/edit#gid=279543225). The slug is typically the client's domain name. These folders look like: `/clients/<client slug>`.

#### Project Folders

In each `/clients/<client slug>` folder, we have a folder for each project, using an [official project slug](https://docs.google.com/spreadsheets/d/11IvCJCtw0iD4vWEOY_tNMvpUnte2eb1Z3exMMtevIzk/edit#gid=279543225). A project should be all activity organized around a specific objective (set of problems to solve). These folders look like `/clients/<client slug>/<project slug>`.

#### Standard Folders

  * `preproduction` these are inputs to the project that existed beforehand.
  * `design` are raw project files designers work on.
  * Please structure design assets as follows [ image ]
  * For Reviews, please use the format YYYY.MM.DD_
  * When creating a new project in Google Drive, copy the template linked [ here ]

### Google Drive Folder Standards

TODO: clarify our standards. An example is here, but it's not obvious how to follow it, https://drive.google.com/drive/u/0/folders/1iPhpEg1RuEz_ki4yNgzSOg9Z257Mpa7x?ddrp=1

  * Why were these folder names chosen?
  * How and where do add new stuff?

### Countable Marketing Folder

https://drive.google.com/drive/folders/1iPhpEg1RuEz_ki4yNgzSOg9Z257Mpa7x?usp=sharing

All the old files are in there, but they've been organized into the following categories:
1. cwp_logo: in this folder exists our most up-to-date logo, its styleguide, and an _archive folder which houses all previous versions.
2. cwp_marketingassets: this folder has a lot of content - any individual assets that have been created for marketing purposes (business cards, social media profile images and banners, brochures, signage, video, team bios, CV, proposals, etc) AND their working files.
3. cwp_marketing: this folder includes a folder for our blog and a folder for various tradeshows and other marketing events.
4. cwp_website: another big one!  This folder includes all of countable.ca's web design files, content strategy, and assets, including sliced images and the logo files specifically used for the website.


It is based on Felipe's folder design schema (attached) and this article: https://pixeldreams.com/blog/best-practices-folder-structure/
