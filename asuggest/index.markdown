---
layout: default
title: jquery.asuggest - open source javascript autocomplete library
projectname: / asuggest
projectpage: http://github.com/imankulov/asuggest/
regards: Created with <a href="http://www.jquery.com/">jQuery</a>
---


<script type="text/javascript">
    $(document).ready(function(){
        $(".jscode").each(function(){
            eval($(this).text());
        });
    });
</script>


**jquery.asuggest** is a small suggestion (autocomplete) library intended to be
a lightweight replacement for [jquery.autocomplete][autocomplete] in textareas.
The fact is that drop-down menu in the autocomplete library works not very well
in texteareas. So the alternative decision without menu and only with automatic
word completion has been proposed.

Requires:
 - [jQuery][jquery] (tested with 1.3.2)
 - [jquery.fieldselection][fieldselection] >= 0.2 

Basic asuggest sample. Sugestion works after the *newline* or *space* symbols.

<code class="jscode">
    var suggests = ["hello", "world"];
    $("#area1").asuggest(suggests);
</code>

<textarea id="area1">hello</textarea>

There is a set of default options which can overridden during asuggest creation
or just in any part of the code. Check this out: second area uses ":" character
as delimiter and begin to make suggestions only after the 2-nd character. This
code uses default options overriding.


<code class="jscode">
    var suggests = ["hello", "world"];
    $.fn.asuggest.defaults.delimiters = ":";
    $.fn.asuggest.defaults.minChunkSize = 2;
    $("#area2").asuggest(suggests);
</code>


<textarea id="area2">hello:w</textarea>

The third area uses "," and ":" for suggestions and starts to perform its job
after the 3-rd character. This example avoids to use global scope of defaults
and override options only for the current jQuery object.

<code class="jscode">
    var suggests = ["hello", "world"];
    $("#area3").asuggest(suggests, {
        'delimiters': ',:',
        'minChunkSize': 3,
    });
</code>

<textarea id="area3">hello,wo</textarea>


[autocomplete]: http://bassistance.de/jquery-plugins/jquery-plugin-autocomplete/ "jQuery Autocomplete"
[fieldselection]: http://labs.0xab.cd/jquery/fieldselection/0.2.3-test/ "jQuery fieldsepection"
[jquery]: http://www.jquery.com/ "jQuery"
