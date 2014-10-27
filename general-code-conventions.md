# General code conventions

Code conventions should be discussed with the team. Using [http://editorconfig.org/](http://editorconfig.org/) is recommended to automatically adapt the editor/ide.

## tabs vs spaces

tabs: good because devs can choose the size of the tab character, and easier for moving

spaces: because why not ?

## Lines length

Code lines should not be too long. 

The old way was less than 80 characters, which is sometimes very limiting.

The line length doesn’t really matter is your code is easy to read.

## Functions

They should not be too long.

A function should do a limited number of things: break it if if does too many things.

Given some parameters, a function should always return the same result (very important for testing !).

## Put a lot of effort into naming things

I wish I could emphasize this more. This applies to all sorts of programming: Js, file names, CSS classes, any language . Name things correctly, as best as you can. **A code with properly named variables and methods is often self explanatory**, and most of the time won’t even need to be commented.

Every programmer at some point had to wonder scratching their what some piece of code meant and what it was doing.

Don’t shortcut, and name things as they are. If it’s a collection, make it plural. If it’s a method, then it should be verbal. Also, qualify when needed: "selectedPolicy" tells more than just “policy”.

Don’t name an Array ‘array’, that doesn’t help, maybe it should be called deletedElementsList, or queuedTasks.

Effort in naming should be greater in public methods/API, good with private/protected members and lesser for locals.

### Avoid abbreviations

Code is written once, but it will be read way more times. By you, by peers. Soon, later, maybe years after. The time you’ll spend typing is negligible so stop fooling with shitty abbreviations. Nobody suffered arthrosis because he was too verbose in his variable and method naming. Nobody had to skip meals to compensate for replacing broken keyboards. Oppositely, we can’t count how many headaches poor naming caused.

`var b = convert( chktbl.getAmount(), ‘EUR’ ); // DON’T`

`var convertedAmount = convert( checkoutBill.getAmount(), ‘EUR’ ); // DO`

#### exceptions:

**iteration index**

for ( var i = 0 ; i < persons.length ; i++ ) { /* ... */ }

note that sometimes, you may want to fully name your loop indices. This is especially true for nested loops, or when you use the index inside the loop.

**Mathematical conventions or short names traditionally used in famous algorithms. implementations**.

var r = Math.sqrt( h*h + w*w );

When implementing a mathematical algorithm, it can be wiser to keep the original naming as computer scientists / mathematicians are used to them.

### How should I name it ?

Code conventions say a method should do one and one thing only. If you applied this, then it should be obvious. If you’re not sure how to name something, most of the times it means your code isn’t doing something clear.

What the hell *manageWidget()* means ?? *addWidget()*, *saveWidget()*, or *renderWidget()* ? Take some time to understand your own code, break it into smaller parts if necessary. 

### Practical rules

#### camelCase

variables and method should be written in camelCase. doSomething(). Java’s legacy brought us caps for class names. class don’t strictly exist in javascript but they can be micmicked with methods: var Car = function() {}; var car = new Car(); you should use caps on those constructs.

Modern frameworks introduced DI and services, so the frontier Class/Instance it isn’t clear anymore. Write your own set of rules and stick to it. For examples, my angular resource services are capitalized, but service methods or service objects are small camelCased… etc.

#### Method naming

methods should be verbs. keep conventions with verbs having broad definitions. All init() methods should do the same kind of processing. Idem for load(), which you could decide should be used for remote loading of content.

Methods returning boolean should be name isSomething().

#### Beware of tense

what deleted() do ? don’t be ambiguous and choose either delete() or isDeleted(). or maybe it meant something else.

#### Temporary variables

Introduce temporary variables to help understanding.

`return buildWidget( $.extend( {}, { closeable: true }, opts) )`

No one will offer you a price for sparing lines of code, or for the best one-liner to be seen.

Quite exaggerated, but here is a more verbose and easier to understand  version. It’s also easier to debug each step:

`var DEFAULT_WIDGET_CONFIG = { closeable: true };`

`var config = $.extend( {}, DEFAULT_WIDGET_CONFIG, options );`

`var widget = buildWidget( config );`

`return widget;`

## GIT and SCM

### End files with a newline

This avoids conflicts with virtually editing the last line

### Autoalign with caution

aligning variables names and cutting documentation to 80 cols can result in lots of line changes when just a small thing is changed. This ruins git histories.

