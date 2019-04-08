# NTTKR Goes Forth - Analysis

1. Haha I forgot I had this blog. Oops
2. I recently decided I needed to learn React. And Electron. So I've come up with a little something to do using both! Meet NTTKR

## Purpose
Create an app built in Electron with React and Typescript to help me understand how React works.
The goal here is NOT to reinvent the wheel, but to learn new skills with a new framework.

> I do not claim ownership of any products referenced herein. Reference to them is for demonstrative and educational purposes.

## Analysis

A good idea is to look at pre-existing products, and identify their Key Features, Key Drawbacks and Potential Improvements.

Examples of note-taking applications include:

- Google Keep - Notes and Lists
- Evernote - Organizer, Planner for Notes & Memos
- Microsoft OneNote

### Key Features

#### [Google Keep - Notes and Lists](https://play.google.com/store/apps/details?id=com.google.android.keep)

>![Google keep demo](/assets/images/2019-04-08/keep_demo_1.png)
>![Google keep demo with note opened for editing](/assets/images/2019-04-08/keep_demo_2.png)
> All personal information has been edited out

Google Keep is Google's flagship notemaking app.
It has a large variety of features and rich integration with the Google product family.
The main features of the app have been identified below:

- Take Notes (duh)
- Add content
  - Checkboxes
  - Colour
  - Drawings
  - Images
  - Links
  - Reminders
  - Tags
  - Text
  - Title
  - Voice Recordings
- Save notes
  - Edit saved notes
  - Online and Offline Storage
- Manage notes
  - Archive
  - Collaborate
  - Copy
  - Delete
  - Pin to Top
  - Reorder
  - Share

Feature evaluation

