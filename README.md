# murcurial-to-github-migration

--for clone form murcurial to local

cd hg-repo----change directory

hg clone url(murcurial selected repo url)

ask for username and pasword

(after it will create clone directory )


--change directory

cd Git-converted-repo/(new directory to fast export--to convert murcurial to github)

--create new directory

mkdir name

--change dir

cd newname

-- initialize the github(initialize empty repo)

git init

----------------------------------------------------------------------------------------------------------------

--for fastexport

/root/fast-export/hg-fast-export.sh -r /root/hg-repo/(name of the cloned repo) --force

/root/fast-export/hg-fast-export.sh -r /root/hg-repo/cdmnet --force

(path of hg-export installation) -------(path of cloned repo)

--> after fast export we need to switch to any one branch otherwise it will give error)

-- if branches is there

git checkout (any branch name)    ----(to switch one branch)

git branch -a (to see all branches in the repo)

  (or)
  
--checkout if multiple branch

git checkout HEAD

if files are large use git lFS after fast export

----------------------------------------------------------------------------------------------------------------

--git push

 git push --mirror url(github)
 
git push --mirror https://kiran-ab01:ghp_Myd2ZZLsZa1dg9TtRGEjJxJkflwy8K0O8u3(secrate access tokens)p@github.com/PrecedenceAus/assistant-released.git



--------------------------------------------------------------------------------------------------------------------------------------
after fast export use git lfs

Step 2: Install git LFS

git lfs install

Step 3: Get the large files details in the repository

git lfs migrate info --everything

Step 4: Convert all the large files with extensions found from above command to LFS on all the branch in repository

git lfs migrate import --include="*.dll,*.a,*.xml,*.cs,*.nupkg" --everything

Step 5: Run GC on repository

git reflog expire --expire=now --all

git gc --aggressive --prune=now


-->switch to one branch using git checkout branch-name(otherwise it will give error)

Step 6: Force push the repository

git push --mirror --force REPO_URL

git push --mirror --force --tags REPO_URL

git push --mirror https://kiran-ab01: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@github.com/PrecedenceAus/Assistant-1.git




pat tokens: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


----------------------------------------------------------------------------------------------------------------------------------------------------

->to convert hg clone repo into github we need external plugin/fast export need to installed 

 before that we need to install murcurial
 
-->link:https://snapcraft.io/install/mercurial/centos

sudo yum install epel-release

sudo yum install snapd	

sudo systemctl enable --now snapd.socket

sudo ln -s /var/lib/snapd/snap /snap

sudo snap install mercurial


-->then we need to intsall fast export using 

-https://github.com/frej/fast-export.git

clone above one to local/remote

-->we need to install pyhton using below code

pip install mercurial

sudo yum install python-pip

sudo yum install python-devel gcc


after installation fallow noraml procdure


https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/importing-a-mercurial-repository

------------------------------------------------------------------------------------------------------------------------------------------------------

-->if users ask to push only required branches without having any history

->clone the repo and switch to the repo(if it is a murcurial repo fast export it and then switch to required branch)

->switch to requried branch(git checkout branch-name)

->remove .git file that will remove all other branch and history/commit execpt  the sorce code of the switched/required branch

rm -rf .git

->intiate the git repo

git init

->check status of untracked files

git status

->add all untracked files(that should be in green)

git add .

->commit the change (it consits only one commit ofter push)

git commit -m "Initial commit"

->git push url

(this can done if we have LFS wile more than 1 gb to 5gb)

(here we can push only one branch to one repo, while we remove .git it will remove all the branch and we remain with source code, so we can push only one branch to repo)

------------------------------------------------------------------------------------------------------------------------------------------------------
->if users ask to push multiple branch in single repo(if we have code in diffrent repo with single branch)

->first clone the repo, if we have more than  2 repos 

git clone url

->go to which repo code need to be push as sub branch of the same repo

-> rename the existing branch "main"

git branch -m main subbranch

-->push the code(it will overwrite the code if we have same branch name and it will create new branch if that branch is not there) 

git push url (url of the repo which main repo that under it will create new sub branch)

-->it will ask for upstream

copy the code and paste to upstream 

->do same if we have nmultiple branch to be pushed to single repo as subbranches

------------------------------------------------------------------------------------------------------------------------------------------------------------------

->if users ask to push Github repo without track the LFS(becouse of after doing LFS import users not able to see code in the UI 

->users need to download LFS to locally to see code in the cloned file and also to push

https://github.com/git-lfs/git-lfs/releases

install Windows Installer for windows

Darwin AMD64 for mac

-->to push repo without tracking lfs file

-first find out in which branch we have lfs file by clone repo to local and switch to required branch and remove .git and try to push to diffrent repo and

- if we have lfs file we get an error like lfs need to track
- 
- if we didn't get any error in that branch we don't have any lfs file
- 
- so we need to find out which branch has lfs and remove the particular barnch
- 
git branch -D branch-name


-->git push










