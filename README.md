# clidpy

[![https://badge.fury.io/py/clidpy.svg](https://badge.fury.io/py/clidpy.svg)](https://pypi.org/project/clidpy/)

A Python module for making simple CLI-configured Discord bots.

I make a surprising number of "single-serving" bots, so I figured this module would be useful for me.

It's kinda like `python -m http.server` but for Discord bots.

## Usage

Run `pip install clidpy`, get your `BOT_TOKEN` from [here](https://discord.com/developers/applications), and then run:

```
python -m clidpy $BOT_TOKEN "!" greet "f'Hello, {name}!'"
```

You can import modules with `-i` before the token, and define multiple commands:

```sh
python -m clidpy -i num2words -i random $BOT_TOKEN "!" \
    reverse "text[::-1]" \
    shout "f'**{text.upper()}!!!**'" \
    wp "'https://en.wikipedia.org/wiki/' + title.replace(' ', '_')" \
    spell "num2words.num2words(number)" \
    roll "f'Rolling a {sides}-sided die: **{random.randint(1, int(sides))}**'"
```

Free variables in each expression are automatically turned into parameters.

Commands work both with the supplied prefix (here `!`), and as slash commands:

![Demonstrating clidpy-defined commands](https://user-images.githubusercontent.com/16232127/187996745-344d89f4-1664-4851-8f37-2fc73f5978e9.png)
