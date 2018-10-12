## FST Creation:

To solve the Finnish vowel harmony problem, I created 3 FSTs:

`add_at_suffix`: it attaches the adessive suffix _"llä"_ at the end of the word.

`add_in_suffix`: it attaches the inessive suffix _"ssä"_ at the end of the word.

`vowel_harm`: it turns the _"ä"_ in the suffix into a _"a"_ on the condition that the preceding stem contains one of the back vowels and there is no intervening front vowels.

Chaining the first one and the third one creates the FST that takes a Finnish word in its original form, and makes its correct adessive form. This is stored as `"ADESSIVE"` in the .far file. Similarly, `"INESSIVE"` of the .far file is created by chaining the second and the third.

## Accuracy

I tested the two rules with the dataset. For the adessive, `54` correct results were produced, which is `70.13%` of the data, while `23` cases were wrongly predicted. For the inessive, `60` were correct and `13` were incorrect, with an accuracy of `82.19%`.

## Analysis

I observed the data and discovered some exceptions. For example, `"diskofiili"` has a backvowel "o" and there is no intervening front vowel after the "o". According to the rule, its adessive should be "diskofiililla". In fact, however, it is "diskofiilillä". In other cases, the suffix triggered some change in the stem. For example, `"kutu"` becomes "kudulla" instead of "kutulla", where "t" becomes "d", or `"seinus"`
becomes "seinuksessa", where a "e" is inserted between the original stem and the suffix, instead of "seinusssa".

I worked together with Marcos, Anthony and Lara for some part of the homework.