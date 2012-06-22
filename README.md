What is this?
-------------

This is a fork of the [RT Import plugin](http://www.redmine.org/plugins/rt_import) for Redmine.  I am not the original author.

I started with the tarball for 0.6.1 (2011-10-17), and made some changes to suite a [ChiliProject](https://www.chiliproject.org/) install that was trying to import an XML/MPP export from [Gantter](http://gantter.com/).

Among the changes are:

- Enable traceback logging of save errors (it kept failing silently for some objects so I changed all `@obj.save` calls to `@obj.save!`).

- No longer try to import projects/sub-projects: just import everything into one project (identified by the "prefix" when uploading the file) and build a tree of issues/sub-issues.

- No longer try to import resources / users.  Issue assignment must be done manually after import.

Installation
------------

Run from command line:

	cd /path/to/vendor/plugins
	git clone git://github.com/awbush/redmine_rt_import.git
	rake db:migrate:plugins RAILS_ENV=production

Then restart redmine/chiliproject.  For example, if you're using Apache w/ Passenger you might run:

	sudo service apache2 restart
