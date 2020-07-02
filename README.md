# PyLadies Chapter Websites

## Request a PyLadies chapter repository

To start you'll need to [open an issue](github.com/pyladies/chapter-websites/issues) in this repository providing:

- PyLadies chapter name
- GitHub handle(s) of the chapter organizers
- URL for your custom domain (e.g. seattle.pyladies.com or sea.pyladies.com)

You'll be provided a PyLadies organization repository (e.g. [PyLadies Chicago](github.com/pyladies/pyladies-chicago-website)) and be setup in a PyLadies team with proper publishing permissions.

## What to include in your PyLadies page

Some ideas of content to include on your page:

* Play with the Meetup API to show your upcoming events, number of members, etc
* Play with the Twitter API to show your group's latest tweets
* A chapter blog
* anything!

## Bootstap with PyLadies templates

We've started adding templates into the pyladies organization you can use by clicking the `Use this template` button. Existing templates include:

* [A simple HTML & CSS PyLadies Netlify template](https://github.com/pyladies/netlify-website-template)

If you have a template you'd like to create [here's how](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-template-repository).

## Adding your website to a submodule 

If your website code lives in the main [Pyladies repo](github.com/pyladies/pyladies), you'll want to copy your contents into the new repository that the PyLadies Tech Infra team will create for you. Then in the main [Pyladies repo](github.com/pyladies/pyladies) you will need to open a pull request to remove your website. Follow these instructions to [remove the website](https://github.community/t/how-to-delete-multiples-files-in-github/702/3).

The workflow for adding [your website as a submodule](https://www.vogella.com/tutorials/GitSubmodules/article.html#submodules_adding) is as follows:

```bash
$ cd chapter-websites  # PyLadies repo root
$ git submodule add -b <YOUR_CHAPTER_WEBSITE_REPO_PROD_BRANCH> https://github.com/<YOUR_GITHUB_USER_NAME>/<YOUR_PYLADIES_WEBSITE_REPO>.git chapter_websites/<YOUR_CHAPTER_NAME> # e.g. git submodule add -b gh-pages https://github.com/pyladies/pyladies-chicago-website chicago
$ git submodule init # Adds to .gitmodules 
```

Here is an example [pull request adding Chicago to the repository](https://github.com/pyladies/chapter-websites/pull/2).

If you ever want the PyLadies repo to be fixed at [the most recent commit of your website](https://www.vogella.com/tutorials/GitSubmodules/article.html#submodules_track) you'll need to:

```bash
$ cd chapter-websites/<YOUR_CHAPTER_NAME>  # Your PyLadies website submodule directory
$ git checkout <YOUR_CHAPTER_WEBSITE_REPO_PROD_BRANCH> # Update to whichever branch you use to host your production code on e.g. gh-pages if hosting on GitHub pages
$ git pull 
$ cd ../
$ git add <YOUR_CHAPTER_NAME> # Your PyLadies website submodule directory
$ git commit -m "Update submodule for chapter <YOUR_CHAPTER_NAME> to latest commit on main"
$ git push <YOUR_CHAPTER_WEBSITE_REPO_PROD_BRANCH>
```

## Updating your website submodule

The repository is setup to use a [GitHub action](https://github.com/marketplace/actions/checkout-submodules?version=2.1.1) to checkout submodules defined in the repo any time a push to `main` happens. The setup is specified under `.github/workflows/build.yml`. Or you can see more info under the repo [actions tab](https://github.com/pyladies/chapter-websites/actions).
## Questions?

Reach out to `#project-tech-infra` on the PyLadies Slack!
