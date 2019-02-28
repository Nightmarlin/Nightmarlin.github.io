---
title: Good Nightmarlin   
categories: Programming
mathjax: true
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

> B: Hey &#8501;ightmarlin, I've got a problem  
> &#8501;: Yeah what is it  
> B: So I want to add a ListBox and some buttons to a form, and then hook the events on so that it adds
whatever is saved in a variable to the ListBox.  
> &#8501;: Sounds simple enough  
> B: But I haven't really used OOP in my project. At all.  
> &#8501;: Well it can't be that bad... Can it?  
> B: And my project is in VB  
> &#8501;: ***dead***

## The solution

### Setting things up

B's solution was written in VB. I do not like VB. Solution: C#.  
The problem was essentially changing the contents of specific controls dynamically. This shouldn't have been
too hard but B had written his project in such a way that the only reference to a control was through
`Me.Controls`, which would be time-consuming to iterate through each time you needed a control. No, you couldn't
even search by name.

I set up a quick mock-up that copied the part of his code that added the controls to his form, this time with an
identifier system:

{% highlight cs %}

public partial class Form1 : Form {
    public Form1() {
        InitializeComponent();
        NextId = 0;
        ToAddPanelsTo = splitContainer1.Panel2;
    }

    private int NextId;                     // Ensure unique names
        
    private readonly Control ToAddPanelsTo;
        
    private void Button1_Click(object sender, EventArgs e) {

        var Pnl = new Panel {               // A panel to add the controls to
            Location = new Point(10 + (NextId * 123), 10), 
                                            // place it so it doesn't overlap with other panels
            Size = new Size(122, 95), 
            Name = $"mypnl{NextId}",     // Unique Id
            BorderStyle = BorderStyle.FixedSingle
        };
			
        var LstBx = new ListBox {           // A listbox to show items
            FormattingEnabled = true,
            Location = new Point(0, 0), 
            Name = $"lb{NextId}",
            Size = new Size(120, 45),
        };
			
        var Btn = new Button {
            Location = new Point(0, 45),
            Size = new Size(120, 25),
            Name = $"btn{NextId}",
            Text = $"Add item to {NextId}'s list",
        };
			
        Btn.Click += ButtonsOnClicked;      // Add handler to the button
            
        LstBx.Items.Add("Default");         // LstBx.Items[0]
   	                                        // Add default item to prevent crashes
       			                              
        LstBx.SelectedIndex = 0;            // Select default item
            
        Pnl.Controls.Add(LstBx);            // Pnl.Controls[0]
        Pnl.Controls.Add(Btn);              // Pnl.Controls[1]
           
        if (ToAddPanelsTo is null) return;  // Don't break please
            
        SuspendLayout();                    // Stop drawing
        ToAddPanelsTo.Controls.Add(Pnl);    // Add to control
        ResumeLayout();	                    // Start drawing
        NextId++;                           // Unique Ids
    }
        
    private void ButtonsOnClicked(object S, EventArgs E) { }
        
}
    
{% endhighlight %} 

I also added a text box called `TxtToAdd`, this is where we will get the input from (simulating B's program)

> B: Wait what does all this do  
> &#8501;: So it's basically what you've written so far, but done in 10 minutes by me.  
> B: Ok then

### Solving the problem

When B showed me his program running, I noticed that he generated an identical set of Buttons for each new List.
I then realised that I could cheat a little, and instead of searching by name, I could find the ListBox by
checking which control was at a point a bit above the button. More than a bit hacky, but because B was consistent
it worked!

{% highlight cs %}

    private void ButtonsOnClicked(object S, EventArgs E) { 
        if (!(S is Button B)) return;
        
        var C = B.Parent.GetChildAtPoint(new Point(B.Location.X + 5, B.Location.Y - 10));
        
        if (!(C is ListBox LstBx)) return;
        
        LstBx.Items.Add(TxtToAdd.Text);
        
    }

{% endhighlight %}

The `GetChildAtPoint` method was guaranteed to work as the button would only spawn beneath the ListBox.  
Unfortunately, the hard part was yet to come, as VB does not have full support for C#'s pattern matching.
This meant translating the code to VB and finding an equivalent method. A quick search on
[Stack OverFlow](https://stackoverflow.com/questions/47495455/vb-net-equivalent-for-c-sharp-7-type-pattern-matching)
lead me to an easy way to cast, and from there it was smooth sailing.

### The end result

{% highlight vb %}

    Private Sub addlist()
        '...
        AddHandler additembutton.Click, AddressOf AddButtonsOnClicked
        '...
    End Sub

    Private Sub AddButtonsOnClicked(ByVal S As Object, ByVal E As EventArgs) { 
        If Not TypeOf S is Button Then
            Return
        End If
        Dim B As Button = S
        
        Dim C = B.Parent.GetChildAtPoint(new Point(B.Location.X + 5, B.Location.Y - 10))
        
        If Not TypeOf C is ListBox Then
            Return
        End If
        Dim LstBx As Button = C
        
        LstBx.Items.Add(TxtToAdd.Text)
        
    }

{% endhighlight %}

This code was relatively simple, yet highly effective. It's also really cheat-y but I didn't have too long
to make it so I'm just going to dismiss that point. I only found out about the `GetChildAtPoint` method by
accident, as I had been working on my coursework the night before and that function popped up (How convenient).  

I'm quite proud of this little bit of code, mostly because of how fast I produced it. But also because I was
able to work with someone to make something work, which is a really good feeling no matter what.

&#9472; &#8501;