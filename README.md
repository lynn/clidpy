# clidpy

[![https://badge.fury.io/py/clidpy.svg](https://badge.fury.io/py/clidpy.svg)](https://pypi.org/project/clidpy/)

A Python module for making simple CLI-configured Discord bots.

I make a surprising number of "single-serving" bots, so I figured this module would be useful for me.

It's kinda like `python -m http.server` but for Discord bots.

## Usage

Run `pip install clidpy`, get your `BOT_TOKEN` from [here](https://discord.com/developers/applications), and then run:

```sh
python -m clidpy $BOT_TOKEN "!" greet "f'Hello, {name}!'"
```

That's it! That's the bot. Free variables in the expression are automatically turned into parameters.

Commands work both with the supplied prefix (here `!`), and as slash commands:

![greet-bot responding](https://user-images.githubusercontent.com/16232127/187997763-68b84467-8ed1-4210-99c7-605edfa2aa9d.png)

## A note on slash commands

**Your bot has a special command `!sync_commands` (or whatever prefix you chose) to tell Discord about the slash commands.**

You'll have to run this yourself, somewhat sparingly. There's allegedly a rate-limit on this operation but I don't know how severe it really is.

## Importing modules

You can import modules with `-i` before the token, and define multiple commands:

```sh
python -m clidpy -i num2words -i random $BOT_TOKEN "!" \
    reverse "text[::-1]" \
    shout "f'**{text.upper()}!!!**'" \
    wp "'https://en.wikipedia.org/wiki/' + title.replace(' ', '_')" \
    spell "num2words.num2words(number)" \
    roll "f'Rolling a {sides}-sided die: **{random.randint(1, int(sides))}**'"
```

![Demonstrating clidpy-defined commands](https://user-images.githubusercontent.com/16232127/187996745-344d89f4-1664-4851-8f37-2fc73f5978e9.png)

This includes local modules, so you can run `clidpy -i my_code` from a directory containing `my_code.py`.


