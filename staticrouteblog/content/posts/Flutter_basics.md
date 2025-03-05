+++
date = '2025-03-04T20:05:45-06:00'
title = 'Flutter basics'
+++
 >**Note**: If you've worked with statically typed languages nothing about Dart should be too shocking and it should be pretty readable. After having spent the last 15 years or so working in really "fast" scripting languages like Powershell and Python, it has taken me some getting used to:
```Dart
<Dart> Can? Seem (Very<Verbose>);
```
<br>
I recently had the opportunity to learn the basics of DartLang and the Flutter framework. As always, it can be difficult to find guides that are the right technical depth, either they are geared towards total beginners, or seasoned Devs. There are two concepts I think are most important to understand when starting to work with Flutter are.

- *State management*

**State management** was a wholly new concept to me. Most of the code I've done up to this point takes data in at run time, performs functions, and reports or saves data as output. The most user interaction I've had to account for was a switch-style CLI menu. When I was researching Flutter builds I kept seeing State Management packages getting thrown around and realized it was a concept I'd have to tackle, but wasn't exactly sure what aspects of my app would require it. If you're a seasoned Mobile developer you'd have a gameplan for state management at scale before starting your build. If you're me, you start making those decisions at the moment you try to write your first widget. Every UI component in Flutter is a Widget, and every Widget inherits from one of two base classes: Stateless or Stateful.




- *Class inheretence*