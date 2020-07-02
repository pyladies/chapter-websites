# PyLadies Chapter Websites

## How to setup your own domain/site:

You are welcome to create your own location's webspace,
e.g. seattle.pyladies.com or sea.pyladies.com, or even
www.pyladies.com/seattle etc. If you want your own URL, tell me:

1. what you want your URL to be.
2. make a pull request for your site, adding your website as a submodule to the repository in a directory with your chapter name e.g. `chicago` for PyLadies Chicago
3. when you want it to go live.

Some ideas of content to include on your page:
* Play with the Meetup API to show your upcoming events, number of members, etc
* Play with the Twitter API to show your group's latest tweets
* A chapter blog
* anything!

We've started adding templates into the pyladies organization you can use by clicking the `Use this template` button. Existing templates include:
* [A simple HTML & CSS PyLadies Netlify template](https://github.com/pyladies/netlify-website-template)

If you have a template you'd like to create [here's how](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-template-repository).

-your friendly administrator.  

## Moving your existing website to a submodule 

If your website code lives in the main [Pyladies repo](github.com/pyladies/pyladies), you'll want to copy your contents into the new repository that the PyLadies Tech Infra team will create for you. Then in this repository you'll need to:

```bash
$ cd pyladies  # PyLadies repo root
$ rm -rf <YOUR_CHAPTER_NAME>
$ git rm --cached -rf <YOUR_CHAPTER_NAME>
```

You can now complete the steps in `Adding your website as a submodule`.

## Adding your website to a submodule 

The workflow for adding [your website as a submodule](https://www.vogella.com/tutorials/GitSubmodules/article.html#submodules_adding) is as follows:

```bash
$ cd chapter-websites  # PyLadies repo root
$ git submodule add https://github.com/<YOUR_GITHUB_USER_NAME>/<YOUR_PYLADIES_WEBSITE_REPO>.git -b gh-pages chapter_websites/<YOUR_CHAPTER_NAME> # e.g. git submodule add https://github.com/pyladies/pyladies-chicago-website -b gh-pages chicago
$ git submodule init # Adds to .gitmodules 
```

If you ever want the PyLadies repo to be fixed at [the most recent commit of your website](https://www.vogella.com/tutorials/GitSubmodules/article.html#submodules_track) you'll need to:

```bash
$ cd chapter-websites/<YOUR_CHAPTER_NAME>  # Your PyLadies website submodule directory
$ git checkout gh-pages 
$ git pull 
$ cd ../
$ git add <YOUR_CHAPTER_NAME> # Your PyLadies website submodule directory
$ git commit -m "Update submodule for chapter <YOUR_CHAPTER_NAME> to latest commit on main"
$ git push
```
