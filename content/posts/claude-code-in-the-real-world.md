+++
date = '2025-09-03T14:43:59-04:00'
title = 'First Impressions: Claude Code in the Real World'
+++

I’d been a little reluctant to try out **Claude Code** for a number of reasons, but I finally did. I was also hesitant to use it on work projects, but I ended up testing it on a greenfield project I needed to complete.  

At work, we have a bunch of aging laptops that need to be disposed of. There are plenty of ITAD vendors out there, but the ones I contacted required a spreadsheet filled with detailed device information. They’d then take that spreadsheet and provide a quote. If you left out details, the quote would be wildly inaccurate.  

So, I leaned on Claude Code to help me build a script that could extract data from 80+ machines and generate a report for ITAD vendors.  

I installed Claude Code, started it up, and ran `/init` in the project directory, which produced a `claude.md` file. From there, I needed a paid account, so I went with the $20/month subscription.  

Initially, Claude Code was super productive. In about 25 minutes, I had a first version of a shell script I could copy onto a USB drive. The workflow was: boot an Apple laptop into recovery mode, plug in the USB drive, open a terminal, and run the script. The script would then write its results back to the USB drive.  

But—it didn’t fully work. It *mostly* worked. That kicked off a painful debugging cycle: Claude wrote the code, I copied it to a USB drive, tested it, reported back what failed, and repeated. I did this for almost two hours.  

About an hour in, I realized I needed to change my approach. I asked Claude to capture the full `ioreg` command output on the USB drive so it could debug more quickly. That was a game changer. Within a couple of hours, I had a script that worked on one test device.  

The first device, from 2018, had an Intel chip. The second, from 2022, ran on Apple Silicon. The script failed again, but with Claude Code’s help I iterated until it worked on the newer device. Of course, when I tested again on the 2018 machine, it broke.  

At that point, I asked Claude to start writing test cases. Since it already had raw data stored on the USB drive, it could do this quickly. With tests in place, I had Claude run them while iterating on code changes. Before long, I had a script that worked on a 2020 device.   

Next, I asked Claude to refactor `claude.md` which I still don’t know what to do with, and to write a `readme.md` which impressed me and felt like I could pass off to someone else for running the script on 80+ macs.

Next, with my collected data on the usb drive, I moved on to the Python code that processed the collected data. This part was more straightforward. After a few iterations, Claude ironed out the bugs and the processing code worked as intended.  

In the end, I had:  
- Spent less than 30 minutes getting most of the code written  
- Spent another ~4 hours debugging, optimizing test runs, improving data collection, and cleaning up the code  
- Likely spent less time overall than if I had written the shell script and Python code entirely by hand  

I’m ready for the next project. 
