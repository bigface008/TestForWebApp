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

![](images/pic3.png)

#### Hotfix branches

May branch off from: master

Must merge back into: develop and master

![](images/pic4.png)







