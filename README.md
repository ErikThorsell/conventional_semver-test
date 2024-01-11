# Conventional Semver: Test

This repository is meant to showcase the usage of my little CLI tool
[Conventional Semver](https://github.com/ErikThorsell/bump-semver-using-conventional-commits).

## Why?

I want to version my code using [Semantic Versioning](https://semver.org)
and find an automated way to update the version every time I merge a new
commit to main.
By writing my commit messages on the format specified by
[Conventional Commits](https://www.conventionalcommits.org/), I can use the
[Conventional Semver](https://github.com/ErikThorsell/bump-semver-using-conventional-commits)
tool to have my build pipeline figure out which _new_ semantic version the
code should get.

## How?

This repository does not contain any meaningful code.
It is taken directly from [Microsoft's getting-started
sample](https://github.com/dotnet/samples/tree/main/core/getting-started/unit-testing-using-dotnet-test)
and is only the bare minimum required to show how the
[Conventional Semver](https://github.com/ErikThorsell/bump-semver-using-conventional-commits)
tool can be used.

The interesting part of this repository is the `.github/workflows` directory,
in which you will find two workflows (one for PRs and one for commits merged
to `main`).
Have a look and copy what makes sense for you.
If you use GitHub Actions too, you can probably copy most of the workflows :)

The [Conventional Semver](https://github.com/ErikThorsell/bump-semver-using-conventional-commits)
tool is written in Python -- and you need to have Python installed in your
build environment in order to use it -- but the tool itself is suitable for
versioning _any_ project which utilises SemVer and Conventional Commits, why
I have chosen to create a dotnet sample project even though I know very little
about dotnet and C#.

## Notes

Make sure you have a `config.toml` file in your repo root, or pass a path to
one to the CLI tool.
You can use the one in this repository to start with.

In order to use the `--local / -l` argument, the repository must have tags.
If you're starting from scratch you can tag your initial commit with `0.0.0`.
If you're introducing
[Conventional Semver](https://github.com/ErikThorsell/bump-semver-using-conventional-commits)
in an existing project you need to make sure the latest tag in the repo is
accurate.

## Important

[Conventional Semver](https://github.com/ErikThorsell/bump-semver-using-conventional-commits)
only look at the latest commit on a given branch.
This means that any PRs made towards `main` must result in one new commit.
You can ensure this is the case either by only allowing squashing, or by only
allowing rebasing (and adding a check which ensures the branch contains only
one commit).
