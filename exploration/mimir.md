# [Exploration](readme.md) - [mimir](https://github.com/Huginn18/mimir)
This log was started after project started, to be precise after first prototype.


## 19/02/2021
I was experimenting with `emacs` for few days. Trying to set it up for my needs tested my sanity to the breaking point. So after spending 4 days in `init.el` I decided to go back to work on `mimir`, even thinking about doing vim plugin for it.

### So what are the goals?
- quick note taking
- log/journal system
- project management
	- TODOs
	- project Documentation
	- project Estimation
- CV Generator

#### Quicknote taking
`QN` files will be by default stored in `~/config/.mimir.d/quicknote`. `Quick Note` module allows create, edit, delete and search for notes.

#### Log/Journal
`log` handles main log directory and also can handle logs for separate projects. Said that log's commands would be creating/updating logs and search them.

#### Project Management
For quite some time recently I got annoyed with lack of proper tool that I needed to do project management, namely making estimations, todo/kanban and doing documentation. Probably there are some other features I will add along the way but for now this is the list.

#### CV Generator
Creating and sending CV was always a chore for me, so why not use yaml or json and generate nice pdf from it? I need to figure it out later.

- - -

I have big problem finishing projects, every time I take break from a project and come back after some time I need to start everything from scratch. This weird quirk is my OCD/perfectionism taking control. Anyway this time I will take less aggressive approach, I will salvage `git` and `file manager` code and focus on creating proper plan/documentation.


## 20/02/2021
Another insomnia episode! I'm suuuuuuuuure this won' have any effect on how many typos and stupid mistakes I will make... FML

Anywayz I created some documentation for this project. Each module got short description and I think I have good idea where to start. Config and project module sound like a good idea for first try. I Should probably work on that git module, last time I was focused on making this god damn thing working and skipped over some of the commands that might be useful later. I admit I should probably add this idea to the backlog, maybe create gist that I will update later.

My first goal is to create project module and config for it. It is pretty obvious that commands like new, add, delete, clone are a must. I need to think about where to put `manifest` file for this module. It will __probably__ end up in `~/.config/.mimir.d/`. For now this is the most logical choice. Creating multiple, local `manifest` files for data creating modules is something that I need to think about it. It seems like a good solution, after all all projects will be using `git` for versioning and backups. Making one, big `manifest` might cause more problems then it is worth. For sure this approach gives me few extra points in `modularity` approach, you can clone/dowload already existing repo without much of a headache.

## 25/02/2021
I have been occupied with normal life stuff for last couple of days but I'm back! I'm currently working on `pm` module. I thought I had this figured out but well... here I am.

How `new` command should work? After user provides `project name` and `path`app should check if directory exists.

1. If it doesn't create project directory. After that user should decide if they want to init git in the directory.
2. if it does ask user if they want to create project there. If `.git` directory exists skip git init, if it doesn't exist ask user if they want to use git in the project.

That seems simple enough, let's code.

Ok, I forgot about one important thig. Checking `project name` if project already exists user should be asked for a new name.

## 26/02/2021
New command is more or less done... Wait... BRB

Ok, now that I'm done I need to figure out what to do next. I think the best thing to do right now would be to implement `list`, `add` and `delete` in that order. `list` will be a nice easy task, perfect after fuckery that occurred during implementation of `new` action. All of the remaining actions are pretty straight forward. I should be able to implement those in a day or two and start working on `qn` module.

After that I need to take care of autocomplete. Not sure if I can do path autocomplete, I need to do more research.

I'm still not sure how to make other modules compatible with `pm` module. Probably I will need to implement two kinds of commands, `<module> <action>` and `<module>-p <project name> <action>`. This looks like a reasonable and elegant solution which will be easy to implement and use. I still have some time to think about it.

I was also thinking about using gh projects for kanban module. After some research and brainstorming I have decided that as much as possible should be done as plain text, also `gh cli` doesn't support projects and I'm to lazy to experiment with `gh api`.

`pm list` is implemented and I got an idea. It might be nice to see what modules are used in projects. I need to check how to print table in cmd but besides that this should be easy enough.

Currently `pm` module creates `gitHub` repo automatically, I should ask user if they have `gh cli` on their computer and want to use it to put projects on github. That said I need to (at some point) ask user during git init if the repo should be also created on the github. This also means I will need to implement things like `pm add_origin <project name> <url>`, but this is problem for another day.

Ok, for some weird reason autocomplete stopped working on my macbook... partialy, it works perfectly fine in terminal but in python subshell it is gone. So for now I will ignore autocomplete feature.

# 27/02/2021
I started working on `qn` module and realized that I will need another module, namely `config`. `config` will allow user to reinitialize modules and change their settings. I mean this is last thing I'm gonna do since this app is/will be used only by me, but I should do it at some point to make it complete.

# 03/03/2021
With `qn` module done I need to plan work for `qnp` (quicknote with pm support). `qnp` will be nearly the same as `qn` module, only change that I will need to incorporate will be passing reference to `pm` module for easy access to projects list.

This one shouldn't take more than a day of after-hours work. After that I will start working on `log` module and I need to think about `log` and `docs` modules. Generating `ToC` and folder structure for the doc file.

# 05/03/2021
Implementing `qnp` was annoying to say the least, basically copying `qn` methods and adjusting indexes and replacing `self` everywhere. For `log` module I need to find a way to implement `logp` without this whole mess. This will be fun.

I also figured that it will be useful to add `gitIgnore` functionality to the `pm` module, but this is a story for another day.
