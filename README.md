# Using Git Large File Storage (LFS)

If you've tried to use GitHub for storing large files, then you've probably realized there are [hard limits for file and repository sizes](https://docs.github.com/en/github/managing-large-files/working-with-large-files/what-is-my-disk-quota). While there are options for externally hosting and embedding large files (like AWS S3, Google Drive, DropBox, etc.), the preferred method is to use Git Large File Storage (LFS). Git LFS is easy to implement and doesn't require you to work outside the Git workflows for handling and uploading large files to your GitHub repositories.

With Git LFS, you can use GitHub to store files up to 2 GB.

## Why use Git LFS?

Every time you create a commit, Git creates a new tree object of your repository's files. When this happens, files are added for ones that have been modified, and the old file is stored in the commit history. If you're modifying large binary files (like images, datasets, or videos), you could quickly approach storage limits since every version of every file is preserved. When someone clones your repository, they in turn have to download every version of every file that has been changed, which could take some time and continue causing unnecessary problems when pushing and fetching.

Git LFS works around this by created pointers to large files and storing them alongside your GitHub repository. When you modify a large binary file, Git updates the new pointer file, and only the large files they reference – not the modified version history. This means your GitHub repository will have a reduced storage size, and only the latest version of large files will be downloaded when the repository is cloned.

These resources contain information for learning more about Git LFS:

- [Git Large File Storage](https://git-lfs.github.com/)
- [GitHub Docs - About Git Large File Storage](https://docs.github.com/en/github/managing-large-files/versioning-large-files/about-git-large-file-storage)
- [GitLab Docs - Git Large File Storage (LFS)](https://docs.gitlab.com/ee/topics/git/lfs/)
- [Atlassian Bitbucket Tutorials - Git LFS](https://www.atlassian.com/git/tutorials/git-lfs)

## How to set up Git LFS for your GitHub repository

Certain binary files are often used in virtual teaching and learning resources, including:

- High resolution image files
- Zipped directories of workshop data
- Video recordings of lectures or tutorials
- Audio files
- Gifs of screencasts

**If your resource contains binary files which exceed a file size of 15 MB or more, the suggested practice is to use Git LFS.**

## Download Git LFS

In order to use Git LFS, you must first download and install it on your machine.

#### For Mac and Linux:

1. Go to [git-lfs.github.com](https://git-lfs.github.com/) and download the version for your operating machine.
2. Unzip the file you downloaded.
3. Open Terminal and navigate to your unzipped folder.

```
cd ~/path/to/folder
```

4. Inside that folder, run the Bash installation script.

```
./install.sh
```

You should see a reply prompt saying Git LFS has been initialized. You only need to do this one time for your user account.

#### For Windows:

1. Go to [git-lfs.github.com](https://git-lfs.github.com/) and download the version for Windows.
2. Unzip the file you downloaded, and navigate inside the new folder.
3. Double-click the file called _git-lfs-windows-1.x.x.exe_
4. To verify it has been installed, open GitBash and type

```
git lfs install
```

You should see a reply prompt saying Git LFS has been initialized. You only need to do this one time for your user account.

## Track your large files

Once Git LFS is installed on your machine, you can start using it by tracking specific large files or folders of files.

#### Track a specific file

1. In Terminal or GitBash, navigate to your Git repository

```
cd ~/path/to/git/repo
```

2. Select the file that you want to track with Git LFS

```
git lfs track "data/big-file.tiff"
```

If successful, you will see the reply prompt `Tracking "data/big-file.tiff"`

3. Make sure your `.gitattributes` file is being tracked

```
git add .gitattributes
```

#### Track a specific file type

1. In Terminal or GitBash, navigate to your Git repository

```
cd ~/path/to/git/repo
```

2. Select the file type that you want to track with Git LFS

```
git lfs track "*.tiff"
```

3. Make sure your `.gitattributes` file is being tracked

```
git add .gitattributes
```

#### Track all files recursively in a folder

1. In Terminal or GitBash, navigate to your Git repository

```
cd ~/path/to/git/repo
```

2. Select the folder with files that you want to track with Git LFS

```
git lfs track "myfolder/**"
```

3. Make sure your `.gitattributes` file is being tracked

```
git add .gitattributes
```

Once you have pushed your tracked files to GitHub.com, you will see a note indicating your files hare being stored with Git LFS

![tracked files](/content/tracked-files.png)

Use the path to the raw file if you are using GitHub to host content that will be linked or downloaded.
