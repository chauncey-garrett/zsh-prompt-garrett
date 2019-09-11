# Garrett Zsh Theme for Prezto

> A prompt with the information you need the moment you need it.

**NEW: It's been a long time coming but I've added gifs so you can see
what the fuss is all about!**

I designed my prompt for readability and to present useful information when
needed.

The Garrett prompt supports:

- `git` status information
- All prompt types (`PS1`-`PS4`, `Autocorrection`, and a backup `SUDO_PS1`)
- Notification of background jobs
- Non-zero return codes
- Line drawing
- `ssh` status
- Directory truncation
- Vi-editor info
- Job completion
- History line number
- The current time

## Prompt types

### Standard Prompt (PS1)

Many (most?) prompts put the directory information in front of the cursor
entry point. Changing directories changes the location of the cursor on the
screen. This inconsistent location is undesirable. The Garrett prompt cursor is
consistently at the same place on the screen.

By using line drawing and inserting a newline between each command, scrolling
back through your history for the output of a previous command becomes
drastically easier.

Both Terminal and iTerm2 support line drawing and the prompt will look it's best
there.

![][1]

The Garrett prompt has a fallback if line drawing is unsupported by your
terminal emulator.

![][2]

The terminal theme shown here is [Solarized Dark][3] and the font is [Pragmata
Pro][4] (affiliate link).

### Right Prompt (RPROMPT)

![][5]

The right prompt contains useful information but moves out of the way for long
commands.

### Continuation prompt (PS2)

![][6]

### Selection prompt (PS3)

![][7]

NOTE: This view contains both the selection *and* continuation prompts. The
selection prompt is shown when entering 1, 2, or 3.

### Execution trace prompt (PS4)

![][8]

### Autocorrection prompt

![][9]

### Backup root prompt

There is a backup root prompt that will highlight most of the terminal in red if
you switch to the sudo user inside another shell which hasn't set this prompt.
It's a simple safety measure.

NOTE: This feature is available only when the shell environment is not reset by
switching to the `sudo` command. *i.e.,* switch to root using `sudo -s` and you
will see the prompt change its primary color to red (as described above); switch
to root with `sudo -i`, the environment will be reset and you'll see the base
Zsh prompt instead of my custom one.

## Features

This prompt has the following features. These features may be disabled and
rearranged as desired by using the corresponding tokens. There are also minor
changes that can (easily) be made in terms of formatting the output of the
prompt by editing the prompt file itself but that's up to you.

### Change host color when on ssh

![][10]

You can display either the full or truncated hostname on ssh by editing the
prompt file. The default is to display the truncated hostname.

