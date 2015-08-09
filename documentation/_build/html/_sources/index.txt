.. Pygeminfo documentation master file, created by
   sphinx-quickstart on Sun Aug  9 02:47:17 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Pygeminfo's documentation!
=====================================


.. toctree::
   :maxdepth: 2


.. title:: Pygeminfo

:Author:   **Taiwo Kareem**
:Contact:  taiwo.kareem36@gmail.com


Contents:

Pygeminfo is a python package for displaying statistics about Rubygems. Its equivalent is the Rubygem called `geminfo`. It allows you to see several information about a Gem like *Name, Author, UserID, Secure Hash Algorithm, Key, Total downloads, Latest version, total gems owned by author, gem's release date* etc.


Importing and Usage
--------------------

.. code::

	from pygeminfo.gems import * 
	# from pygeminfo.gem import Stats
	# from pygeminfo import downloads()
	#etc.

	#Another way is to do
	import pygeminfo.gems
	# then use it like
	pygeminfo.gems.Stats("gemname")



MODULES --> gems
-----------------

Contains a class **Stats** that takes one argument **Gem name** and has seventeen methods to display several information.

Stats
^^^^^^

* name() --> returns gem name.
* authors() --> return gem's Author names.
* total() --> return gem's total download for all versions.
* latest() --> return Gem's total download for latest version.
* latestversion() --> returns gem's latest version.
* info() --> returns gem's description.
* licenses() --> returns gem's licenses.
* metadata() --> returns gem's metadata.
* sha() --> returns gem's Secure Hash Algoruthm 256 Checksum.
* projectURL() --> returns gem's project URL.
* gemURL() --> returns gem's URL.
* homepage() --> returns gem's dedicated website.
* wikiURL() --> returns gem's wiki URL.
* docURL() --> returns gem's documentation URL.
* mailURL() --> returns gem's mailing list URL.
* sourceURL() --> returns gem's source-code URL.
* bugURL() --> returns gem's bug tracking URL.

as well as seven other methods.

Example
"""""""

.. code::

	sample = Stats("somegem")

	print ("Gem Name: {}".format(sample.name()))
	print ("Overall Gem download: {}".format(sample.total()))
	print ("Latest version download: {}".format(sample.latest()))
	print ("Latest version: {}".format(sample.latestversion()))
	print ("Authors: {}".format(sample.authors()))
	print ("Description: {}".format(sample.info()))


Result
""""""

.. code::

	Gem Name: somegem
	Overall Gem download: 1,051,815,917
	Latest version download: 1,328,554
	Latest version: 4.1.0
	Authors: Daffy Duck
	Description: somegem has been built to train Daffy duck and co for heroic acts.
	


Methods
^^^^^^^^

**gemversions** takes one argument (*gemname*). It shows the gem version, author, build date, total downloads and secure hash algorithm of all the versions of a gem.

Example
""""""""

.. code::

	# Argument is gem's name
	gemversions("somegem")


Result
"""""""

.. code::

	Gemname: somegem-1.0.1
	Authors: Daffy Duck
	Built on: 2006-12-15
	Total downloads: 2504
	SHA 256 Checksum: 795942397a9854969cd5b9a9e68c7138f7111e5ae96b6166099b952d68006b4a

	Gemname: somegem-1.0.0
	Authors: Daffy Duck
	Built on: 2006-10-13
	Total downloads: 2310
	SHA 256 Checksum: 593f193c332355264c289ff2065ea2e91d1095888d50147a7fdee41fad058b9e



