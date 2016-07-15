What to do when you have a new feature to add to production:
1. Commit new feature from Dev branch to master.
        a. $ git add -A
        b. $ git commit -m “Comment on changes made.”
2. Check master for conflicts
        a. $ git checkout master
        b. $ git pull
        c. Correct conflicts found
                1. Once conflicts are resolved, commit and make another pull request
                        a. $ git add -A
                        b. $ git commit -am ‘Comment on commit.’
                                - If commit shows long message, type “[esc] : w q”
                        c. $ git checkout master
                        d. $ git pull
        d. When all conflicts are resolved, push changes to Dev branch
                1. $ git checkout “Dev branch”
                2. $ git push —set-upstream origin “Dev branch” 
3. Create pull request on GitHub and commit changes to master
        a. chose Dev branch on Github
        b. click Compare & Pull Request button
        c. update comments and click Create Pull Request button
        d. someone else will typically review the code and when it is approved click Merge Pull Request then click Approve
4. Commit changes on GitHub to local environment files
        a. $ git checkout master
        b. $ git pull
5. Tag you release version
        a. $ git tag -a vX.X.X -m “Release code and new feature’s name”
        b. $ git push —tags
6. Push changes to staging server and test for bugs
        a. $ git push stagingServer master
                1. In order to push to “stagingServer” you first have to create the link
                        a. $ git remote add stagingServer ssh://stf27@198.199.66.116/var/repos/designhamster.us
7. When staging server is running without bugs, push changes to production server
        a. $ git push prodServer master
                1. In order to push to “prodServer” you first have to create the link
                        a. $ git remote add prodServer ssh://stf27@192.241.144.25/var/repos/designhamster.us
