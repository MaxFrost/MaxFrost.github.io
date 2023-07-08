---
title: Why now James?
tags:
    - life
    - technology
date: 2019-09-05 21:04:44
comments: true
---

## Introduction

First off, an introduction. My name is James Maxson, and I'd like to think I'm somewhat decent at PowerShell and doing IT. I've been working with PowerShell since 2012 when I actively started using it at my job to manage Office 365. My script writing and mastery of the language has only improved since then.

I'd taken it on myself to start this blogging journey to help isolate when/where/why I learned things. My goal is if I learn something that took a while for me to grok, to write it down and pass it on to others with the hope that they too can learn from my mistakes and misadventures.

Another goal is to _always_ have some sort of code in every single post. If it's a slice of life post, there might not be any code, but generally, this blog is going to be powershell centric until it has no reason to be.

And for your amusement, a quick function that replicates the password information from `net user $user /domain` but as a powershell function!

``` powershell
function Get-ADUserPWStat {
    param(
        [string]$User
    )
    Import-Module ActiveDirectory
    $UserParams = @{
        SamAccounntName = $User
        Properties = @(
            "PasswordLastSet"
            "msDS-UserPasswordExpiryTimeComputed"
            "lastlogondate"
            "lockedout"
            "lastbadpasswordattempt"
        )
    }
    Get-ADUser @UserParams |
        Select-Object name,
            PasswordLastSet,
            @{
                Name="PasswordExpires"
                Expression={
                    get-date $_."msDS-UserPasswordExpiryTimeComputed"
                }
            },
        lastlogondate,
        lockedout,
        lastbadpasswordattempt
}
```
