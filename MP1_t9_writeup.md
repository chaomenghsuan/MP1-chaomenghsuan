## FST Creation:

To solve the T9 problem, I first created [t9.tsv](https://github.com/language-technology-gc/MP1-chaomenghsuan/blob/master/t9.tsv) mannually, which is used to created the FTS decoder through `"pynini.string_file"` function.

I trained a language model (order=6) based on 5,000 sentences from the `news.2009.en.shuffled` database to assign weight to the decoder.

`encode` is the FST that works the opposite way, turning text into the corresponding number.

`decode` is the FST that maps the number to the text. Before being assigned weight, it produces all of the possible combinations. 

`encoder` is a function which takes a string as input, and returns the encoded number form string as output.

`decoder` is a function that takes two inputs; a encoded number form string, and a number `n`. It assigns weight based on the language model, and returns a list of the first n most possible results.

## Challenges

`File size problem`: the database contanis about 44,000,000 sentences. I selected 5,000 to build my language model.

`No more than order 5 problem`: I tried language models based on 1,000, 5,000, 10,000, 100,000 and 200,000 sentences. Apart from the first two, when I tried `order=6` or more, I got an error like `FATAL: NegLogDiff: undefined 0 -4.55916e+20`.

`Prediction problem`: Both LMs with lower order or higher order creates some wrong prediction. However, they tend to make wrong prediction on different words. Intuitively, I feel that a LM with higher order better predicts long words.