## Author's approach for reviews

As an author, you are going to receive feedback for your work. For this reason,
it is important to be open and welcome the others' opinion, as well as to be humble.

### Humble-what?

It is normal (and commonly expectedd) to make mistakes, as long as code is written by humans.
Of course, that it does not mean that <br> you should write down your code without giving the appropriate 
case. Having a team which consists of developers that accept and admit ther mistakes is desired. <br>
That helps the team to accept comments and critism on a review. 

It also helps to avoid having endless discussions & rejections, because some may think that introducing 
bugs is seen as something forbidden and keep them hidden. <br>This is the opposite to be open for feedback.

> Having buds on your code is accepted and recognizing them is desired.

Our profession never stops evolving. You have to admit that nobody's is perfect, 
to accept that you can make mistakes and despite how good your are, <br> you can still
learn new things and improve (yourself).

You are not unmistakable or unbuggable and you don't need to link 
your credibility as a developer with possible mistakes that can appear in your code.
After all, you are a human, so please **be humble**.

Additionally, being a member of a team with a leader that can accept critism on
mistakes is crucial. *In the end, you always learn from your mistakes.*


### You are not equal to your code

When someone provides you with comments and critisism on your your code,
it is not a critisism on you personnally. Remember: don't link your reliability with the code
you write. <br> Your personality and your work still counts in your team. 
Being a programmer, does not mean that you are perfect in everything from day 1.
*As said, it is a never ending evolving skill.*


### You are on the same side
Read this quote first:

> “Criticism is almost never personal in a professional software engineering environment — it’s usually just part of the process of making a better product."
> [Fitzpatrick, Collins-Sussman: Debugging Teams, page 16](https://book.debuggingteams.com)


Please make sure that you always have in mind that both the reviewer and you, are on the same side.


### IKEA Effect

> The IKEA effect is a cognitive bias in which consumers place a disproportionately high value on products they partially created. <br>The name refers to Swedish
> manufacturer and furniture retailer IKEA, which sells many items of furniture that require assembly. *source: [Wikipedia](https://en.wikipedia.org/wiki/IKEA_effect)*


What exactly is this?
> A 2011 study found that subjects were willing to pay 63% more for furniture they had assembled themselves than for equivalent pre-assembled items.[1]
> *source: [Wikipedia](https://en.wikipedia.org/wiki/IKEA_effect)*

It is totally ok think of your code as something valuable, probably the best in the market. I am sure that you gave the best of yourself. <br>
Though this, does not mean that your code cannot accept any changes or you might need to refactor a portion of it.
So we need to have in mind the IKEA effect and not being influenced by it.


References:
* [1](https://stitcher.io/blog/the-ikea-effect)
* [2](https://betterprogramming.pub/the-ikea-effect-when-people-delete-our-code-243405c151f3)

### Different Aspects/Perspectives on your Code

Each developer can have a different technical background, different approaches
on certain things, experiences, etc; <br>That applies as well for the reviewers of your code.
It is quite possible to see your code in an different way that yours. <br>
Plus, your code apporach and its concept is not as common for them as to you.
This, of course does not mean that your code cannot contain a mistake, even a little one.

For instance,

```
@Composable
fun myComposable(card: CardModel){
    if(card.type == CardType.Credit || card.type == CardType.Debit) {}
}
```

A common set of questions of the code sample above is
* When does this take place?
* Why having business logic in your composable? I think that we should place it somewhere else

All of them are pretty much correct. However the reviewer is not always
able to understand and have the same knowledge of the code as you.

A (better) approach is:
```
//constants.kt
val billableCards = listOf(CardType.Credit, CardType.Debit)
//or better
fun CardType.isBillableCard(cardType)

val isBillableCard = cardType in billableCards

if(isBillableCard){...}

```

The pattern we discuss here is called **[implicit knowledge](https://bloomfire.com/blog/implicit-tacit-explicit-knowledge/)**. It is common and normal for not to be able to see this.<br>
However, it is better that there might be someone that can have a different perspective than yours.
So, welcome the constructive critisism, be open, be humble and thank your reviewers for giving 
you different approaches on your code.

### Exchange Knowledge

You are members of the same team (or chapter) and dot't forget that you are working
for the same product.

Code reviews through PRs are a great means to establish standard patterns and conventions, maintain
your architecture and exchange knowledge & best practices. <br> I would say 
that you need to think of them a great source of knowledge.