**usergems** take one argument *username/userID*. It shows some information (total gems, gems, overall downloads, gem's latest version and overall downloads) about all the gems of a specified user.


Example 1
""""""""""
**With Username**


.. code::

	# Argument is username or ID
	usergems("daffy")		# With user name
	


Result 1
"""""""""

.. code::

	Username: daffy
	Total gems: 2

	Gemname: ducks 
	Overall downloads: 483 
	latest version: 0.0.1 
	Latest version downloads: 483 

	Gemname: ducklings 
	Overall downloads: 1,443 
	latest version: 0.0.2 
	Latest version downloads: 493


Example 2
""""""""""
**With ID**


.. code::

	usergems("12345")		# With user ID

Result 2
""""""""

.. code::

	User ID : 12345     
	Total gems: 1

	Gemname: ducks 
	Overall downloads: 203 
	latest version: 0.0.2 
	Latest version downloads: 100 



**owner** takes one argument *gemname*. It displays some information (total gems, gems, overall downloads, gem's latest version and about all the gems of the specified user.

Example
"""""""

.. code::

	# Argument is gem's name
	owner("ducks")


Result
"""""""

.. code::
  
	Gemname: ducks 

	User ID: 12345
	Username: daffy
	Email Address: daffy@ducks.quack



**search** takes `one to three` arguments. The `first` and `compulsory one` being the *query parameter*. It also takes another 	`optional argument` being *page number* and a third being the *amount* of items to be displayed from a page. The default is `30 items`.

.. note::

	The optional parameters helps you to refine your search result.


Example 1
""""""""""

**One argument**


.. code::

	# Argument is gem's name, optional--> (page number , amount to show)
	search("man")			# page 1 of query result


Result 1
""""""""
.. code::

	Gem Name: batman
	Author: Bruce Wayne
	Latest Version: 0.2.4
	Total Downloads: 47,342

	Gem Name: spiderman
	Author: Peter Parker
	Latest Version: 1.20.0
	Total Downloads: 742,616

	Gem Name: superman
	Author: Clark Kent
	Latest Version: 0.6.0
	Total Downloads: 457,848

	... and so many more results


Example 2
"""""""""

**Two arguments**


.. code::

	search("at", 5)		# page 5 of query result
	

Result 2
"""""""""

.. code::

	Gem Name: rat
	Author: Jerry Mouse
	Latest Version: 0.2.4
	Total Downloads: 47,342

	Gem Name: cat
	Author: Tom Cat
	Latest Version: 1.20.0
	Total Downloads: 742,616

	Gem Name: fat
	Author: Humpty Dumpty
	Latest Version: 0.6.0
	Total Downloads: 457,848

	... and so many more results up to 30


Example 3
""""""""""
**Three arguments**

.. code::

	search("at", 5, 1)	 # first results on page 5 of the query result

Result 3
"""""""""

.. code::

	Gem Name: rat
	Author: Jerry Mouse
	Latest Version: 0.2.4
	Total Downloads: 47,342



**latestgems** takes *zero* arguments but an *optional argument* (`amount to show`) can be passed to it. The default items to show is `50`. It shows the latest gems on the `Rubygems` website.

.. note::

    The optional parameter helps you to refine your search result.

Example 1
"""""""""

**No arguments**


.. code::

	# Optional --> (amount to show)
	latestgems() 		# latest gems
	

Result 1
""""""""

.. code::
	
	Gem Name: newruby
	Author: Ruby Miner
	Latest Version: 0.1.0
	Total Downloads: 4
	Description: A simple Ruby miner who loves gems.

	Gem Name:newgold
	Author: Gold Digger
	Latest Version: 1.0
	Total Downloads: 10
	Description: A simple gold digger who needs nothing but money.

	Gem Name: newdiamond
	Author: Diamond Thief
	Latest Version: 0.0.3
	Total Downloads: 17
	Description: Gold gold and gold is precious

	... and so many more results --> Up to 50


Example 2
""""""""""
**One argument**

.. code::

	latestgems(1)		# first results of latest gems


Result 2
""""""""

.. code::

	Gem Name: newruby
	Author: Ruby Miner
	Latest Version: 0.1.0
	Total Downloads: 4
	Description: A simple Ruby miner who loves gems.


**updatedgems** takes *zero* arguments but an `optional` argument(*amount to show*) can be passed to it. The default items to show is `50`. It shows the recently updated gems on the Rubygems website.


.. note:: 

   The optional parameter helps you to refine your search result.


Example 1
""""""""""
**no arguments**

.. code::

	# Optional --> (amount to show)
	updatedgems() 		# recently updated gems


Result 1
"""""""""

	Gem Name: newruby
	Author: Ruby Miner
	Latest Version: 0.1.1
	Total Downloads: 4
	Description: An update to a simple Ruby miner who loves gems.

	Gem Name: newgold
	Author: Gold Digger
	Latest Version: 1.1
	Total Downloads: 10
	Description: An update to a simple gold digger who needs nothing but money.

	Gem Name: newdiamond
	Author: Diamond Thief
	Latest Version: 0.1.3
	Total Downloads: 17
	Description: An update to Gold gold and gold is precious

	... and so many more results --> Up to 50


Example 2
"""""""""

.. code::

	updatedgems(1)		# first results of updated gems


Result 2
"""""""""

.. code::

	Gem Name: newruby
	Author: Ruby Miner
	Latest Version: 0.1.1
	Total Downloads: 4
	Description: An update to a simple Ruby miner who loves gems.


**downloads** takes `no argument`. It shows the total downloads of all Rubygems till date.

Example 
""""""""

.. code::

	# No optional argument
	downloads()



Result
"""""""

.. code::
	
	Total Rubygems Downloads till date: 5,709,711,396


Other Information
-------------------

help on using this package is included in the `examples folder`.

For more help information please see examples in the package or checkout its `documentation <http://www.pythonhosted.org/pygeminfo>`_ at http://www.pythonhosted.org/pygeminfo/
	
Requirements
------------

* Any version of python

Download
---------

Download and install using:

.. code::

   pip install pygeminfo

   
Issues
-------

There are some `unicode encoding` issues on python 2 but it works fine on Python 3. It also works on Python 2 but sometimes, the errors arise so its better and advisable to use it on Python 3. Furthermore, you may need to do

.. code::
   
   pip install json 
   pip install requests


if it doesn't come with your python package


Acknowledgements
----------------

**All glory belongs to God and praise be to his holy name.**


Contact
-------

If further information or help is needed, feel free to contact me on my email at taiwo.kareem36@gmail.com
This is still in a test mode please if any error or bugs is found, feel free to contact the developer and give details


Contributing
-------------
Bug reports and pull requests are welcome on `Github <http://github.com/tushortz/pygeminfo>`_. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the `Contributor Covenant <http://contributor-covenant.org/>`_ code of conduct.

License
--------
The python package is available as open source under the terms of the `MIT License <http://mit-license.org/>`_.

Copyright © 2015 Taiwo Kareem