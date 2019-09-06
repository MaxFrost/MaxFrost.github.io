---
title: Windows vs Linux - Command Line life
tags:
    - technology
    - powershell
    - windows terminal
    - bash
    - linux
    - windows
    - rant
---

This is me mostly about why it took so long for Microsoft to even begin thinking about catching up to linux in the command line world. I love the recent work that has happened to Powershell, CMD, conhost, and most recently Windows Terminal, but honestly, it feels like it's 10 years too late.

## The Past

Back when I was still in college, I started tinkering with linux, specifically Ubuntu, which was still very young. Why? Compiz. It was pretty, and was way beyond anything I've seen in windows. It got me to install linux for the first time to try it out, and I was astounded by how much reliance on the command line to do anything involving installation. Was that my most favorite thing? No, honestly, I still prefer .exe and .msi over linux package managers, just for sheer simplicity, at least in terms of standalone packages and compatibility.

Concepts like su and sudo, package management and maintaining software packages, all handled exceptionally well within linux. Unfortunately, I hadn't learned much about IT at this time, and didn't realize the implications of what this meant for server management. That would come about 6 years later. Also learned later was that linux for server was command line only, which is a massive reason as to _why_ this terminal first methodology to managing the server was such a big deal.

Server management tooling was all based around terminal. Your process manager, top, works in the terminal, and even has a fancy interface. wget and curl for downloading artifacts directly off of the internet, complete with progress bars and download speed information. ssh, a secure way to connect and work on another machine in a terminal only environment. vi, nano, emacs, and a few other editors all allow powerful code editors all in the terminal. The list goes on and on, and even back in 2004 when I was experimenting with linux for the first time, this methodology was already powering infrastructure as code, because it was trivial for a shell script to completely setup a server for linux, even back then.

Windows on the other hand, was in the dark ages. VB scripting helped a bit, but it was convoluted, and difficult to learn, and there wasn't much tooling to encourage it's usage. Server 2008 was the first Microsoft OS to ship with Powershell, which was microsoft's answer to the tooling present in linux. I have to credit Microsoft here, as this was the start of a long journey to bring windows admins kicking and screaming back into management by command line. The Powershell IDE shipped with this OS and all following operating systems, providing a powerful IDE that was able to simplify editing of scripts. Powershell itself was also centered around verboseness, making it easier to pick up and run with it. `Get-Help` and `Get-Command` are famously the only two functions that you need to be introduced too for powershell to take root.

I have to admit, I likely would have attacked scripting sooner if VB or even BAT had similar capabilities. On the BAT side of things, before the internet, documentation was flakey, and it wasn't capable of complex scripting, operating a lot like BASIC. VB (Visual Basic) on the other hand, was far more powerful, but typically required a background in C#/C++ to crack open, and the downside to it is that it didn't natively run in the shell, it was executed on demand and you were lucky to get output from it.

## The Present

Jumping forward to the present, Powershell is now the defacto way to manage windows servers. It has also created a bit of a rift between old and new guard, as old guard don't like the fact that this new skill set is making them redundant in a bad way. The sheer speed that scripts can handle things over clicking for hours in the GUI alone creates a massive demand. This tooling, as brought up before, is old hat for linux admins, and honestly, they have the right to laugh at us. We were in the wrong. We weren't keeping up with changes in the market, and many admins got caught on the wrong foot.

Knowing only how to managed windows via GUI often meant, in the period from 2010-2018, that you were relegated to desktop and corporate support. Windows servers still had one massive advantage over linux, and that was large scale management and authentication of an enterprise domain. I am aware that linux has similar tooling, but Group policy alone is a huge reason to have a Windows domain controller, at least if your company is running Windows. Most companies run windows for the rank and file, and usually most executives as well. The only major group I'm aware of that doesn't run windows as a primary OS are developers and marketing (MacOS). Windows, as a user desktop, still beats the pants off of linux in user experience and ease of use, and that is because Microsoft has years and years of R&D and feedback polishing their OS. Each version of the user OS is leaps and bounds better than it's predecessor (Vista included, there were other issues with it, but it still improved the platform). Easier for IT to manage, easier for users to backup their documents, more security controls.

Enter Powershell 4.0 and Windows 8.1 (Server 2012). First major version of Powershell that started giving direct hooks into the OS. This is where Powershell found its legs and really started taking off. It finally became feasible to completely manage windows OS 100% from Powershell, not needing to dip into cmd utilities, including hardware and registry management. 5.1 improved further still, and is what I'd like to say the point when powershell started writing tooling to make using the shell easier. Syntax hi-lighting, something not seen on windows before, started showing up with this version of powershell due to PSReadLine. It's a small change, but a very important one. We started seeing new console hosts showing up for windows, to make window management easier, and prettify the shell. Admins and developers were beginning to demand the same tooling from linux on windows, and it was starting to appear.

## The Future

I'm looking forward to what happens going forward. I'd love for the next major version of Server OS to be shell only. Make admins learn their remote tooling if they still need the MMC plugins. Stop the reliance on RDP to manage servers. It's slow, ineffecient. I would also love an in-house package management system. Let us take a pile of .msi files and .exe with run files, drop them in a share, then load up a registry entry to point a machine at the share, and can show things like program updates are available. Make WSUS easier to use, it's a massive, clunky thing that inhales disk space for no good reason. I love where windows patching is now, and look forward to it's continual improvement.

I am aware that chocolatey exists. It's nice to use, but it's not built-in. Creating a feed to use with it is also an exercise in frustration. Even if I had to use chocolatey, there needs to be an easier method to setup packaging for rapid deployment of applications across an enterprise, and that's something package managers excel at, and Windows still doesn't have one.

I'm looking forward to where this goes. Desktop is starting to move over to MDM, which may make GPOs redundant. That might be a good thing, because as powerful as GPOs are, they're hard to manage, upgrade, and force a reliance on Windows domain controller. There's also no change control and not a good way of throttling deployment of a bad change without external tools. MMC plugins are prone to crashing if things are slightly weird, and GPOs are one thing that are still hard to manage with Powershell alone. I would love a path forward from GPO management that gives us the same level of control and simplicity as GPO. DSC is part-way there, but is very verbose and easy to get lost in when managing a lot of individual settings. I am aware that Microsoft is retooling DSC, so that may be the answer when DSC 2.0 shows up.

I could keep going, but honestly, I love windows. I wish I knew linux better, but I see my continued livelihood staying with Windows and working with the cloud. I'm looking forward to what is coming next from Microsoft. Maybe they'll continue to surprize us, or newly disappoint. It's change, one way or another.
