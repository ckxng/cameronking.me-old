---
layout: page
title: Projects
---

Here is a selection of several _personal_ projects which I have
developed or worked on.

## Pinewood Derby Racing Web
GitHub: https://github.com/ckxng/racingweb

This is a web-based tool for generating race schedules and running
pinewood derbies.  It's written in C++17 with
[Web Toolkit](https://www.webtoolkit.eu/wt).

![Racing Web Video](https://github.com/ckxng/racingweb/raw/main/img/race.gif)

---

## Planning Center Tools

These tools help with volunteer and calendar management using Planning
Center Online.

### Calendar Notify
GitHub: https://github.com/ckxng/pco-calnotify

On a recurring scheudle, this module will watch a Planning Center
calendar for events matching a specific set of labels and will send
notifications via.  email and text message at defined intervals prior
to the event's scheduled time.

### Team Schedule Veiwer
GitHub: https://github.com/ckxng/TeamScheduleViewer

Presents a mobile-browser-friendly and printable schedule for voluneers using
Planning Center Serviecs.

---

## University of Scouting
GitHub (v1 - node): https://github.com/ckxng/universityofscouting  
GitHub (v2 - .net): https://github.com/ckxng/ClassPortal

It's important to have trained leaders in an organization like the
BSA, and 2020 brought some unique challenges.  We took a virtual-first
approach with University of Scouting, and this meant we needed a tool
that provided schedule management, transcript viewing, and degree
printing.

Ben Spellmann and I built a transcript reporting system for scouters
(adult scout leaders) in Longhorn Council. Using this system, scouters
can look up their current schedule and prior registrations through
University of Scouting.

---

## Chat Bots
### SoothBot and Invisible Sun Text Parser
GitHub: https://github.com/ckxng/soothbot  
GitHub: https://github.com/ckxng/invisible-sun-text-processor

This bot is a Discord chat bot, designed to facilitate online sessions
of Invisible Sun RPG.  It includes a dice roller, sooth deck and path
of suns management, and a lookup for various spells and other game
features.

Since the Monte Cook Games license rules do not allow redistribution
of game content, I wrote a text parser which is able to transform the
Invisible Sun text reference files (a Kickstarter reward from the
origninal run) into a structured YAML file which can be read by the
bot.

### Adaptive Card CLI
GitHub: https://github.com/ckxng/acardbot-cli  
NPM: https://www.npmjs.com/package/@ckxng/acardbot-cli

I had a need to post text messages to Microsoft Teams channels, and it
was somewhat challenging to find a simple API that would do what I
needed, especially one that supported environment variables for the
webhook URL (to make integrating with Jenkins and similar CI engines
easier).

This CLI sends text messages and an optional title to teams channels.

---

## Cypher System RPG Character Generator
GitHub: https://github.com/ckxng/cyphergen-web

This simple Heroku-friendly webapp allows GMs to upload the world
parameters for their upcoming campaign, and players may then use a
special link to generate Level 1 characters.  This is helpful, because
Cypher is a system that is designed to be customized, and there is a
lack of online tooling supporting this aspect of the RPG system.

---

## Standard Version CI Action
GitHub: https://github.com/ckxng/docker-standardversion  
Docker Hub: https://hub.docker.com/r/ckxng/standardversion

I needed a convenient way to manage version numbers at merge-time in
JavaScript and Puppet modules, and found that standard-version does
the trick nicely.  While integrating JavaScript modules with
standard-version directly is convenient, it is less convenient for
other other project types which don't already have node_modules
present.

To solve this problem, I built standard-version into a docker
container and published it, for my own use in GitHub Actions and
Jenkins workflows.

---

## 2-Lane Pinewood Derby Judge

I made up two designs for this, one bare bones and one with a little
bit more flash. Both are purposefully simple, and designed using the
MakeCode block editor for the benefit of scouts interested in
programming.

### Feather M0 Express
GitHub: https://github.com/ckxng/pxt-simple-pwd-finish-line-judge

The first iteration is based on an Feather M0 Express, and includes
only the absolute minimum features required to serve as a finish line
judge. The only output is through the single onboard pixel. Blink once
for a win in the first lane, blink twice for a win in the second lane.

### Circuit Playground Express
GitHub: https://github.com/ckxng/pxt-lightup-pwd-finishline-judge

The second iteration is only slightly more complicated, and is based
on the design from the first project. This version uses a Circuit
Playground Express, mainly because it is a popular beginner board and
because of the number of onboard features.

Here, the 10 onboard pixels are used to a greater effect indicating a
win by pointing left or right, and some musical tones are added for
fun. Thanks to the addition of a servo motor, an onboard button now
releases cars to start the race. This allows the program to track the
time of the winning car, though it is only reported by serial.

---

## Pregnancy Timer
GitHub: https://github.com/ckxng/arduino-pregnancy-clock

For one of my kids, we announced my wife's pregnancy by creating a
tiny little count up clock.

The board was an Arduino Nano connected to a real-time clock module
and a SSD1306-based OLED display (the bar accross the top was yellow,
and the remainder of the display was blue). The whole thing was wired
as closely as possible and jammed into a tiny project box which was
almost exactly the right size to hold it all.

The GitHub repo has build photos.

---

## Diceware

My "Hello World" lately, has been to generate diceware passwords.
Here are a few projects where I explored new languages or patterns.

### CLI (Go)
GitHub: https://github.com/ckxng/diceware

I wrote this simply to play around a bit with some specific go
patterns, such as test coverage, concurrency, interfaces, and error
handling. While this tool seems to work fine for me, use it for your
own passwords at your own risk.

    package main
    
    import (
      "fmt"
      "diceware"
      "flag"
    )
    
    func main() {
      var num = flag.Int("d", 8, "number of dice")
      flag.Parse();
      dice := diceware.New()
      if result, err := dice.Generate(*num); err == nil {
        fmt.Printf("%s\n", result)
      } else {
        fmt.Printf("error: %s\n", err)
      }
    }

### Web (JavaScript)
GitHub: https://github.com/ckxng/diceware-web  
Docker Hub: https://hub.docker.com/r/ckxng/diceware-web  
Live: https://ckxng.github.io/diceware-web/public/

Diceware Web is a static, JavaScript site with no external resources
that generates 8-word Diceware passwords.

### API (JavaScript)
GitHub: https://github.com/ckxng/dicewareapi

If you would like to generate a diceware password in the least secure
way possible, feel free to click the links below.

- https://diceware.azure-api.net/api/1/generate
- https://diceware.azure-api.net/api/1/generate?length=8&sep=%5E&upper=1&digit=1

(The initial API call may take up to a few minutes as Azure boots up
the container that hosts the API code. Subsequent calls will be much
faster.)

Please don't actually use these passwords for anything important. I'm
sure Azure is run by perfectly nice folks, and their SSL is plenty
secure... but this is not a safe way to generate passwords.

It's more of an Azure API "hello world" than anything else.

### API (Python Flask)
GitHub: https://github.com/ckxng/diceware-flask

- https://protected-atoll-19813.herokuapp.com/api/v1/passphrase?words=8&sep=~

A second API-based implimentation, equally ill-suited to generate your
personal passwords, demonstrates a single Flask-based web API
endpoint.

### API with Observability (ASP.NET Core)
GitHub: https://github.com/ckxng/diceware-netapi

I wrote this in order to run through the Hello World paces with the
new ASP.NET Core libraries, and to demo metrics observality within a
simple API.

---

## Very Small Web Publishing Tools
GitHub: https://github.com/ckxng/tinysite  
GitHub: https://github.com/ckxng/microsite-php  
GitHub: https://github.com/ckxng/microsite-golang  
GitHub: https://github.com/ckxng/microsite-ruby  
GitHub: https://gist.github.com/ckxng/5fba350bc22e8dd981d7d5a01b5b1daa#file-microsite-cgi

These small webapps wrap static pages in a simple HTML template.  The
TinySite project includes it's on WYSIWYG editor, while the others
expect the user to update the filesystem directly (for example,
via. FTP).  I also wrote a version of this in C, but it has been lost
to the depths of time.

All of these except the golang version run within the context of a web
server.  The golang version runs an embedded web server using
http.Handle.

---

## ECC Docker Repo
GitHub: https://github.com/ecc12/docker

In 2014, I created a somewhat standardized set of Docker images based
on CentOS 6 which I used for both personal and professional
projects. Since then, best practices for Docker have come a long way
and the Dockerfiles I created no longer even build (since the
centos:6.4 base image is no longer available).

Recently, I moved all of these projects to their own repos, with hopes
of someday revisiting them. Until then, you can find them here:
https://github.com/ckxng?tab=repositories. I am leaving the original
repo in place for the time being, as that is where dockerhub is
pulling from.

Ultimately, the community has come a long way since 2014, and these
Docker images are likely no longer of use to anyone anymore.

---

## Other Misc Projects
GitHub: https://github.com/ckxng?tab=repositories

I've tinkered with a lot of different ideas, some good, some bad. For
every repo that's pushed here, there are several more that I never got
around to uploading (usually because I forgot, then later lost the
code).

You will find a mix of finished and unfinished projects (plus a few
forks) in the cobwebs of my GitHub profile.  I tend not to delete
code, no matter how ugly or unfinished.  Half-baked ideas have a way
of being useful years later.  (The file edit dates on these are
especially unreliable, as many of them were pushed to GitHub many
years after they were written.)

