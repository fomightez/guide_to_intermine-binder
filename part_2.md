# Leveling up your Intermine Skills with Jupyter Notebooks backed by Binder: Part II

This is meant to continue from [part I of this guide](https://github.com/fomightez/guide_to_intermine-binder) and to be used with active Binder instances launchable from [here](https://github.com/fomightez/intermine-binder).

-----

Here is the amazing thing about [Part I](https://github.com/fomightez/guide_to_intermine-binder/blob/master/README.md): the critical step to making the Intermine web service useful via the binder session you launched, was the fact I simply added `intermine` as a line in my [`requirements.txt`](https://github.com/fomightez/intermine-binder/blob/master/requirements.txt).

Because of that, when I pointed [the mybinder.org](https://mybinder.org/) site at the repository that included that [`requirements.txt`](https://github.com/fomightez/intermine-binder/blob/master/requirements.txt) file, it launched the session witih the ability to use Python to communicate with Intermine. I added a few other useful items on top of [the example available here](https://github.com/binder-examples/requirements); however, that was all that was really required. If at this point that brief explanation suffices for background on what is going on behind-the-scenes, you can try another practical demo next, and then possibly choose to read more about the Binder system later. However, if you have an urgent need to understand how the active session able to communicate with Intermine is being established momments after you click the `launch` button, skip down to [here](#mybinderorgbinder-and-github) and return to the next section for the next demo of using Intermine via the Jupyter notebook later.

Let's take on a more in-depth example making use Intermine via Binder, and see how we can take advantage of Python along the way.

Practical demonstration II: more realistic use of Intermine via Binder and taking advantage of Python
----------------------------------------------

COMING SOON.

-----

Before concluding, I am going to cover some of the technical aspects briefly and offer options to those wanting to pursue various options further. Feel free to skip to [the 'Where to next?' section below](https://github.com/fomightez/guide_to_intermine-binder/blob/master/part_2.md#where-to-go-next) though as the next few sections are intended more for those looking to consider further aspects touched on earlier, mainly about the underlying tech.

----

MyBinder.org(Binder) and Github
--------------------------------

The Binder system is an impressive combination of [a great number of technologies and resourceful and helpful developers](https://bids.berkeley.edu/news/binder-20-has-arrived). Most of the technologies you don't need to know anything about to take advantage of the Binder system because it is mostly behind-the-secenes stuff the end-user should not need to engage. Think of the man and machinery behind the curtain in the Wizard of Oz. Currently, the computational infrastructure is hosted on Google Cloud Platform with funding from the Moore foundation. One of the key components of the underlying machinery is `repo2docker`. `repo2docker` is able to take a git repository and convert it into an image of a 'container', which is a lightweight, isolated virtualized system-level environment that starts fast. When you 'launch' a binder if the details of what to spin up, a.k.a. a built image, is already available it will make an active session based on the details specified when that image was made and let you access the active form of it from your browswer. If what is to be launched is new to the Binder system it will first build what it will need to the launch the 'system' detail in the git repository, and then proceed on to launch the active container with the active Jupyter environment set up as specified in the details of the repository. We will come back to this build step later. 

Of course, I am only touching on some of the basic details of Binder here and not any of the additional underlying tech. Power users can seek out the resources I highlight at the end of this section to delve further. Chances are good that the repository I have set up is enough to get you started if you want to use Python and Intermine. The [`requirements.txt file`](https://github.com/fomightez/intermine-binder/blob/master/requirements.txt) has some of the main popular modules, and you can always use `!pip install` followed by the module name in a cell within an active notebook to install additional modules. In fact, if you think that launchable Binder is good enough for now and you are satisfied that you know enough about the Binder system for your current needs, feel free to skip right on to the next section. Advanced users will most likely to set up their own Binder repository to specify certain modules to already be there upon launch. For example, in the enivronment set up to run Intermine code, I have added the conversion from Python 2 to 3 that was used in the previous page (at least in early 2018) and that is beyond what is a default Jupyter set up. You may wish to get started by forking [my repository](https://github.com/fomightez/intermine-binder) or just copy and adapt the `requirements.txt` file using those off [examples of working Binders](https://github.com/binder-examples/) as a basis.

Additionally, one of the important aspects Binder targets is reproducibility. Along those lines, you can lock in the versions of the software in order to better insure that everything will run as it did at the time the repository was made. Because this example repository was set up to use the most recent versions of the dependencies in order to hopefully keep it as current as possible, I didn't do that there; however, that is just one of the many other reasons advanced users may want to set up their own repositories with custom `requirements.txt` settings, or use `enviroment.yml` configuration files as illustrated [here](https://github.com/binder-examples/conda) and [here](https://github.com/binder-examples/python-conda_pip), to control the environment in the launched binder.  All you need is a Github account to customize your environment, and you can simply edit these two types of files directly in the Github web browser interface. While many users needs should be met through use of custom `requirements.txt` or `enviroment.yml` configuration files, apt-get and Docker can also be used by advanced users to specify the details of the container that ultimately will be launched. 

A `postBuild` file in the repository can be used to insure the running container does any last steps needed or retrieves data from remote sites to make your repository lightweight and more flexible. A limitation that novices may encounter is that making use of these necesitates the use of git because the file has to be executable, and I have found editing it directly in Github's browser interface seems to break this ability in a way that is not obvious as the file will still be tagged as executable in Github's browser interface. 

Once you have a repository in Github, you can go to [MyBinder.org](https://mybinder.org/) and place the link to it in the form on that page. That page will also provide the pastable text for making `launch buttons` buttons you see; however, as they are just markdown text, you can edit the text for any button to point at your own repository. The first launch can take several minutes. Typically, once built launches only take a few seconds.  You can monitor the progress using the `show` toggle on the right side of the bar below the large spinning icon.

Every time you subsequently change a repository associated with launchable Binders, the image build process on Binder will need to be re-run.

Additional resources and examples concerning Binder can be found below:

- [mybinder.org](https://mybinder.org/)

- [Introducing Binder 2.0 — share your interactive research environment](https://elifesciences.org/labs/8653a61d/introducing-binder-2-0-share-your-interactive-research-environment) - November 30, 2017 | eLife 

- [Binder 2.0 announcement by Berkeley Institute for Data Science](https://bids.berkeley.edu/news/binder-20-has-arrived)

- [Binder group featured on Google Cloud Platform podcast](https://www.gcppodcast.com/post/episode-122-project-jupyter-with-jessica-forde-yuvi-panda-and-chris-holdgraf/)

- Nature article: [Make your data dance with interactive visualization tools: TOOLBOX  30 JANUARY 2018](https://www.nature.com/articles/d41586-018-01322-9) by Jeffrey M. Perkel, features Binder along with several other tools.

- Good summary list of resources for getting started with Binder can be found in [this twitter thread](https://twitter.com/betatim/status/997736804320202752).

- [Examples of Working Binder Implementations](https://github.com/binder-examples/)

- [Binder 2.0, a Tech Guide](https://blog.jupyter.org/binder-2-0-a-tech-guide-2017-fd40515a3a84)

- [Binder / mybinder.org Documentation](https://mybinder.readthedocs.io/en/latest/)

- [Gathering place for Binder developers and users](https://gitter.im/jupyterhub/binder)

- [repo2docker](http://repo2docker.readthedocs.io/en/latest/)

- Even [more from what proceeded this guide](https://gist.github.com/fomightez/4aae844937a4aa6e22f555757a81b201)


Limitations of Binder
--------------------

There are general limitations to consider when considering how and when to use the Binder system. Many of them are covered in [sections found here](https://mybinder.readthedocs.io/en/latest/faq.html#how-much-memory-am-i-given-when-using-binder). I will highlight some of the most important.

- Ephemeral. Treat the session as temporary and save immediately to your local machine anything useful you do. The notebook itself can be saved to your local machine and uploaded again to a later active session. The Jupyter Dashboard with a familiar file upload/download interface can be accessed any time by pressing on the Jupyter logo in the upper left of an running notebook. You may get warnings about leaving a notebook page to go to the dashboard, but if you run `Save` you should be fine to switch.

- You individual session isn't public, however ...the [documentation warns](https://mybinder.readthedocs.io/en/latest/faq.html#can-i-push-data-from-my-binder-session-back-to-my-repository), "You shouldn’t do anything on mybinder.org that you wouldn’t mind sharing with the world!". BinderHub can be delployed locally to serve more specialized needs, see [here](https://mybinder.readthedocs.io/en/latest/faq.html#what-can-i-do-if-mybinder-org-does-not-meet-my-needs).

- Limited in memory and size.

    >"just a note that if it[,the particular launchable binder] gets really popular, mybinder.org will start reporting "too many users on this repo" errors it's capped at 100 active users per repo, I believe (simultaneous active users)"

Understanding how to adapt the [examples of working binder implementations](https://github.com/binder-examples/) can be daunting for those not used to the Jupyter ecosystem, but hopefully you've seen that might not be necessary at the start. Additionally, some of the limitations for those not used to dealing with git have already been touched upon in the last section. At a different end of the spectrum,
some would argue Jupyter notebooks, and by extension running them on Binder, aren't the answer for real 'Big' data or meet all the needs for open data: see a related discussion [here](https://twitter.com/BioMickWatson/status/985491549197930496) and [here](https://twitter.com/David_McGaughey/status/985550038117044225).

------


Conclusion
----------

Intermine's web interface is great. I work on YeastMine and can accomplish a great deal via the web interface. For example, I often want to know more details on a list of genes where the systematic ID is provided. The standard name and a short description usually let me know a little more. I can easily convert and such information by starting on the `Lists` tab of YeastMine. Eventually though, you'll hit tasks that you do often and would benefit by automation or you'll have something you cannot quite do easily via the browser. Or perhaps you have a long series of steps you are accomplishing and want to document the process you took from point A to B clearly in a Jupyter notebook.

However, it can be daunting to set up your environment on your computer to make things work well. And maintain that. And if you set it up on one computer, what happens when you are on another computer or want a colleague to be able to do the tasks or tasks while you are using your computer?  Or what if you are going to be doing this task dozens of times in the next two weeks but might not do it again for another six months? Will it still work on your computer?  Or you want to share this with others not physically near you? Or you want to fully document your steps for drafting a publication and know reviewers are going to be able to test those steps?  Hopefully, you've seen that the Binder system is a useful step towards addressing a lot of that. Additionally, it is a great tool for teaching biologists (and even others) how to start and integrate many different computational resources into their efforts.

The underlying Intermine database may return different results over time and so 'reproducibility' always comes with slight qualifiers; however, the Binder system is a significant step towards addressing the common "it works on my computer" barrier. Or the problem that 'it' doesn't work on my computer because of troubles with installations, dependencies, and concerns about messing up other things, sometimes known collectively as "[dependency hell](https://medium.com/@Marianattestad/a-treatise-on-making-circos-plots-from-genomic-data-7ff496849e0)".




Where to go next?
-----------------

Using the tools intoduced here you could try and integrate your use of Intermine sites with more Python, and maybe learn Python more. The Jupyter environment provides a really useful glue to do this and integrate with the Bash shell even. You can pass variables and data back and forth easily between the shell and Python within the Jupyter environment giving you the ability to integrate running other command line programs. For examples of that see the advanced Python demonstrations associated with launchable binders for BLAST [here](https://github.com/fomightez/blast-binder) or PatMatch [here](https://github.com/fomightez/patmatch-binder).

The now "binderized" Intermine-Python tutorials presently available [here](https://github.com/yochannah/intermine-ws-python-docs/) cover interacting with Intermine more with Python directly.





