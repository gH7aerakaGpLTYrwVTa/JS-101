# JS-101

So basically we want to create a basic Node.js microservice that takes authenticated JSON requests, runs a shell script and returns a JSON response.

Typically, you don't want to write everything in pure Node.js and parse & handle the requests manually - you want to use some framework or library. Our upstream uses Express for this, but it's fairly outdated and too heavy. It is suggested we use Micro, which is small, easy to use and provides basically what we need. https://github.com/zeit/micro#programmatic-use

The second thing is calling shell scripts, which is pretty straightforward too and is well documented in official docs.
https://nodejs.org/docs/latest-v12.x/api/child_process.html#child_process_child_process_execfile_file_args_options_callback

This can then be dockerized and put behind a Tor hidden service.

Start with some basic guide on how to execute shell scripts in Node.js. All you need is some shell script (could be anything, even Hello World for a start) and a node module which executes this script and console.logs what the script returns.

This is a basic guide on how child processes work in Node.js
https://dev.to/ruheni/child-processes-2507

That should not really be needed I think. We can always us child_process.exec instead of child_process.execFile. But we will have to extract specific commands from menus into separate shell scripts.

For example from Whirlpool menu we will need separate shell scripts for stop, start, restart, logs etc. which would either be called from Ronin CLI menu (current state) or from Ronin GUI (node.js microservice)
https://code.samourai.io/ronindojo/RoninDojo/blob/master/Scripts/Menu/menu-whirlpool.sh

execFIle is faster but does not redirect I/O
"Since a shell is not spawned, behaviors such as I/O redirection and file globbing are not supported."

But speed is not our concern since these are really basic scripts, so we can use exec.

## Research URLs:

https://www.youtube.com/watch?v=PkZNo7MFNFg

https://fullstackopen.com/en/

https://pm2.keymetrics.io/docs/usage/pm2-doc-single-page/

https://youtu.be/rtgbaKBhdkk

https://www.freecodecamp.org/news/understanding-recursion-in-javascript/

