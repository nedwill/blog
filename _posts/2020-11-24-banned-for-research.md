---
layout: post
title:  "Getting Banned for Security Research"
date:   2020-10-24 21:22:00 -0700
categories: jekyll update
---
*Note that this post does not reflect the opinions of my employer nor my colleagues, and I conducted this research on my own time.*

About a week ago, Activision banned me from Call of Duty: Modern Warfare/Warzone (2019) for attempting to study the security of its networking code.

As a user, I think I ought to be able to research vulnerabilities when I may be at risk. Multiplayer games do a great deal of networked communication, both between the user and the vendor (e.g., for fetching stats or user configuration) and between users (when hosting a private game or communicating over the microphone). A user should be able to trust that playing the game in a typical manner should not lead to a compromise. Some initial background research revealed that other security researchers, like me, have reverse engineered previous iterations of the game to discover and report vulnerabilities. There is already a precedent for both the validity of the security risk and Activision’s demonstrated openness to vulnerability reports [[1](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20817), [2](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-10718), [3](https://github.com/momo5502/cod-exploits/tree/master/huffman), [4](https://github.com/momo5502/cod-exploits/tree/master/steam-auth)].

To do this research, I needed to reverse engineer the networking code in the game’s executable, as this would allow me to review the code for memory corruption vulnerabilities. Unfortunately, the executable was heavily obfuscated, and IDA was unable to analyze it. Therefore, I had to dump the unobfuscated code from the memory of a running game process. I believe it was at this point where the developers flagged me as a suspected cheater. I did two things to try to read memory from the process while I was in the main menu to avoid affecting any players. First, I attached WinDbg, and the game exited (probably the flagging event). Next, I tried pausing the process before dumping memory from it. I simply dumped an image of the game from memory in the main menu and then exited normally.

After spending a few days reviewing the binary, I decided that the binary was so large and unwieldy to deal with that I would table the project for a later date. But unfortunately, I was banned about a month later, losing over a year of progress on my account. The ban saddens me on a personal level as I’ve reconnected with family and friends from throughout my life playing this game during the pandemic. But more importantly, this sends a clear signal: this research is not welcome. I believe I had a reasonable expectation that it would be. I had done similar work during a CTF, where I reverse engineered and fuzzed CS:GO without ever risking a ban. Valve regularly accepts bug reports, and in one case, they paid a researcher $18000 for [reporting a vulnerability](https://hackerone.com/reports/470520).

Cheating is one of the biggest threats to the experience of gamers online. I understand that the developers shoulder an impressive burden in preventing cheat development and use. They need to leverage a variety of signals to detect cheat development and use. I’m guessing that because they may not have seen security researchers reviewing their platform before, they interpret any attempt to reverse engineer as a sign of malicious behavior. No typical player would attach a debugger to the game, and therefore they probably assume they don’t need much more evidence beyond this to issue a ban. Let me be clear: at no point did I intend to develop or use a cheat, and at no point did I manipulate any aspect of the game for another player or even myself. To this day, I don’t know what exactly caused the ban, and there’s no process to appeal it. What if using a reversing tool as part of my job gets me flagged? This fear is in the back of my mind for all games with anti-cheat, not just Warzone.

Where do we go from here? Obviously, I’d appreciate it if Activision unbanned my account. More importantly, I think they should provide a way for security researchers to have a place in the ecosystem and by carving out exemptions for security research and establishing a point of contact (even a bug bounty) for vulnerability reports. The task of managing cheaters on the PC platform is growing both in difficulty and [controversy](https://www.pcgamer.com/the-controversy-over-riots-vanguard-anti-cheat-software-explained/) - and I believe that Activision should join Valve and other publishers in fostering a symbiotic relationship with security researchers rather than an adversarial one. Together we can make games safer from cheaters and malicious users alike.