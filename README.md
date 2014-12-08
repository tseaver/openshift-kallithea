Kallithea on OpenShift
=========================

NOTE: THIS QUICKSTART IS NOT FUNCTIONAL YET. THIS NOTICE WILL BE REMOVED ONCE IT IS OPERATIONAL.

``Kallithea`` is a fast and powerful management tool for Mercurial_ and GIT_
with a built in push/pull server, full text search, pull requests and
code-review system.

Kallithea was forked from RhodeCode in July 2015. This quickstart was forked from the RhodeCode kickstart in December 2015.

More information can be found at https://kallithea-scm.org/

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a DIY application. If you may add a PostgreSQL cartridge.

    rhc app create kallithea diy-0.1 postgresql-9.2

Add this upstream Kallithea quickstart repo

    rm -R diy .openshift misc README.md
    git remote add upstream -m master https://github.com/ncoghlan/openshift-kallithea.git
    git pull -s recursive -X theirs upstream master

Push the repo upstream to OpenShift

    git push

Head to your application at:

    http://kallithea-$yourdomain.rhcloud.com

Default Credentials
-------------------
<table>
<tr><td>Default Admin Username</td><td>admin</td></tr>
<tr><td>Default Admin Password</td><td>changethis</td></tr>
</table>

To give your new Kallithea site a web address of its own, add your desired alias:

    rhc app add-alias -a kallithea --alias "$whatever.$mydomain.com"

Then add a cname entry in your domain's dns configuration pointing your alias to $whatever-$yourdomain.rhcloud.com.

