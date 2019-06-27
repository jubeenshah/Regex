# Regex

## Welcome to the [RegEx101 regex quiz](https://regex101.com/quiz).

This quiz used to be featured on this website many years ago, but was abandoned due to the vast amount of work to keep it updated. I have finally found the time to resurrect it, and ported it to the new website. It is based on the original quiz created by msmo many, many, years ago. My rendition of it is incomplete, and there are many improvements to be made. If you do have any feedback, please post it in the github issues and I will take a look at it.

The goal is to provide a fun way to learn how to use regular expressions with real life tasks, and at the same time try to guide you to learn useful constructs and how the internals of the regex engine works. The quiz will utilize the PCRE regex engine, but many of the skills you learn will be transferable to other flavors. The tasks will be unlocked one by one. When you finish task 1, task 2 will be unlocked, and so on. The tasks will get progressively harder, and you will receive less and less hand-holding the further you progress. It might be a good idea to open another tab to fiddle with the expressions, and utilize the very powerful unit test feature located in the regex editor.

Enjoy and I hope you learn something!

* Question 1 - Check if a string contains the word <strong>word</strong> in it (case insensitive). If you have no idea, I guess you could try <strong>/word/</strong>
  * Solution
  `/(?i)\bword\b/`</br>
    * (?i) match the remainder of the pattern with the following effective flags: i
      * *i modifier*: insensitive. Case insensitive match (ignores case of `[a-zA-Z]`)
    * \b assert position at a word boundary: `(^\w|\w$|\W\w|\w\W)`
    * word matches the characters word literally (case insensitive)
    * \b assert position at a word boundary: `(^\w|\w$|\W\w|\w\W)`
    
    
    
 * Question 2 - Use substitution to replace every occurrence of the word <strong>i</strong> with the word <strong>I</strong> (uppercase, I as in me). E.g.: <strong>i'm replacing it. am i not?</strong> -> <strong>I'm replacing it. am I not?.</strong> A regex match is replaced with the text in the <strong>Substitution</strong> field when using substitution.
    * Solution
      `s/\bi\b/I/g`</br>
        * **\b assert position at a word boundary: (^\w|\w$|\W\w|\w\W)**
        * **i matches the character i literally (case sensitive)**
        * **\b assert position at a word boundary: (^\w|\w$|\W\w|\w\W)**
        * **Global pattern flags**
            * g modifier: global. All matches (don't return after first match)
       
 * Question 3 - With regex you can _count_ the number of matches. Can you make it return the number of uppercase consonants (B,C,D,F,..,X,Y,Z) in a given string? E.g.: it should return `3` with the text `ABcDeFO!`. **Note:** Only ASCII. We consider `Y` to be a consonant! **Example:** the regex `/./g` will return **3** when run against the string `abc`.
 Match a single character not present in the list below

    * Solution
      `/(?![AEIOU])[A-Z]/g`</br>
        * **Negative Lookahead (?![AEIOU]) Assert that the Regex below does not match**
          * Match a single character present in the list below [AEIOU]
          * AEIOU matches a single character in the list AEIOU (case sensitive)
        * **Match a single character present in the list below [A-Z]**
          * A-Z a single character in the range between A (index 65) and Z (index 90) (case sensitive)
        * **Global pattern flags**
          * _g modifier_: global. All matches (don't return after first match)