| Feature | Description | Keep it? Why / Why not? |
|---------|-------------|------------------------|
| Checkboxes | Add to-do list checkboxes to the note on each new line | Yes. To-do lists are good to help keep track of what has / hasn't been done |
| Colour | Change note background colour to a selected colour | Yes. Allowing for categorisation by colour allows for greater accessibility |
| Drawings | Add a hand-drawn image to the note | No. This is a PC app, and it is unlikely that many users will have a drawing peripheral |
| Images | Add a saved image to the note | Yes. This provides a visual aid to help with notemaking |
| Links | Add a hyperlink to the note | Yes. This allows the user to save sites and such into their notes |
| Reminders | Add a timed reminder to the note that will alert the user about it at the selected time | Maybe. PC applications can display notifications, but they may not be as useful as on mobile platforms|
| Tags | Add a Tag / Label to the note | Yes. Grouping notes by tag is similar to grouping by colour, but allows for easy searching and filtering |
| Text | Add text to the note | Yes (obviously). The most basic feature of a note-making app would be the ability to, well, make notes |
| Title | Add an informative title to the note | Yes. This would also allow for sorting / searching / filtering by the user |
| Voice Recordings | Add a voice recording to the note | No. Voice libraries are a pain to work with. Maybe another time |
| Saving Notes | Store the note to the device | Partially. Google Keep uses online backups and offline storage systems to store notes. I would only offer an offline storage solution |
| Edit saved notes | Add / Edit / Remove any content type from a note freely | Yes. If a user makes a mistake when making the note, then they should be able to edit it |
| Online Storage | Save a backup in the [Cloud](https://cloud.google.com/storage/) (Yes, that kind of Cloud, not [this kind of Cloud](/assets/images/2019-04-08/the_cloud_sky.jpg). Or [this kind of Cloud](/assets/images/2019-04-08/the_cloud_wifi.jpg)) | No. Supporting cloud storage would require me to write my own cloud storage API or use a third party one. Which probably costs money |
| Archive Notes | Move a note to a secondary storage area | Yes. This allows unused / outdated notes to be kept for reference |
| Collaborate | Allow multiple users to edit a note | No. this application is designed for offline use, so allowing multiple editors is not likely to be necessary |
| Copy Notes | Make a copy of a note and store it | Yes. Copying notes with slight changes is probably useful. Probably. |
| Delete Notes | Remove a note from all storage areas. Permanently | Yes. |
| Pin Notes | Pin a note to the top of the list | Yes. This allows users to make their most important notes more prominent |
| Reorder Notes | Change the order and position of notes on screen | Yes. This allows users to customise their layouts to their preference |
| Share Notes | Send a note from one user to another | Maybe? Implementation dependent. |


Woah that's a lot of features. I don't expect to add them all, but I'll take my favourites and roll with them.


#### [Evernote - Organizer, Planner for Notes and Memos](https://play.google.com/store/apps/details?id=com.evernote)

> ![Evernote demo](/assets/images/2019-04-08/evernote_demo_1.png)
> Again, personal details have been removed

Unlike Google Keep, Evernote has two versions: A free version and a paid version.
The paid version boasts additional features and such but as my application is going to be free to use, I will not be evaluating those.

- Make Notes
- Add Content
  - Document Formatting
  - Text Effects
  - Files / Attachments
  - Checkboxes
  - Lists
  - Tables
  - Code Blocks
  - Fonts
  - Headings
- Save Notes
  - Edit Saved Notes
  - Online & Offline
- Manage Notes
  - Copy
  - Move
  - Archive
  - Delete
  - Notebooks

Feature evaluation

> Features that have already been evaluated will be ignored

| Feature | Description | Keep it? Why / Why not? |
|---------|-------------|-------------------------|
| Document Formatting | Apply customised formatting such as colours and emphases to text in the note | Yes? Formatting a document is quite difficult to do, but would provide an interesting challenge |
| Inline Attachments | Unlike Keep, Evernote allows you to attach files within a note and position them as you would a line of text | No. The ability to attach files should in itself be enough for my application |
| Notebooks | Notebooks are essentially folders of notes, and provide better categorisation tools for the user | Yes. Notebooks would be useful as they allow for easier organisation and control over the user's notes |
| Code Blocks | Inline code formatting is available in the note | Yes. This is separate to Document Formatting as it would allow for syntax highlighting within the document, which is a specific feature I would very much like to see |


Overall, Evernote is closer to a fully-fledged word processor pretending to be a note-making app than an actual notes app.
Its most useful feature is definitely the ability to sort notes into notebooks, which provides a high degree of control over notes.
Features such as inline attachments would be useful, but would require a lot of work to add.

#### [Microsoft OneNote](https://play.google.com/store/apps/details?id=com.microsoft.office.onenote)

> ![OneNote Demo](/assets/images/2019-04-08/onenote_demo_1.png)

OneNote is Microsoft's offering to the note-making world.
The application is targeted towards students and businesses as a method of making continuous notes and plans.
Of the three products evaluated, OneNote is the only one that is exclusively paid-for.
*(I have it as part of my Office 365 subscription)*

OneNote's integration with the Windows 10 OS and the Microsoft Surface line of tablets & PCs means that the ability to draw onto it is heavily emphasised as a feature, however it is capable of more than that...

Unlike Keep or Evernote, OneNote stores notes as Pages, where anything can be written anywhere.
I even use it for my A-Level notes as I can quickly draw up sketches and images, much faster than I ever could in Microsoft's Word

- Basic Notemaker Features (consistent between Google Keep, Evernote & OneNote)
- Inline Drawings
- Inline Equation Editing
- Customisable backgrounds (Lines / Grids / Plain)
- Notebooks
- Notebook Sections
- Notebook Pages
- Document Formatting
- Relocateable Elements
- Built-In Researcher
- Built-In Forms Integration
- Calendar Integration
- Replay
- Class Notebooks

Feature Evaluation

| Feature | Description | Keep it? Why / Why not? |
|---------|-------------|-------------------------|
| Notebooks | OneNote also organises with Notebooks, but they are more like <u>collections</u> of Evernote's Notebooks | No. OneNote's notebooks are one level too high for my liking |
| Notebook Sections | These are equivalent to Evernote's Notebooks, and make up a OneNote Notebook | Yes. See Evernote's evaluation for details |
| Notebook Pages | OneNote's pages allow you to edit any point on the page, not just each line | Yes? Implementation dependent |
| Inline Drawings | Unlike Google Keep, OneNote allows you to draw anywhere on its Pages | No. This is more of a desktop PC application, and most users are unlikely to have the peripherals required to use this feature |
| Inline Equation Editing | OneNote provides the MSOffice Equation editor within itself. This uses a hybrid LaTeX style to produce pretty equations | Maybe. If I can find a library for this then it is a feature I'd love to add, but it's not one I want to code myself |
| Built-In Researcher and Forms | OneNote allows you to add Polls and Research immediately to your notes | No. These features are intended primarily for academic use, and OneNote does them really well already |
| Replay | OneNote allows you to replay how your Page has taken shape over time | No. I don't see much use for this feature outside of academia, which is not the target for this product. Plus it'd be an absolute nightmare to make |
| Class Notebooks | OneNote allows professors and teachers to share notebooks with their students | No. This is a really smart part of OneNote but not one that my program is likely to need, especially given that I already ruled out collaborative notes |

### Key drawbacks

No product is perfect, and here is where I'm going to pick out the bits I don't like from each of the products

#### Google Keep

Google Keep is quite basic as far as note-making software goes.

- It only supports plaintext
- Images and embeds are only placed at the top of the note, not inline
- All notes are stored in one area. Notes can be tagged, but this is only a workaround

While Keep does provide reminders, unlike the other two softwares, its notes are always simple and cannot be edited to the same level as those made in OneNote or EverNote

#### Evernote

Evernote can do a lot, but you need to know where everything is

Take a look at this image

> ![The Evernote demo from earlier](/assets/images/2019-04-08/evernote_demo_1.png)

There are obviously a lot of features available, but it's hard to immediately see what each button does.
Evernote splits each set of actions with a small bit of whitespace, which looks nice I guess, but blends the sections together a bit.


#### Microsoft OneNote

OneNote is a big complex notemaker with way too many features

OneNote has... Everything (Pretty much) - You name it, you can probably put it in OneNote.
But this "catch-all" approach actually serves to disadvantage the program, as its large number of features make it prone to crashing and erroring.
My personal favourite is a glitch that occurs when zooming in or out without using the buttons in the ribbon.
The cursor on the page desyncs from the actual cursor, causing OneNote to place things in the wrong locations...


## Feature list

Okay so let's wrap this incredibly long post up, shall we?

### Things to use

- Notes
  - Save
  - Load
  - Edit
  - Archive
  - Delete
  - Pin
  - Reorder
  - Share
  - Notebooks
  - Colour
  - Tags
  -
- Content
  - Text
  - Title
  - Images (Inline?)
  - Links
  - Code Block Formatting
  - Attach Files
  - Equation Editing?

### Things to improve

- Not just plaintext
- Inline images and embeds?
- Simple and intuitive interface - but don't oversimplify
- Not too much at once - You never know where a bug might pop up...

## Summary

So, it looks like NTTKR is gonna be big...
Or perhaps not.
These are my ideal results but I know that building a massive application by myself near A-Levels is a big ask.
I tend to get carried away, but we'll see how far I can take this little Electron-React-Typescript app.