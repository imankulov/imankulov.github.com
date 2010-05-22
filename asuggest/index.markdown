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
word completion is proposed.

Requires:
 - [jQuery][jquery] (tested with 1.3.x and 1.4.x)
 - [jquery.fieldselection][fieldselection] >= 0.2

Basic asuggest sample. Sugestion works after the *newline* or *space* symbols.

<code class="jscode">
    var suggests = ["hello", "world"];
    $("#area1").asuggest(suggests);
</code>

<textarea id="area1">hello</textarea>

There is a set of default options which can overridden during asuggest creation
or just in any part of the code. Check this out: second area uses ":" character
as delimiter and begins making suggestions only after the 2-nd character. This
code uses default options overriding.


<code class="jscode">
    var suggests = ["hello", "world"];
    $.fn.asuggest.defaults.delimiters = ":";
    $.fn.asuggest.defaults.minChunkSize = 2;
    $("#area2").asuggest(suggests);
</code>


<textarea id="area2">hello:w</textarea>

The third area uses "," and ":" for suggestions and starts performing its job
after the 3-rd character. This example avoids using global scope of defaults
and overrides options only for the current jQuery object.

<code class="jscode">
    var suggests = ["hello", "world"];
    $("#area3").asuggest(suggests, {
        'delimiters': ',:',
        'minChunkSize': 3,
    });
</code>

<textarea id="area3">hello,wo</textarea>

<p>This variant doesn't perform automatic completion which can be pretty
annoying in some cases, but tab-driven completion is still works as expected.
You may note also that completion handles well the case of zero-sized minimal
chunk.</p>

<code class='jscode'>
    var suggests = ["head", "hello", "heart", "health", "horizontal", "horizont", "hormonotherapy"];
    $("#area4").asuggest(suggests, {
        'minChunkSize': 0,
        'delimiters': ' \n',
        'autoComplete': false,
        'cycleOnTab': true
    });
</code>
<textarea id='area4'>he</textarea>

Next sample discusses rather sophisticated "stop suggesting" feature. As you can
see in previous examples, pressing Enter or Space key while autocompleting
breaks this process and adds a space after the latest chosen variant. This
behaviour can be disabled or overrided with two asuggest options:

- `endingSymbols`: string which will be appended at the end of the suggested
  text after this kind of breaking. Space is the default one.
- `stopSuggestionKeys`: array of keycodes (int), each of which defines a key
  which stops suggesting. Codes of space and return are used by default.

In order to prevent such behaviour it's enough to pass an empty array for a
"stopSuggestionKeys" argument. The example below append a comma after each
selection. In order to take odvantage of this feature it's enough to type Enter
key.

<code class='jscode'>
    var suggests = ["head", "hello", "heart", "health", "horizontal", "horizont", "hormonotherapy"];
    $("#area5").asuggest(suggests, {
        'endingSymbols': ', ',
        'stopSuggestionKeys': [$.asuggestKeys.RETURN]
    });
</code>
<textarea id='area5'>he</textarea>

There is a set of constants in $.asuggestKeys variable, which simplifies the
definition of stopSuggestionKeys array, as in previous example. Variants
currently defined are SHIFT, CTRL, ALT, LEFT, UP, RIGHT, DOWN, DEL, TAB,
RETURN, ESC, COMMA, PAGEUP, PAGEDOWN, BACKSPACE and SPACE.

[autocomplete]: http://bassistance.de/jquery-plugins/jquery-plugin-autocomplete/ "jQuery Autocomplete"
[fieldselection]: http://labs.0xab.cd/jquery/fieldselection/0.2.3-test/ "jQuery fieldsepection"
[jquery]: http://www.jquery.com/ "jQuery"
