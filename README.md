# Fun Password Generator (`fpw`)

A password generator that attempts to generate random passwords in a cryptographically secure manner. 

By default, `fpw` generates completely random passwords using all of the letters, numbers, and symbols that are easily typed on an English keyboard. To support insecure systems, you can specify required character groups. To support insecure humans, you can generate pronounceable passwords. To break things, you can generate passwords from a large unicode character set.

Although `fpw` is mainly focused on a command line interface, 

# Usage

```
usage: fpw [-h] [--number NUMBER] [--pronounceable] [--lower] [--require-lower] [--upper]
           [--require-upper] [--digits] [--require-digits] [--special]
           [--require-special] [--characters CHARACTERS] [--unicode] [--active-directory]
           [--build-markov FILE]
           [length]

Generate random passwords in a hopefully secure manner.

positional arguments:
  length                Length of password

optional arguments:
  -h, --help            show this help message and exit
  --number NUMBER, -n NUMBER
                        Number of passwords to generate
  --pronounceable, -p   Create human pronounceable passwords
  --lower, -l           Use lower case letters
  --require-lower, -L   Require at least one lowercase character
  --upper, -u           Use upper case letters
  --require-upper, -U   Require at least one upper character
  --digits, -d          Use digits
  --require-digits, -D  Require at least one digit character
  --special, -s         Use special characters (punctuation)
  --require-special, -S
                        Require at least one special character
  --characters CHARACTERS, -c CHARACTERS
                        Specify individual characters
  --unicode, -z         Use a large unicode character set
  --active-directory, -a
                        Output passwords that exceed the default requirements in
                        Microsoft Active Directory environments (`-LUDS`)
  --build-markov FILE, -b FILE
                        Build a markov chain using the words in FILE.
```

# Features

## Character groups

You can specify the minimum number of lower, upper, digit, or special characters. You can also include only certain groups, or even specify a list of approved characters. If you specify `--lower`, `--upper`, `--digits`, `--special`, or `--characters` then passwords will only contain those characters.

## Pronounceable passwords

Generate pronounceable passwords using Markov chains.

The Markov engine is trained to produce English-like gibberish using the `words.txt` file in the repository. However, that file is not required to operate `fpw` because `fpw` is a self-updating program, making it significantly closer to sentience than your average password generator. I am going to go out on a limb here and make the claim that `fpw` uses Artificial Intelligence.

To make `fpw` smarter, get a list of words in a file. The words should be separated by a newline. Then run:

```
fpw -b words.txt
```

It will parse them and store the resultant Markov data inside the `fpw` script file itself so that you don't have to copy around multiple files. You read that right. It stores its data inside the same file holding its executable code.

### Examples

Generate passwords from lowercase, uppercase, digit, and special characters:

```
> fpw -luds
```

Require at least one lowercase, uppercase, digit, and special character:
```
> fpw -LUDS
NLHh'nfSgV1@U;{q
```

Only digits:

```
> fpw -d
4261729641542628
```

Only certain characters:

```
> fpw -c u
uuuuuuuuuuuuuuuu
```

Make a short password:

```
> fpw 1
r
```

Make a long password:

```
> fpw 300
rM_DK'^kf3@^pg]ja!\p3nrV$TUhq*.x(GCZr)Qz%>hup-T!y@@6KW#]f](]b!R6w'C{!x>sEeYtQ*yY~).xI7-|-Y(\Lk;c4COr-jdyM=/D@w{|jmmHeFNL:JqXWgQ$J&N@sb0.$w9e('j^R:x"qcv7Y{-DQ!pmwi%UoT,F)WTL-Q._L-1U&".jr)J[g/n"8|-Vv3/S1Yr&zG}S"xv1?!iC_(?T.$tjX!d:<B|elY^UIe,xfnR+fldNiE}V33uYT3}>yAE3kR,){x+vJsP|vHnDZKH6'N\hV@}Boh.4)O!?
```

Require 6 digits and 3 special characters:

```
> fpw -D 6 -S 3
SK374-{Y5y2Wty3-
```

6 high unicode range passwords:

```
> fpw -zn 6
཯୳↥ѐḒृ₮⇉O2ޝ☀แݾ࢙ቦ
♝⇧ᑙᘒଥȨണቁᢔዅ✀ᳫܡ὿࿾ᇤ
ຟക᭫ᢱᾞẠᬩ❷਴∴ᾘ✋Ṋឧ৹ཡ
ᮀ૲ᓴಙᳫaᯍ┐╝ᒨ℁ڛ܂ฃఎ֞
ࡰ⎪⍜✐␯͊ಪǱ⊯ᯒ◬ყӽѦଁ࿼
○ܠᕲ༖੄ᨱʤᧁΩ፭⁤နཟϳ഑⎬
```

5 vaguely human pronounceable passwords:

```
> fpw -pn 5
eidbloneseandune
rintrsscaphatind
onionsalatrytoki
pharocagnossshyd
dititesindeseses
```
