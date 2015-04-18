# TMVE 0.1
Automatically exported from code.google.com/p/tmve

## topic model visualization engine

## 
* * *

### Demo

#### a browser of 100K Wikipedia articles

[This browser](http://www.sccs.swarthmore.edu/users/08/ajb/tmve/wiki100k/browse/topic-list.html) was produced by using the results of running [David Blei's LDA-C](http://www.cs.princeton.edu/~blei/lda-c/) on 100,000 Wikipedia articles to find 50 topics.

* * *

### Tutorial

#### to produce a browser similar to the demo above

First, download build [LDA-C](http://www.cs.princeton.edu/~blei/lda-c/) and run it on a dataset. For the above demo, the command looked something like:

./lda set 1/50 50 settings.txt wiki/100K/word_count.dat seeded wiki-100k-lda

Next, the LDA data will need to be processed and put into a database; for this purpose, use the database generator provided in the _lib_ folder. Again, for the demo, the command to run the generator would be as follows.

python generate_db.py 100k_wiki_db wiki/100K/word_count.dat wiki-100k-lda/final.beta wiki-100k-lda/final.gamma wiki/100K/vocab.dat wiki/100K/dmap.dat

This can take a while for large datasets. As a short-cut, a demo 1k database is included in the _demo_ folder, entitled _1k_demo_db_.

Finally, TMVE needs to be run with a project file, which specifies what database and template to use. Templates control how the data is displayed; in this case, a basic browser is produced. The included project file _wiki_project_demo.tmv_ is set up to run with the demo database.

The command to run TMVE with the demo project is fairly simple:

python src/tmve.py demo/wiki_project.tmv

Or, for more information as the script runs, the verbose mode is helpful:

python src/tmve.py -v demo/wiki_project.tmv

For the demo project, you will need to be connected to the Internet while TMVE generates the document pages as it must pull content from Wikipedia. When this is done, you should have a local browser (in the demo directory) like the demo above, but a little smaller.

* * *

### Making Changes

#### adapting to other datasets and other topic model types

Creating a new template will allow you to view your data in an alternative fashion. To do so, take a look at the BasicBrowser template included in the TMVE source download.

To use another dataset, you will need to change the way documents are displayed. This is currently hard-coded into the _BasicBrowser.py_ file, in the function <font class="code">get_doc_display</font>.

To try different topic models, only the database generator needs to be changed. Depending on how the output differs from LDA-C, the work to do this may be minimal.

* * *

Allison J. B. Chaney • 2010 • Princeton University
