# mulit-developer-workflow
Multi-developer Git workflow scheme


1) the remote 'master' (or 'main') is always stable.
2) one strategy is to have a long-running 'dev' branch, which we all work on.
3) we each can branch off the local dev and explore locally, but merge often into the local dev copy.

4) My adaptation of one recommended merge sequence for 'dev' is:

    a) On Github, maintain a master branch and a dev branch

    b) The master branch is the same as production or contains deployment ready code

    c) The dev branch is ahead of master and contains all new code currently being worked on

    d) Each developer works on the dev branch as follows:

        i) new development is done on a local branch 'a' off of dev
    
        ii) when ready to merge 'a' into 'dev':
   
           a.o) git commit 'a'
        
           a.i) git checkout 'dev'
        
           a.ii) git pull origin dev /'/ capture updates from other developers
        
           a.iii) fix merge issues in local dev
        
           a.iv) git commit dev
        
           a.v)  git checkout 'a'
        
           a.vi) git merge dev // catches 'a' up to date with dev
        
           a.vii) fix merge issues in a
        
           a.vii) git commit 'a'
        
           a.ix) git checkout dev
        
           a.x) git merge a
        
           a.xi) git commit dev
        
           a.xii) git push origin dev

Repeat a.ii, a.iii, a.iv, a.xii if the push fails because another developer sneaked in a push to dev before all the other steps were finished.
