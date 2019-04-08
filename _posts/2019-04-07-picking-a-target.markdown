---
layout: post
title:  "Picking a Target"
date:   2019-04-07 18:03:29 -0700
categories: jekyll update
---
Last week I announced that I'm planning to do a video/blog series showing how to find and exploit
vulnerabilities. I hope that by trying this from scratch on a target I've never properly attempted
before, I can share some of what I've learned in the past couple years of vulnerability research training.

I'd also like to show the power of a new fuzzing technique called [structure aware fuzzing][structure-aware-fuzzing].
It's nothing entirely groundbreaking in the realm of fuzzing and security research, but it
combines many great ideas ([quickcheck][quickcheck], [coverage guided fuzzing][coverage-guided-fuzzing], [in process fuzzing][in-process-fuzzing]) in program analysis.

I asked you all about which targets people would find interesting. Thanks to everyone who made a recommendation!
I went ahead and tried to group targets together by category, then I filled them out with a few more options off
the top of my head.

| Type                                               | Target(s) |
|----------------------------------------------------|---|
| Virtual Machines                      | VirtualBox, VMware, Parallels, KVM  |
| Critical Internet Infrastructure | Nginx, sshd, gnupg, openssl |
| Kernels                               | Linux, BSD (PS3, PS4)  |
| Game Consoles                         | 3DS, Switch, PS3, PS4  |
| Scripting Languages            | PHP, Python, Ruby, JS  |
| Console Emulators                  | Project64, VBA, Citra  |
| Mobile OS                     | iOS, Android, AVB2.0  |
| Linux Userland                          | setuid/IPC binaries  |
| Browsers                     | Chrome, Firefox, Edge  |
| Libraries                    | File format parsers  |

Looking at the above list, it's basically all interesting, and I could definitely see demonstrating
some research on all of the above categories. Having done browsers before and currently researching
iOS (as part of my day job), I think simply starting with VMs might be an interesting first step. There have
been many attacks on VirtualBox recently, so there's a good chance I'll be able to find something too.
It has real world value and it's open source, so that makes it possible to show how structure aware
fuzzing works. If that goes well (or doesn't), I'll continue down the list.

I look forward to showing all of you how this goes!

[structure-aware-fuzzing]: https://github.com/google/fuzzer-test-suite/blob/master/tutorial/structure-aware-fuzzing.md
[quickcheck]: http://hackage.haskell.org/package/QuickCheck
[coverage-guided-fuzzing]: https://google.github.io/clusterfuzz/reference/coverage-guided-vs-blackbox/
[in-process-fuzzing]: https://security.googleblog.com/2016/08/guided-in-process-fuzzing-of-chrome.html