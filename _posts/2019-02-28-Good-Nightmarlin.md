---
title: Good Nightmarlin   
categories: Programming
---

# Good Nightmarlin

I was asked today to write a program for a friend (B) who was wondering how to procedurally add objects to his program.
I took a look at what he had written so far... A maze of Visual Basic spaghetti hundreds of lines long greeted me.

{% highlight vb %}

Imports System
Public Sub dothething(ByVal text As String) Handles obj.oneevent
    dotheotherthing(12)
    textbox1.Text += text
End Sub ' yes VB calls this a comment
Public Sub dotheotherthing(ByVal int As Int16)
    MsgBox(int.ToString())
End Sub

{% endhighlight %}

I decided that instead of tinkering with his project, I would create my own with the added challenge of at least
trying to make my code look like his (Spoiler alert: I failed at that second part). I also decided that I would
write my bit in C# and then translate it to VB. What followed was 116 lines of C# code that was surprisingly
effective.

## The Problem

> B: Hey Nightmarlin, I've got a problem  
> $\aleph$: Yeah what is it  
> B: So I want to add a ListBox and some buttons to a form, and then hook the events on so that it adds
whatever is saved in a variable to the ListBox.  
> $\aleph$: Sounds simple enough  
> B: But I haven't really used OOP in my project. At all.  
> $\aleph$: Well it can't be that bad... Can it?  
> B: And my project is in VB  
> $\aleph$: ***dead***

## The solution

### Setting things up

B's solution