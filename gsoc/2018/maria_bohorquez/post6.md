# Remodelling ReadTheDocs so all the Docs are in the same place

For questions or help for other GSoC students (or anyone really!), contact me at gabriellabohorquez@gmail.com or robocomp.team@gmail.com  

## Learning about how to configurate ReadTheDocs

ReadTheDocs (the org) has a pretty extensive documentation section [[1](https://docs.readthedocs.io/en/latest/)], where they never say how to make your docs as nice as theirs :unamused:.

These are Open Source Projects, so clearly the solution to this was searching the original code for their documentation!

After a little bit (a lot) of searching and investigating I found [this](https://github.com/rtfd/readthedocs.org/blob/master/docs/index.rst).

![ReadTheDocs Github](https://i.imgur.com/5sW9wTA.png)

And voila! In the `index.rst` file (in the /docs folder in the repo) you create these little groups of files so your docs will look like this:

![ReadTheDocs Docs](https://i.imgur.com/acFTlSm.png)

So, on we go to experiment with Robocomp's docs. Here is the `index.rst`:

![Our changes](https://i.imgur.com/NciTyzS.png)

And this should about fix our docs like ReadTheDocs.

**Comment**: If this doesnt work it's probably the ../file in the path. I didn't know where ReadTheDocs goes looking for the files, so I wrote the path starting from /docs ang going to /doc.
