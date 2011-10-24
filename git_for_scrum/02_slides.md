
!SLIDE bullets incremental transition=fade
_and now finally_
# Git workflow #
## shamelessly forked from @porras:
<http://www.slideshare.net/sergio.gil/a-git-workflow>
but different

!SLIDE bullets incremental transition=fade
# Git for Scrum #
_at least, 'our way'_

* Features (demo)
* Bugfixes (instant)

!SLIDE bullets incremental transition=fade
# Features #

* One branch for story/backlog item
* Branch from __stable__
* Merge with __master__
* Demo
* Deploy

!SLIDE bullets incremental transition=fade
# Features #

* One branch for story/backlog item

!SLIDE commandline small incremental transition=fade
# Feature (start) #

    $ git checkout stable
      Switched to branch 'stable'

    $ git status
      # On branch stable
      nothing to commit (working directory clean)

    $ git pull origin stable
      From git.my_server.com:my_project
      * branch            stable     -> FETCH_HEAD
      Already up-to-date.

    $ git checkout -b fancy_feature
      Switched to a new branch 'fancy_feature'

!SLIDE commandline small incremental transition=fade
# Feature (start) #

Develope and pass your tests
    $ git diff
      # check we dont include anything wrong, debug, traces...

    $ git commit -m "Ultrachilling fanciness"
      [bundler 0401de4] Ultrachilling fanciness
      X files changed, Y insertions(+), Z deletions(-)

    $ git checkout master
      # On branch master
      nothing to commit (working directory clean)

    $ git pull origin master
      From git.my_server.com:my_project
      * branch            master     -> FETCH_HEAD
      Already up-to-date.

!SLIDE commandline small incremental transition=fade
# Feature (merge) #

    $ git merge fancy_feture
      100% (4/4) done
      Auto-merged file.txt
      CONFLICT (content): Merge conflict in file.txt
      Automatic merge failed; fix conflicts and then commit the result.

      <<<<<<< HEAD:file.txt
      Hello world
      =======
      Goodbye
      >>>>>>> 77976da35a11db4580b80ae27e8d65caf5208086:file.txt

    $ git add file.txt
    $ git commit
      # no -m, automatic message

    $ git push origin master
    $ testing_deploy

!SLIDE transition=fade

## What just happened? ##

![Bug](merge.png "Merge")

!SLIDE code
# Branching #
<pre style="font-size:130%">
                                                  +  production deploy
                                                  +          |
stable--\--\--------------------------------------+-------/--|------stable
         \  \                                     +      /
          \  \---fancy_feature--\                 +     /
           \                     \                +    /
            \------master---------\--|------------+---/
                                     |            +
                                testing deploy  DEMO
</pre>

!SLIDE bullets small incremental transition=fade
# What makes a Bug? #

* Prevent normal application use
* Show wrong or misleading data
* Destroy data
* Impact severely on user experience

!SLIDE bullets incremental transition=fade
# Bugs #

* One branch for BUG
* Branch from __stable__
* Merge with __stable__
* Check
* Deploy

!SLIDE commandline small incremental transition=fade
# Bug (start) #

    $ git checkout stable
      Switched to branch 'stable'

    $ git pull origin stable
      From git.my_server.com:my_project
      * branch            stable     -> FETCH_HEAD
      Already up-to-date.

    $ git checkout -b bug_killing
      Switched to a new branch 'bug_killing'

    $ $EDITOR lib/wadus/foo_bar.rb

    $ git commit -m "Bug killing Argh!!"
      Updating e53ac7a..670e353
      Fast forward
      lib/wadus/foo_bar.rb |   16 +++++++++++++++-
      1 files changed, 15 insertions(+), 1 deletions(-)

!SLIDE commandline small incremental transition=fade
# Bug (finish) #

with clean workspace
    $ git checkout stable
      Switched to branch 'stable'

    $ git merge bug_killing
      Updating 361303d..670e353
      Fast forward
      lib/wadus/foo_bar.rb |   16 +++++++++++++++-
      1 files changed, 15 insertions(+), 1 deletions(-)

    $ git push origin stable
      Counting objects: 7, done.
      Compressing objects: 100% (4/4), done.
      Writing objects: 100% (4/4), 407 bytes, done.
      Total 4 (delta 2), reused 0 (delta 0)
      To git@github.com:wadus/my_repo.git
         361303d..f2cd831  master -> master

    $ production_deploy

!SLIDE code transition=fade
# Branching #
<pre style="font-size:130%">
                                               production deploy  +  production deploy
                                                       |          +          |
stable--\--\----------------------\----------------/---|----------+-------/--|------stable
         \  \                      \--bug_fixing--/               +      /
          \  \---fancy_feature--\                                 +     /
           \                     \                                +    /
            \------master---------\--|----------------------------+---/
                                     |                            +
                                testing deploy                  DEMO
</pre>


!SLIDE bullets smaller incremental transition=fade
# More #

<http://git-scm.com/documentation>

<http://gitimmersion.com>

<http://gitready.com/>

<http://gitref.org/>

<http://cheat.errtheblog.com/s/git>

__<http://www.ndpsoftware.com/git-cheatsheet.html>__

<http://www-cs-students.stanford.edu/~blynn/gitmagic/intl/es/index.html>(es)

