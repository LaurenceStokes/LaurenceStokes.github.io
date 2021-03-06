---
layout: post
title: Deobfuscating Javascript Code
tags:
  - security
  - development
---

In software development, obfuscation is the intentional structuring of code to make it difficult to interpret by humans. Typically, this is done to prevent reverse engineering or to conceal the purpose of the code, which is known as __security through obscurity.__ Many malicious malware binaries obfuscate their code to this end – as do javascript malware exploits, which use javascript and the users browser as their delivery mechanism. Not only does obfuscation render reverse-engineering the malware harder, it also makes it more likely to bypass virus scanners. The virus scanner might be looking for certain signatures (evidence of shellcode payloads, for example) that may go unnoticed if the malware is sufficiently obfuscated.

In this blog post I am going to go through and deobfuscate some javascript code, courtesy of [www.scumware.org](https://www.scumware.org), a website dedicated to malware analysis and research.

Although a contrived example (you would never see a password checker like this in ‘real-life’), the basic principles and step-by-step processes remain the same. In fact, I like the scumware.org series of challenges and feel they present a nice introduction to javascript deobfuscation. Finding a password also provides a nice ‘end goal’ to each challenge!

Anyway, with that long preamble aside, let’s jump right into the challenge, which can be found at: [http://www.scumware.org/skill_up/WarmUp_lvl1.scumware](https://www.scumware.org/skill_up/WarmUp_lvl1.scumware)

On loading the webpage, you will be presented with a input form and a password check. First things first, let’s view source. (right click the page: view page source)!

![scumwarePart1](../../images/scumwarePart1.png)

On viewing source, we can see some horribly obfuscated Javascript code which is generating and checking the password. Following a few simple steps we can deobfuscate the code, work out what it’s doing, grab the password and complete the challenge!

[![scumwarePart2](../../images/scumwarePart2.png)](../../images/scumwarePart2.png)

The first step I would advise is beautifying the JavaScript. You can find JavaScript beautifiers online and I used the top result on a Google search for JavaScript beautifier, [http://jsbeautifier.org/.](http://jsbeautifier.org/) The beautified result is below (this time presented in a syntax highlighter code block rather than an image….)

```javascript
var paper = document;
var domain = paper.domain.length;
var flog = eval;
var VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV = new Array;
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[0] = Math;
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[20] = 'Correct! Now go to level 2 by opening file: ';
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[1] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[0].floor;
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[2] = domain;
var fbg = flog;
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[21] = 'bad pass! :(';
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[3] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[1](VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[0].PI) + VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[2];
var fba = fbg;
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[4] = unescape;
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[5] = String.fromCharCode(2 * VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[3] - 1);
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[22] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[4];
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[6] = 'H70H61H70H65H72H2EH77H72H69H74H65H28H22H3CH66H6FH72H6DH20H6EH61H6DH65H3DH27H63H64H33H27H3EH3CH69H6EH70H75H74H20H74H79H70H65H3DH68H69H64H64H65H6EH20H76H61H6CH75H65H3DH27H73H64H73H64H32H27H20H6EH61H6DH65H3DH27H73H64H33H32H27H3EH3CH69H6EH70H75H74H20H74H79H70H65H3DH74H65H78H74H20H6EH61H6DH65H3DH27H63H36H38H27H3EH3CH2FH66H6FH72H6DH3EH3CH61H20H68H72H65H66H3DH27H27H20H6FH6EH43H6CH69H63H6BH3DH27H64H73H73H65H28H29H27H3EH63H6CH69H63H6BH20H68H65H72H65H20H74H6FH20H63H68H65H63H6BH20H70H61H73H73H77H6FH72H64H3CH2FH61H3EH22H29H3B';
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[25] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[22];
fba(VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[25]('%66%62%67%28%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%5B%32%32%5D%28%22%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%42%25%33%33%25%33%31%25%35%44%25%33%44%25%32%37%25%35%36%25%33%34%25%33%32%25%35%36%25%33%37%25%33%32%25%35%36%25%33%36%25%33%39%25%35%36%25%33%36%25%34%35%25%35%36%25%33%36%25%33%37%25%35%36%25%33%35%25%34%36%25%35%36%25%33%36%25%34%34%25%35%36%25%33%36%25%33%35%25%35%36%25%33%35%25%34%36%25%35%36%25%33%36%25%34%33%25%35%36%25%33%37%25%33%36%25%35%36%25%33%36%25%34%33%25%35%36%25%33%33%25%33%32%25%32%37%25%33%42%22%29%29'));
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[7] = 'M66M69M67M28M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M5BM34M5DM28M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M5BM36M5DM2EM72M65M70M6CM61M63M65M28M2FM48M2FM67M2CM20M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M56M5BM35M5DM29M29M29';
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[8] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[5];
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[9] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[4];
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[11] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[31].replace(/V/g, VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[8]);
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[10] = '.scumware';
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[30] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[4](VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[11]);
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[12] = 'H66H75H6EH63H74H69H6FH6EH20H64H73H73H65H28H29H7BH69H66H20H28H66H6CH67H2EH63H64H33H2EH63H36H38H2EH76H61H6CH75H65H20H3DH3DH20H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H5BH33H30H5DH29H20H7BH20H61H6CH65H72H74H28H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H5BH32H30H5DH20H2BH20H66H6CH67H2EH63H64H33H2EH63H36H38H2EH76H61H6CH75H65H20H2BH20H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H5BH31H30H5DH29H3BH20H66H6CH67H2EH68H72H65H66H3DH27H3AH53H27H3BH20H7DH20H65H6CH73H65H20H7BH20H61H6CH65H72H74H28H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H5BH32H31H5DH29H3BH7DH7D';
VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[24] = VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[12].replace(/H/g, VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[8]);
var fig = flog;
var flg = paper;
var fog = fig;
fig(VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[22](VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[24]));
fog(VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[4](VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[7].replace(/M/g, VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[8])));
```

Now we’ve beautified the code, let’s replace the variable with all the VVVVVVVVVVVVVVVV’s to something more readable. We know it’s an array from the line:

```javascript
var VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV = new Array;
```

so I’ve decided to call it VArray (imaginative, I know…)

```javascript
var paper = document;
var domain = paper.domain.length;
var flog = eval;
var VArray = new Array;
VArray[0] = Math;
VArray[20] = 'Correct! Now go to level 2 by opening file: ';
VArray[1] = VArray[0].floor;
VArray[2] = domain;
var fbg = flog;
VArray[21] = 'bad pass! :(';
VArray[3] = VArray[1](VArray[0].PI) + VArray[2];
var fba = fbg;
VArray[4] = unescape;
VArray[5] = String.fromCharCode(2 * VArray[3] - 1);
VArray[22] = VArray[4];
VArray[6] = 'O70O61O70O65O72O2EO77O72O69O74O65O28O22O3CO66O6FO72O6DO20O6EO61O6DO65O3DO27O63O64O33O27O3EO3CO69O6EO70O75O74O20O74O79O70O65O3DO68O69O64O64O65O6EO20O76O61O6CO75O65O3DO27O73O64O73O64O32O27O20O6EO61O6DO65O3DO27O73O64O33O32O27O3EO3CO69O6EO70O75O74O20O74O79O70O65O3DO74O65O78O74O20O6EO61O6DO65O3DO27O63O36O38O27O3EO3CO2FO66O6FO72O6DO3EO3CO61O20O68O72O65O66O3DO27O27O20O6FO6EO43O6CO69O63O6BO3DO27O64O73O73O65O28O29O27O3EO63O6CO69O63O6BO20O68O65O72O65O20O74O6FO20O63O68O65O63O6BO20O70O61O73O73O77O6FO72O64O3CO2FO61O3EO22O29O3B';
VArray[25] = VArray[22];
fba(VArray[25]('%66%62%67%28%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%5B%32%32%5D%28%22%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%42%25%33%33%25%33%31%25%35%44%25%33%44%25%32%37%25%35%36%25%33%34%25%33%32%25%35%36%25%33%37%25%33%32%25%35%36%25%33%36%25%33%39%25%35%36%25%33%36%25%34%35%25%35%36%25%33%36%25%33%37%25%35%36%25%33%35%25%34%36%25%35%36%25%33%36%25%34%34%25%35%36%25%33%36%25%33%35%25%35%36%25%33%35%25%34%36%25%35%36%25%33%36%25%34%33%25%35%36%25%33%37%25%33%36%25%35%36%25%33%36%25%34%33%25%35%36%25%33%33%25%33%32%25%32%37%25%33%42%22%29%29'));
VArray[7] = 'H66H69H67H28H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H5BH34H5DH28H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H5BH36H5DH2EH72H65H70H6CH61H63H65H28H2FH4FH2FH67H2CH20H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H56H5BH35H5DH29H29H29';
VArray[8] = VArray[5];
VArray[9] = VArray[4];
VArray[11] = VArray[31].replace(/V/g, VArray[8]);
VArray[10] = '.scumware';
VArray[30] = VArray[4](VArray[11]);
VArray[12] = 'O66O75O6EO63O74O69O6FO6EO20O64O73O73O65O28O29O7BO69O66O20O28O66O6CO67O2EO63O64O33O2EO63O36O38O2EO76O61O6CO75O65O20O3DO3DO20O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O5BO33O30O5DO29O20O7BO20O61O6CO65O72O74O28O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O5BO32O30O5DO20O2BO20O66O6CO67O2EO63O64O33O2EO63O36O38O2EO76O61O6CO75O65O20O2BO20O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O5BO31O30O5DO29O3BO20O66O6CO67O2EO68O72O65O66O3DO27O3AO53O27O3BO20O7DO20O65O6CO73O65O20O7BO20O61O6CO65O72O74O28O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O56O5BO32O31O5DO29O3BO7DO7D';
VArray[24] = VArray[12].replace(/O/g, VArray[8]);
var fig = flog;
var flg = paper;
var fog = fig;
fig(VArray[22](VArray[24]));
fog(VArray[4](VArray[7].replace(/H/g, VArray[8])));
```
This is starting to look more like some readable javascript already! The first variable, var paper = document is making paper equivalent to the HTML DOM document object ([http://www.w3schools.com/jsref/dom_obj_document.asp](http://www.w3schools.com/jsref/dom_obj_document.asp )). The next variable, domain is paper.domain.length. This is therefore equivalent to document.domain.length (as we know paper IS ‘document’). Bringing up chrome dev tools (crtl-shift-i by default) and going to the javascript console we can get the document.domain.length for http://www.scumware.org/skill_up/WarmUp_lvl1.scumware like so: (we could also count the chars in ‘www.scumware.org’….)

![scumwarePart3](../../images/scumwarePart3.png)

The javascript console will come in useful often during this challenge, so it’s good to get working with it now! Carrying on in a similar fashion, we can start to work backwards with the other array indices and variables to work out what they are doing. I’ve labelled a few in the comments in the code below:

```javascript
var paper = document;
var domain = paper.domain.length; // document.domain.length = 16
var flog = eval;
var VArray = new Array;
VArray[0] = Math;
VArray[20] = 'Correct! Now go to level 2 by opening file: ';
VArray[1] = VArray[0].floor; //Math.floor
VArray[2] = domain; //= 16
var fbg = flog;  //=eval
VArray[21] = 'bad pass! :(';
VArray[3] = VArray[1](VArray[0].PI) + VArray[2]; //(Math.floor(Math.PI) + 16 = 19
var fba = fbg; //= eval
VArray[4] = unescape;
VArray[5] = String.fromCharCode(2 * VArray[3] - 1); // String.fromCharCode(2 * 19 - 1) = 37 = % symbol
```

For the VArray[5] indice, I again used the javasript console in the chrome dev tools to work out what it was. I think the rest of the comments should be self-explanatory, so I won’t go into depth on those. Here’s the dev tools output for String.fromCharCode(37): (We could have also manually looked up the char code on an ascii table such as the one at [http://www.asciitable.com](http://www.asciitable.com/))

![scumwarePart4](../../images/scumwarePart4.png)

Looking through the rest of the code, the next step I personally took was at the last section.

```javascript
var fig = flog; //eval
var flg = paper;
var fog = fig; //eval
fig(VArray[22](VArray[24]));
fog(VArray[4](VArray[7].replace(/H/g, VArray[8])));
```

The last line is equivalent to eval(unescape(VArray[7].replace(/H/g, ‘%’), having worked backwards from what each of the array indices means – fog is eval, VArray[4] is unescape and VArray[8] is ‘%’. The eval() function in JavaScript means execute JavaScript code/expressions and unescape decodes an encoded string. In this case, it’s going to attempt to decode from Hexadecimal (base 16). The replace(/H/g, VArray[8]) means for each instance of ‘H’ in the VArray[7] string, replace H with VArray[8] (the g means global replace). VArray[8] is equivalent to VArray[5], which we have worked out to be the ‘%’ symbol. If we put this in the chrome dev tools we get:

[![scumwarePart5](../../images/scumwarePart5.png)](../../images/scumwarePart5.png)

More obfuscated code! Firstly, Let’s replace the VVVVVVVVVVV back into VArray

```javascript
fig(VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[4](VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[6].replace(/O/g, VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[5])))
```

Becomes...

```javascript
fig(VArray[4](VArray[6].replace(/O/g, VArray[5])))
```

Which we now know what to do with (it’s almost identical to the previous example!). Let’s enter this into dev tools and see what we get:

[![scumwarePart6](../../images/scumwarePart6.png)](../../images/scumwarePart6.png)

Well, this is promising! This is the HTML that generates the form field (remember, paper.write is actually document.write!)

```html
<form name='cd3'><input type=hidden value='sdsd2' name='sd32'><input type=text name='c68'></form><a href='' onClick='dsse()'>click here to check password</a>
```

So, what now? Let’s take a look at this bit of code. It’s all starting to look similar and repetitive now…

```javascript
VArray[24] = VArray[12].replace(/U/g, VArray[8]);
```

Just as before, running this in chrome dev tools gives us:

```javascript
function dsse(){if (flg.cd3.c68.value == VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[30]) { alert(VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[20] + flg.cd3.c68.value + VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[10]); flg.href=':S'; } else { alert(VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV[21]);}}
```

Again, removing the V’s we get:

```javascript
function dsse(){if (flg.cd3.c68.value == VArray[30]) { alert(VArray[20] + flg.cd3.c68.value + VArray[10]); flg.href=':S'; } else { alert(VArray[21]);}}
```

Let’s inspect this for a second. if flg.cd3.c68.value == VArray[30] {do something} else alert(VArray[21]). Well, VArray[21] is the string ‘bad pass :(‘. Therefore I suspect VArray[30] *is* the pass. If what we we enter to flg.cd3.c68 (document.cd3.c68) – the input text form – is equivalent to VArray[30] we have entered the correct pass ELSE we get an alert with ‘bad pass :(‘ We’re getting closer…! The next step I took was to figure out this line of code:

```javascript
fba(VArray[25]('%66%62%67%28%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%56%5B%32%32%5D%28%22%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%36%25%35%42%25%33%33%25%33%31%25%35%44%25%33%44%25%32%37%25%35%36%25%33%34%25%33%32%25%35%36%25%33%37%25%33%32%25%35%36%25%33%36%25%33%39%25%35%36%25%33%36%25%34%35%25%35%36%25%33%36%25%33%37%25%35%36%25%33%35%25%34%36%25%35%36%25%33%36%25%34%34%25%35%36%25%33%36%25%33%35%25%35%36%25%33%35%25%34%36%25%35%36%25%33%36%25%34%33%25%35%36%25%33%37%25%33%36%25%35%36%25%33%36%25%34%33%25%35%36%25%33%33%25%33%32%25%32%37%25%33%42%22%29%29'));
```

Oh god, more unescaping! It’s the same thing again! eval(unescape(….)). The result:

```javascript
VArray[31]='V42V72V69V6EV67V5FV6DV65V5FV6CV76V6CV32';
```

Awesome! Now we can solve this line:

```javascript
VArray[11] = VArray[31].replace(/V/g, VArray[8]);
```

which yields:

```javascript
Bring_me_lvl2
```

Wahey, we’re pretty much done (actually, we technically are, but let’s finish properly for completeness!)

```javascript
VArray[30] = VArray[4](VArray[11]);
```

We know VArray[30] is the password, so that’s simply asking us to unescape(‘Bring_me_lvl2′) – which will return Bring_me_lvl2 which is the password. :D

![scumwarePart7](../../images/scumwarePart7.png)

Now you can try [level 2](https://www.scumware.org/skill_up/Bring_me_lvl2.scumware) on your own!
