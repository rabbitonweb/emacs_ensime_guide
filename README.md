#Scala and Emacs with Ensime. Guide for frustrated IDEA users.

__this gist is under development. once done i will transform it into blogpost__

## 1. Emacs pre-configuration

### 1.1 Install Emacs

`sudo apt-get install emacs`

### 1.2 Get familiar with Emacs (for first-time users)

If you see Emacs for the first time, go through the interactive tutorial. Simply open Emacs and follow the link of the 'Emacs Guidd Tour'. I mean it, do it! It's less ten 1000 lines of text and it will give you basic intro to the tool. 

Further instructions of this tutorial presume that you understand what `C-x C-s` or `M-X` means.

### 1.3 Update your .emacs file

Update ~/.emacs to look like the one available [here](.emacs). If you are new to Emacs, just replace your `.emacs` file with the provided [one](.emacs).

This file contain all configurations needed to make your Emacs a fully fledged Scala IDE on steroids.

## 3. Sbt & Ensime

Majority of "IDE" functionalities are provided by `ensime-module`. That modules requires your project to contain a descriptor file called `.ensime` placed in top-level folder of your project. There are numerous ways to create that file, but the easiest way is to use generator which will do all work for you in a matter of seconds.

Assuming your project runs on SBT, the best way to do it is by using [ensime-sbt](https://github.com/ensime/ensime-sbt) plugin:

### 3.1 Add ensime-sbt plugin

Create and/or update sbt plugins file `~/.sbt/0.13/plugins/plugins.sbt` by adding following line:

`addSbtPlugin("org.ensime" % "ensime-sbt" % "0.2.0")`

### 3.2 Generate .ensime file

In root folder of your project run `sbt gen-ensime`. This will create .ensime file.

## 4. Ensime in Emacs

### 4.1 Open your project

Open one of you project files with Emacs (`C-x C-f`). ScalaMode2 should instantly kick in, providing highlighting for you Scala code. If not done automatically, run it explicitly `scala-mode`

### 4.2 Run Ensime

`M-x ensime`

This will initialize Ensime server and connect it to your Emacs editor. First time your run it, it might take a while to initilize.

Congrats! Now you can use all features provded by both ScalaMode2 & Ensime

## 5. Shortcuts mapping

### 5.1 Idea <-> Emacs equivalents

|   Shortcut                 | IDEA             | Emacs+ENSIME     |
| -------------------------- | ---------------- |  -------------   |
| Save changes               | Ctrl+S           |   C-x C-s        |
| Find Type                  | Ctrl+N           |   C-c C-v v      |
| Find File                  | Ctrl+Shift+N     |   C-c C-v V      |
| Context select             | Ctrl+W           |   C-c C-v .      |
| Recently used files        | Ctrl+E           |   C-x C-b        |
| Variable/method definition | Ctrl+Q           |   C-c C-v i      |
| Jump to definition         | Ctrl+B           |   M-.            |
| List method parameteres    | Ctrl+P           |   ???            |
| List project files         | Ctrl+1           |   F8             |
| Rename                     | Shift+F          |   C-c C-r r      |
| Find usage                 | Alt+F7           |   C-c C-v r      |
| Format file                | Ctrl+Alt+L       |   C-c C-v f      |
| Toggle comment             | Ctrl+/           |   C-c /          |
| Double line                | Ctrl+d           |   C-c d          |
| Import file                | Alt+Enter+select |   C-c C-r t      |
| Errors & warning           | Alt+Enter+select |   C-c C-v e      |
