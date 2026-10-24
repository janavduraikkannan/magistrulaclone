# Verba

**Latin sentence practice from Latin I Honors through AP Latin, with Fēlix the tutor cat.**

**Use it here: https://janavduraikkannan.github.io/verba/**

Verba builds fresh Latin sentences from the topics you pick, then has you translate the whole sentence, English to Latin or Latin to English. It checks your answer, tells you exactly what went wrong, and lets you ask Fēlix, an AI tutor, questions about the grammar along the way. It was made for a high school Latin class, and its topics follow the Tennessee course sequence (Latin I Honors, Latin II Honors, Latin III Honors, AP Latin).

> **Privacy, in short:** Verba has no server of its own. Your practice runs in your browser, your AI key goes straight from your browser to the AI company you chose, and nothing is saved anywhere else unless you make an account. If you do, your account and anything you put on the leaderboard are stored with Google Firebase, are **not encrypted**, and **are not private**. Read the full [Privacy Statement](PRIVACY.md) before making an account.

> **Email and password, in short:** optional, never verified, and Verba never sends email. **A forgotten password can't be recovered**, so keep your account key saved too.

## What it does

- **Topics by course.** Every grammar topic from Latin I through AP Latin, grouped under the class it's taught in. Topics already covered in class are shaded.
- **Build your own sentence type.** Pick a main structure (statement, question, indirect statement, conditional, gapping and more) and the grammar that should appear inside it.
- **Whole-sentence translation.** You type the entire sentence. Word order that doesn't change the meaning never counts against you.
- **Fair macron checking.** A missing macron is pointed out but still counts as correct, unless the macron changes which form the word is.
- **Fēlix, the AI tutor cat.** Ask as many questions as you like. Before you answer, Fēlix judges whether a question gives away too much; after you answer, you can ask anything.
- **Charts and vocabulary.** Ending charts and a vocabulary list for each sentence, shown by default and easy to hide. Click a vocabulary word to insert it.
- **XP, levels and streaks.** Roman ranks from Discipulus to Imperātor, a daily streak, and a Laurea for finishing AP Latin.
- **Optional accounts and a live leaderboard.** A personal account key keeps your progress on every device. You can also add an email and password to log in more easily; the account key always works too.
- **Light and dark mode.**

## Getting started

1. Open the site. Fēlix walks you through setup the first time.
2. Get a free AI key. The site uses it to check answers and to power Fēlix. The [step-by-step guide](https://janavduraikkannan.github.io/verba/getkey.html) shows how to get a free Groq key, and the [keys page](https://janavduraikkannan.github.io/verba/keys.html) lists every provider that works.
3. Pick your topics and start translating.

Verba itself is free. The AI providers it supports all have free options; a few paid providers are supported too if you already have a key.

## Accounts

Accounts are optional. Every account has an **account key** (it looks like `VERBA-XXXX-XXXX-…`), and the key is the account: paste it on any device to log in.

You can also add an **email and password** in the Account window, or during the welcome tour. Then you can log in on any device with just those, and everything comes with you: XP, streaks, topics, settings, your profile, and your AI key if you chose to save it to your account.

- **Optional.** The account key always works as a login, with or without an email and password.
- **No emails, ever.** Your email isn't verified and Verba never sends anything to it. It's only the name you log in with.
- **A lost password is gone forever.** There's no "forgot password." If you still have your account key, log in with it and set a new password. If you have neither, the account can't be recovered.
- **Changing it.** Only someone logged in to the account (with the key, or the email and password) can change or turn off its email login.
- **Use a password you don't use anywhere else.** Verba can't promise this is secure; see the Privacy Statement.

**How it's stored.** The email and password are stretched together in your browser (PBKDF2-SHA256, 310,000 rounds). Part of the result names a record in Firebase, and the rest encrypts your account key inside that record, so the record reveals neither your email nor your password. The password is never stored or sent anywhere. Your email is saved in your account data, so the Account window can show it. Each change to a login record has to prove it comes from the account (a hash chain made from the account key, checked by [`firestore.rules`](firestore.rules)). Because the email isn't checked, the same email can be used with two different passwords, which makes two separate logins.

## How it works

Verba is a static website hosted on GitHub Pages. There is no Verba server and no build step:

- **`index.html`** is the whole app: the sentence generator, the answer checker, the interface and the account code.
- **AI requests** go directly from your browser to the provider whose key you entered (Groq, Google Gemini, OpenRouter, Cerebras, Mistral, Hugging Face, Cohere, OpenAI, Anthropic or xAI).
- **Accounts, email logins and the leaderboard** use Google Firebase (Cloud Firestore). The access rules are in [`firestore.rules`](firestore.rules). Nothing about accounts is stored in this GitHub repository.

### Repository layout

| Path | What it is |
| --- | --- |
| `index.html` | The app |
| `getkey.html` | Guide to getting a free Groq key |
| `keys.html` | Every AI provider Verba supports, with free limits |
| `firestore.rules` | Security rules for accounts, email logins, the leaderboard and usernames |
| `img/felix/` | Fēlix, in every mood |
| `img/icons/` | Interface icons |
| `media/` | The key tutorial video, its captions and poster |
| `tools/felix.py` | The script that draws Fēlix |
| `unused/` | Older artwork and resources, kept on purpose but not used by the site |

## Privacy

See the full **[Privacy Statement](PRIVACY.md)**: what Verba stores, who can see it, what the site's owner can see, and which other companies are involved.

## Contributing and issues

Suggestions, bug reports and pull requests are welcome, but **none are guaranteed to be read, answered or accepted**. Anything submitted may be checked and manually approved at the owner's discretion. See **[Contributing](CONTRIBUTING.md)** for details.

**Never post an account key, a password or an AI key in an issue or pull request.**

## Credits

- Icons by Lorc and Delapouite from [game-icons.net](https://game-icons.net), [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) (see `img/icons/LICENSE-game-icons.txt`).
- Day and night switch after Adam Argyle, "Building a theme switch component" ([web.dev](https://web.dev/articles/building/a-theme-switch-component), Apache 2.0), with a sun from [Feather Icons](https://feathericons.com) (MIT) and easings from [Open Props](https://open-props.style) (MIT).
- Confetti by [canvas-confetti](https://github.com/catdad/canvas-confetti) (ISC).
- Profile pictures of Roman figures and places come from [Wikimedia Commons](https://commons.wikimedia.org); each picture's author and license are shown on the site.
- Fonts: Fraunces, Figtree and Gentium Book Plus, from [Google Fonts](https://fonts.google.com) (SIL Open Font License).
- Older artwork in `unused/fluent-emoji/` is [Microsoft Fluent Emoji](https://github.com/microsoft/fluentui-emoji) (MIT).
- Fēlix was drawn for Verba.

## License

No license has been chosen for Verba's own code and artwork yet, so all rights are reserved by the owner. The third-party pieces listed under Credits keep their own licenses.
