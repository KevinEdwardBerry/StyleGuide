### TL;DR (Summary)
The purpose of code is to communicate with humans, so optimize the appearance of
code for better communication with the human(s) that will be working with it.

### General Considerations
* As with any guideline, there will be exceptions when needed.
* Following a style guide will provide consistency in the code base.
Consistency helps with readability because any inconsistency causes some measure
of distraction while reading.
* Optimize for ease of readability.  There is often a lot of opinion concerning
what is "readable".  **Remember that communication with humans is the goal.**
Let understandability be the guiding principle for decisions about code style.
* A style guide does not have to cover how every character must appear.  There
is a subtle art to visual formatting.  Opinions will vary for each person on a
team, but there must be some consensus at a reasonable level.  Do not get "hung
up" too much on trivial details.
* Consistency is most important at the smaller scales (blocks, methods, classes,
and files).
* If there is a consistent style in an piece of code, follow the existing style
when making changes.  Changing styles in the middle of a logical piece of code
creates distraction that causes extra cognitive effort to sort through.

--
The following are some general ideas of good code style based on what I consider
to be important for the readability and understandability of code.  These ideas
are generally considered controversial, so I give the reasons for why I consider
each of these ideas to be the best option for a readable and understandable code
style.

### General Principles of Good Code Style
* Use spaces instead of tabs for any visual separation (e.g. indentation).  Tab
size will be different based on editor setting which makes visual consistency
impossible.  The argument for tabs as saving disk space is not relevant because
disk space is cheap, and readability of code trumps disk space usage.  When disk
space is important (e.g. network transportation), there are tools for
minification that solve this in a much better way.  Modern editors allow you to
use the tab key on the keyboard for indenting in a way that inserts spaces
instead of a tab character.
* Strive to keep line length within the 80 character width.  Lines may extend to
100 or 120 characters occasionally when necessary, but generally prefer to be
under 80 characters.  There are some very rare exceptions to go beyond 120, but
strive for shorter line lengths.  Shorter lines are easier to cognitively digest
(hence why books still follow this principle).  Just because you can fit more
characters on a line on your screen does not mean you should.  This must be
considered on a case-by-case basis because sometimes it is the same level of
readability if the statement is one line or two when it is barely over the 80
character limit.
* Avoid checking in commented out code to your version control system.  This is
almost always extra "noise".  Your version control system will remember what
code was deleted, so there is no need to comment out code and check it back in
to the version control system as a comment.  This is dead code and adds extra
effort to reading the real code.
* Separate multi-line statements from other statements with an empty line.  This
makes it easier to recognize the start and end of a multi-line idea.  This is
similar to indenting paragraphs in a book.  Since indentation has another
meaning when writing code, we use an extra new line to make that kind of
separation.
* Use trailing commas instead of leading commas in a multi-line list.  There are
several ways that people write leading commas which makes it hard to keep it
consistent.  Trailing commas are much easier to keep consistent because they
are typically only written one way.
* Avoid using extra parentheses when they are not needed because these produce
extra "noise".  If it appears hard to understand without adding extra unneeded
parentheses, then consider refactoring the code with method extraction and/or
try changing spaces or new lines to better identify the parts of the expression.
* Optimize for code readability over diff readability.  Do not include a
"dangling" comma at the end of a list of things.  This is misleading because it
communicates that something should follow the comma.  The argument of cleaner
diffs when adding to the end of a list is invalid because the code is read more
than the diff of adding another item at the end.  Having a "dangling" comma is
like saying "To Be Continued" but never actually continuing which is misleading
communication.  The intention of a comma in this context is to append items in a
list, so make sure the list ends with an item.
* Do not force the use of braces to be used when they are not required by the
language.  This is most common among C-style syntax languages where a block of
code that is controlled by some control-flow keyword can be one or more lines.
The argument of reducing errors when adding a second line without adding the
braces is antiquated at best.  Following good coding practices can help prevent
this kind of mistake.  For example, having appropriate unit tests, separating
multi-line statements with a blank line (this includes these kind of blocks with
only one line because the one line is still tied to the control-flow keyword
part in the line above it), and extracting multi-line blocks into a method so
that it can be expressed with one line of code.
