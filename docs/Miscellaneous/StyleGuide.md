<style>
.spacer {
	padding-top: 10px;
	padding-bottom: 25px;
}
</style>
<style>
.nowrap {
	overflow: hidden;
    white-space: nowrap;
}
</style>

##Preface

<div class="spacer">
This page serves as both a template and as an example for how each type of document on YOMIDoku is structured.
</div>

#Classes / GDscript Files

In: res://(Filepath)

Inherits: (Inheritance Chain)

##Description

A brief description of the class / GDscript file.

##Properties

Each publicly accessible variable, alongside a brief description, data type, and initial value if applicable, in the following format:

|Property|Default Value|Description|
|:-----:|:-----:|:-----:|
|`EXAMPLE_PROPERTY`|123|A property, with a default value.|
|`EXAMPLE_PROPERTY_TEXT`|"Example text!"|A property with a string.|
|`EXAMPLE_PROPERTY_DICT`|{Key1: "Value",Key2: 123}|A property with a dictionary.|
|`EXAMPLE_PROPERTY_UNINIT`|N/A|A property, without a default value.|

If there are no publicly accessible variables, then display:
<p>There are no properties for this class.</p>

##Enumerations

A list of each enumerated type, alongside a brief description in the following format:

enum Example

- EXAMPLE_ENUM1 = 0 --- A brief description of the first enum.
- EXAMPLE_ENUM2 = 1 --- A brief description of the second enum.
- EXAMPLE_ENUM3 = 2 --- A brief description of the third enum.

If there are no enums, then display:
<p>There are no enumerated types for this class.</p>

##Constants

A list of constants, alongside a brief description and their values in the following format:

|Constant|Value|Description|
|:-----:|:-----:|:-----:|
|MAX_STALES|15|N/A|
|MIN_STALE_MODIFIER|"0.2"|N/A|

If there are no constants, then display:
<p>There are no constants for this class.</p>

##Methods

A list of methods, alongside a brief description, the return type, arguments (with data types), in the following format:

<div class="spacer"></div>

`exampleFunctionReturnsNull()`

A description of the function goes here. If you do not know how to describe the function, then display N/A.
<p>This function returns null; dont list return types in the description, this is just for clarification in the style guide.</p> 

returns `null`

<div class="spacer"></div>

`exampleFunctionReturnsInt(arg1)`

This is a function that returns an int.
It also has an argument.

returns `int`

<div class="spacer"></div>

`exampleFunctionReturnsDict(arg1:int,arg2="Default")`

This is a function that returns a dictionary value.
It also has a type specified argument, and an argument with a default value.

returns `dict`

<div class="spacer"></div>

If there are no methods, then display:
<p>There are no methods for this class.</p>

##Signals

A list of signals, alongside a brief description and the signal arguments in the following format:

`example_signal()`

A description of the signal goes here.

`example_signal_with_arguments(arg1, arg2, arg3)`

This signal emits several arguments.

If there are no signals, then display:
<p>There are no signals for this class.</p>

##Credits

Attribute any contributors here, using a hyperlink to their name on the about page; do NOT remove contributors.

##Source

A fenced codeblock, under an admonition in the following format:

??? abstract "ExampleSource.gd"
	```gd
	Source code goes here!
	```