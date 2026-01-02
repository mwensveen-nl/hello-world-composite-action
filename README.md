# GitHub Action

This repository contains a number of actions that can be used by projects that use java and maven.
You can use these actions in your .github/workflows actions.


## Build

This action builds the maven project using `mvn package`.
Input: 
 - java-version: java version to use; defaults to 25.
 - github-token: (optional) If the projects needs to use dependencies from a private github maven repository, than this is the token that allows access.  In the pom.xml you need to define a repository with id `github`.

Example usage:

    - uses: mwensveen-nl/github-action/build@main
      with:
        java-version: '25'
        github-token: ${{ secrets.MAVEN_REPO_READ }}

##  Create PR

This action creates a PR to merge a feature or bugfix branch to the main branch. On every commit to the branch, this action checks if a PR already exists. If not, it is created.

Example usage:

    - uses: mwensveen-nl/github-action/createPR@main

## Deploy

This action builds the project and (if successful) deploys the artifact and sets a tag on the git repository.

Input: 
 - java-version: java version to use; defaults to 25.
 - github-token: the token needed to deploy the artifact to a github maven repository. In the pom.xml you need to define a repository with id `github` in the distributionManagement section.

Example usage:

    - uses: mwensveen-nl/github-action/deploy@main
      with:
        java-version: '21'
        github-token: ${{ secrets.MAVEN_REPO_WRITE}}


## Tag

This action set a tag on the git repository after a successful build.

Input: 
 - java-version: java version to use; defaults to 25.
 - github-token: (optional) If the projects needs to use dependencies from a private github maven repository, than this is the token that allows access.  In the pom.xml you need to define a repository with id `github`.

Example usage:

	- uses: mwensveen-nl/github-action/tag@main
	  with:
	    java-version: '25'
	    github-token: ${{ secrets.MAVEN_REPO_READ}}


