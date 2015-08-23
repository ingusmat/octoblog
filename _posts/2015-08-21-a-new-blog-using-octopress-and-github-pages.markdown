---
layout: post
title: "A New Blog Using Octopress and Github Pages"
date: 2015-08-21T00:09:57+00:00
---
Well, here we are. Meet the new blog, same as the old blog, except wait... this one's *different*! It's so fast!  Hit 
that refresh button -- I dare you.  You'll be back before you know you left. See?  You're already here.  That kind of speed
comes from *static pages*, which means the behind the scenes chugging and churning of code is cut down to a minimum.  None
of that querying databases and putting data into templates.

Now, I love data driven sites as much as the next guy, but sometimes you don't *need* all that extra querying and whatnot.  Wonderfully,
Jekyll and Octopress, let you create and publish a blog using static pages that is, if you have a little command line acumen, Damn near
as easy as setting up a Wordpress site.  

Maybe even easier.  

For real..

### First Things First: Vagrant!
This step is totally optional, but if you're like me, you like being able to completely scrub what you were doing and start over from scratch,
even if you had it about 92% correct.  Vagrant will spin you up a virtual machine to do your work on, and when you're done with it, or you want
to work on something else, you just /halt/ the vm, and it's gone until you spin it up again.

The other advantage to using Vagrant for development is that even though Jekyll and Octopress use a relatively tiny number 
of dependency gems, it's good to keep that stuff isolated.  I'm not going to go much further into it.  If you want to learn
more, the documentation on [vagrantup.com](http://vagrantup.com) is exceptionally clear and simple.  Download Vagrant there if you want to
use it.

### All Right, Let's Get Started.
Open up a terminal.  (If you're using os x or linux.  I've never used Vagrant on windows, but I'm sure it's possible.  It's probably in the
docs on the Vagrant site.)  Okay.  Navigate to the place you want to store your working files.  It does not have to be in any sort of LAMP or webserver
directory.  Vagrant will take care of that.  Just cd to where you want it to be.  Like this: (Obviously, don't type the '$' prompts.) 

    $ cd ~/Sandbox/Blog/
    $ vagrant init myBlogName
    $ cd myBlogName

Now, 'vagrant init' will have put a file in that directory named Vagrant file.  Open that baby up either
in the console there or with your favorite editor, and replace the contents with the following:

    Vagrant.configure(2) do |config|
      config.vm.box = "lazygray/heroku-cedar-14"
      config.vm.network :forwarded_port, host: 4567, guest: 4000
    end

Yup.  Nice and simple.  You can switch out the box if you want.  I had lazygray/heroku-cedar-14 already downloaded from some rails work
I was doing.  There are lots of other boxes (virtual machine setups) at [the Vagrant Cloud](https://atlas.hashicorp.com/boxes/search?utm_source=vagrantcloud.com&vagrantcloud=1).

Now save that and do `$ vagrant up`. That'll spit out a ton of generated text telling you all the cool stuff Vagrant is doing.  Sweet.
When it's done, enter `$ vagrant ssh` and you'll be in your brand new virtual machine.  Go ahead and `$ cd /vagrant`.  That will get you
to the shared directory, and THAT is where we'll build our blog.  Do an `$ ls -la`.  Yep!  It's the same directory on your *real* machine that you were in when you
did your vagrant up.

### Okay, Vagrant's working, let's set up Octopress.
And this part is to be continued.  Aw, snap!  Don't worry.  I'll finish it later.  I gotta go to bed and get ready for work, man. 