NOTE: The primary prompt color changes from gray to orange—color was lost when
making the gif (#1).

### Change prompt color when UID is root

As a safety feature, the prompt will change color when logged in as the root
user. This looks the same as host color change on ssh but with a red color
instead of orange.

### ls the directory contents on cd

![][11]

### Determine the number of background jobs

![][12]

### Present working directory truncation, if needed

![][13]

Directory truncation will slim down the `PWD` to the first letter of each child
directory. This is [configurable][14] via Prezto.

### Report non-zero return codes

![][15]

Support for non-zero return codes must be enabled. See
Prezto's prompt [documentation][16].

### Report local time

You can change to time format from within the prompt file. Available options:

- 24 hour time format (default)
- 24 hour time format, second precise
- AM/PM time format

### Report the terminal line number

Useful for bang history completion and hipster pride.

### Report git status, git remote status, git prompt info and git SHA information

![][17]

| Symbol   | Meaning     |
| :---:    | :---        |
| λ:master | branch      |
| 9769ee9  | commit hash |
| \|       | dirty       |
| ⬆        | ahead       |
| ⬇        | behind      |
| ⥮        | diverged    |
| ✭        | stashed     |
| ✚        | added       |
| ✗        | deleted     |
| ✱        | modified    |
| ➜        | renamed     |
| ═        | unmerged    |
| ◼        | untracked   |

### Indicate vi-mode

Normal mode:

![][18]

Overwrite mode:

![][19]

If you like, you can add notification of insert mode by editing the prompt.

### Notifications for commands taking longer than *n* seconds

![][20]

The default time is 2 seconds but is adjustable in the code.

## Installation

- Have a working installation of [Prezto][21]
- Copy `prompt_garrett_setup` to `~/.zprezto/modules/prompt/functions/`
- Set `zstyle ':prezto:module:prompt' theme 'garrett'` in `~/.zpreztorc`
- Optionally, configure [pwd trunctation][22]
- Open a new terminal window

If you'd rather not have to do this, please provide your support on [Prezto #914][23].

## Helpful tips

Here's helpful suggestions and tips for ensuring the prompt works at its
best.

- Make sure you're using [Prezto][24] with the git module enabled - the prompt
  won't work without it (see [#6][25], [#7][26])!
- Even better, use my [fork of Prezto][27] which includes modifications
  (mentioned above) for a better experience
- The Garrett prompt has a custom `clear-screen` widget so that `^L` will
  properly redraw the prompt (#5). If you use [zsh-syntax-highlighting][28],
  [zsh-history-substring-search][29], or [zsh-autosuggestions][30], be sure to
  load those *after* you load the prompt in your [dotfiles][31].

## Like it?

If you've found this project useful, would you consider sending your support?

- [Contribute Feedback][32]
- [Submit a Pull Request][33]
- [Donate][34]

## Author

*The author of this module should be contacted via the [issue tracker][35].*

| [![][36]](http://chauncey.io) |
| :--------------------: |
| [Chauncey Garrett][37] |


[1]: img/garrett-prompt-terminal.gif "terminal prompt"
[2]: img/garrett-prompt-iterm.gif "iterm prompt"
[3]: http://ethanschoonover.com/solarized
[4]: https://www.myfonts.com/fonts/fsd/pragmata-pro/?refby=chauncey-io
[5]: img/garrett-prompt-rprompt-removal.gif "rprompt removal"
[6]: img/garrett-prompt-continuation-prompt.gif "continuation prompt"
[7]: img/garrett-prompt-selection-prompt.gif "selection prompt"
[8]: img/garrett-prompt-execution-trace-prompt.gif "execution trace prompt"
[9]: img/garrett-prompt-autocorrection-prompt.gif "autocorrection prompt"
[10]: img/garrett-prompt-ssh-login.gif "color change when on ssh"
[11]: img/garrett-prompt-chpwd.gif "ls the directory contents on cd"
[12]: img/garrett-prompt-number-of-background-jobs.gif "number of background jobs"
[13]: img/garrett-prompt-directory-truncation.gif "directory-truncation"
[14]: https://github.com/sorin-ionescu/prezto/tree/master/modules/prompt#prompt-display-length
[15]: img/garrett-prompt-exit-code-status.gif "exit code status"
[16]: https://github.com/sorin-ionescu/prezto/tree/master/modules/prompt#display-return-value
[17]: img/garrett-prompt-git.gif "git status line"
[18]: img/garrett-prompt-vim-normal-mode.gif "vim normal mode"
[19]: img/garrett-prompt-vim-overwrite-mode.gif "vim overwrite mode"
[20]: img/garrett-prompt-shell-notifications.gif "shell notifications"
[21]: https://github.com/sorin-ionescu/prezto
[22]: https://github.com/sorin-ionescu/prezto/tree/master/modules/prompt#prompt-display-length
[23]: https://github.com/sorin-ionescu/prezto/issues/914
[24]: https://github.com/sorin-ionescu/prezto
[25]: https://github.com/chauncey-garrett/zsh-prompt-garrett/issues/6
[26]: https://github.com/chauncey-garrett/zsh-prompt-garrett/issues/7
[27]: https://github.com/chauncey-garrett/zsh-prezto
[28]: https://github.com/zsh-users/zsh-syntax-highlighting
[29]: https://github.com/zsh-users/zsh-history-substring-search
[30]: https://github.com/zsh-users/zsh-autosuggestions
[31]: https://github.com/chauncey-garrett/dotfiles/blob/master/zsh/zpreztorc#L24-L56
[32]: https://github.com/chauncey-garrett/zsh-prompt-garrett/issues
[33]: https://github.com/chauncey-garrett/zsh-prompt-garrett/pulls
[34]: http://chauncey.io/donate/
[35]: https://github.com/chauncey-garrett/zsh-prompt-garrett/issues"chauncey-garrett/zsh-prompt-garrett/issues"
[36]: http://www.gravatar.com/avatar/81e1334c20c8dc25dbf3fee88dc1879c.jpg?s=150&r=g
[37]: http://chauncey.io
