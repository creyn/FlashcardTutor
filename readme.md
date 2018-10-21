# Flashcard Tutor

`Flashcard Tutor` is a project that combines **Microsoft Flow**, **Github** and **Twitter** for teaching languages in a form of modern `flashcards`.

## Origin

When I started learning japanese it turned out that there are many alphabets: hiragana, katakana, kanji. And I needed a way to learn and remember all of those new characters. The best option seems to be to constantly remind myself of what I learned.

Around the same time I was playing with Microsoft Flow, the tool that easilly allows you to automate some business logic without the need to create and host a separate application. It is serverless and free (up to 750 *executions* for month). It allows to build an application logic by joining some very basics blocks to create more complex `flows`.

One of the building blocks is a Twitter account connector. It is very easy to send a `tweet`. I am a Twitter user and I follow many people. And also a few bots (probably :)) that from time to time sends some usefull information and even japanese words to learn for every day. But I cannot find a bot with just an alphabet for the polish language.

So I decided to create one. As a developer I came up with a configurable solution that could be extended by new languages (flashcards) to learn. So you can use it for other languages and actually anything you find useful to know.

## How it works

### Github

In this Github repository there is a [courses](courses) folder with files in JSON format. Each file is meant to have data set for **one course** that will be tweeted by **one account**. In addition in the [configuration file](config.json) file there are references to that JSON files. That allows to add / remove courses.

#### Almost a flashcard

The concept of a flashcard is that on one side of a paper you have the word you want to learn. On the opposite side there is a translation. So you can check yourself to see if you know this word.

In the `Flashcard Tutor` solution, the tweets are not reversible, so the word you want to learn is in the first line. In the next lines there is a translation (or pronunciation). And you can have as many lines as you want.

### Microsoft Flow

In my Microsoft Flow account, one of the flow is running every hour. It checks the Github repository and reads the `configuration` file. There it finds all courses that should be executed, with URLs to each course data file. Then it takes all the course data from configured `data` files. For each course it randomly chooses one entry and tweets it.

For now there are only 750 free flow executions each month. As I have few more flows there, I decided to run all courses at the same time. Also the Twitter connector block has hardcoded Twitter accounts. So in order to add a new course I have to manually change the flow.

### Twitter

I created a new account for the project: `Flashcard Tutor` (https://twitter.com/FlashcardTutor). Also, there will be new account for each course so people interested in specific course could subscribe to it.

For now there are 2 accounts:
1. Japanese hiragana characters (https://twitter.com/ft_jpnpol_hirag)
2. Japanese katakana characters (https://twitter.com/ft_jpnpol_katak)

## How to add your courses

If you want to use the `Flashcard Tutor` to learn some language of your choice, you have to prepare new data file and the configuration have to be extended.

You have two options:
1. Contact me at ft@creyn.pl
2. Create PR with the updated configuration file and new JSON data file. The file must be in specific format. 