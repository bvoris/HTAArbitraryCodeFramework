# HTA Arbitrary Code Execution Framework
Framework for a Hypertext Application designed to execute arbitrary code.<BR />
Created By: Brad Voris<BR />
<img alt="GitHub followers" src="https://img.shields.io/github/followers/bvoris?style=social">
<img alt="GitHub User's stars" src="https://img.shields.io/github/stars/bvoris?style=social"><BR />
<img alt="GitHub" src="https://img.shields.io/github/license/bvoris/HTAArbitraryCodeFramework">
<img alt="GitHub commit activity" src="https://img.shields.io/github/commit-activity/m/bvoris/HTAArbitraryCodeFramework">
<img alt="GitHub All Releases" src="https://img.shields.io/github/downloads/bvoris/HTAArbitraryCodeFramework/total">
<img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/bvoris/HTAArbitraryCodeFramework">
<img alt="GitHub language count" src="https://img.shields.io/github/languages/count/bvoris/HTAArbitraryCodeFramework">
<img alt="GitHub issues" src="https://img.shields.io/github/issues/bvoris/HTAArbitraryCodeFramework">
<img alt="GitHub top language" src="https://img.shields.io/github/languages/top/bvoris/HTAArbitraryCodeFramework">

## What is HTA?
An HTML Application (HTA) is a Microsoft Windows program whose source code consists of HTML, Dynamic HTML, and one or more scripting languages supported by Internet Explorer, such as VBScript or JScript. The HTML is used to generate the user interface, and the scripting language is used for the program logic. An HTA executes without the constraints of the internet browser security model; in fact, it executes as a "fully trusted" application.<BR />

The usual file extension of an HTA is .hta.<BR />
Source: https://en.wikipedia.org/wiki/HTML_Application<BR />

## What is this "framework"?
Currently HTAs are still supported on Windows 11 and lower environments.<BR />
This means a crafty Hypertext Applicaiton can be used to steal information from your machien disgusing itself as a legitimate application. This makes it difficult to detect.<BR />
The framework itself is a set of files.<BR />
The HTA itself which is labeled as hack.hta<BR />
The fake "search" feature.<BR />
The malicious script or executable code.<BR />
PIE.js which we use for backwards compatability for CSS (we will get more on that on the secret sauce)<BR />

## What does it look like?
<IMG SRC="https://github.com/bvoris/HTAArbitraryCodeFramework/blob/main/screenshots/Google.com.png?raw=true" height="90%" width="90%">
 
## What's the secret sauce?
There are several components which equate out to the secret sauce<BR /><BR />
FIRST:<BR />
.HTA extension<BR />
This tells Windows that the file is a Hypertext Application.<BR /><BR />

SECOND:<BR />
<HTA:APPLICATION <BR />
     APPLICATIONNAME="HackToolz"<BR />
     SCROLL="yes"<BR />
     SINGLEINSTANCE="yes"<BR />
     SysMenu="yes"<BR />
><BR />
 This is the application information that is in the header of the HTML to preload and execute.<BR /><BR />

THIRD:  
'meta http-equiv="X-UA-Compatible" content="IE=8;IE=7;" /' <BR />
 This meta tag forces Internet Explorer to load the content in IE-7/IE-8.<BR /> This also reduces that security capability and allows arbitrary VBScript to run in the browser via my fourth ingredient secret sauce.<BR /><BR />

FOURTH:<BR />
<BR />

## Connect with me at

<a href="https://twitter.com/HMInfoSecViking?ref_src=twsrc%5Etfw"><IMG SRC="https://github.com/bvoris/bvoris/blob/master/twitter.jpg" WIDTH=10% HEIGHT=10% ALIGN=LEFT></a>

<a href="https://www.linkedin.com/in/brad-voris" target="_blank"><IMG SRC="https://github.com/bvoris/bvoris/blob/master/linkedin.png" WIDTH=10% HEIGHT=4% ALIGN=RIGHT></a>

<BR /><BR />
<BR /><BR />

<A HREF="https://www.victimoftechnology.com">Victim Of Technology<A />
<BR /><BR />
<A HREF="https://www.cyberforgesecurity.com">Cyber Forge Security, Inc.<A />
<BR /><BR />
