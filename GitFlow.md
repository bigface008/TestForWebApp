# Introduction of GitFlow

On January 05, 2010, Vincent Driessen put a new article named [A Successful Git Branching Model](http://nvie.com/posts/a-successful-git-branching-model/) onto his personal blog. After that, the main idea of the article, GitFlow, became the most popular model dealing with branching and merging.

## What is GitFlow?
GitFlow is a model for effective development of software. It consists of the main branches and supporting branches. To start with, let's call our central repo origin. 

### Main branches

The central repo holds two main branches with an infinite lifetime:

- master
- develop

The master branch at origin should be familiar to every Git user. Parallel to the master branch, another branch exists called develop.

![](/images/pic1.png)

When the source code in the develop branch reaches a stable point and is ready to be released, all of the changes should be merged back into master somehow and then tagged with a release number. How this is done in detail will be discussed further on.

### Supporting branches

GitFlow uses a variety of supporting branches to aid parallel development between team members, ease tracking of features, prepare for production releases and to assist in quickly fixing live production problems. Unlike the main branches, these branches always have a limited life time, since they will be removed eventually.
The different types of branches we may use are:

- Feature branches
- Release branches
- Hotfix branches

Feature branches tracks the development of features. Release branches perpare for production releases. Hotfix branches fix the live production problems.We will walk through them in the part of how to use GitFlow.

## Why should we use GitFlow?

Because it is simple and effecient. 

>While there is nothing really shocking new to this branching model, the “big picture” figure that this post began with has turned out to be tremendously useful in our projects. It forms an elegant mental model that is easy to comprehend and allows team members to develop a shared understanding of the branching and releasing processes.

This is part of Vincent Driessen's article. The practice turn out to be a greate success in dealing with the problem we meet during the development of software and teamworking. 

As we know, due to the convenience of git, branching and merging have become a daily routine of software development. Besides, the evolution of social network, microservice and  cloud computing demands higher standard of teamwork and effeciency. So it is necessary to find a model which completes those task fluently. And GitFlow is among the best choices.

## How can we use GitFlow? 

#### Feature branches

May branch off from: develop 

Must merge back into: develop 

1. Creating a feature branch

`$ git checkout -b myfeature develop`

2. Incorporating a finished feature on develop 

`$ git checkout develop`

`$ git merge --no-ff myfeature`

`$ git branch -d myfeature`

`$ git push origin develop`

![](images/pic2.png)

#### Release branches

May branch off from: develop

Must merge back into: develop and master

1.Creating a release branch

`$ git checkout -b release-1.2 develop`

`$ ./bump-version.sh 1.2`

`$ git commit -a -m "Bumped version number to 1.2"`

2.Finishing a release branch

`$ git checkout master`

`$ git merge --no-ff release-1.2`

`$ git tag -a 1.2`

`$ git checkout develop`

`$ git merge --no-ff release-1.2`

`$ git branch -d release-1.2`

![](images/pic3.png)

#### Hotfix branches

May branch off from: master

Must merge back into: develop and master

`$ git checkout -b hotfix-1.2.1 master`

`$ ./bump-version.sh 1.2.1`

`$ git commit -a -m "Bumped version number to 1.2.1"`

![](images/pic4.png)







