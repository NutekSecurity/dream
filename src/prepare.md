# Preparation

## I have preperad for you a Ruby script that works with Homebrew

_Nutek Security Platform_ in form of `nutek-apple.rb`. This Ruby program lets
you download everything you will need to hack & slash.

[Look Here!](https://github.com/nutek-terminal/nutek-apple) and start with
`mini` version.

I have compiled this program sets to replace paid or trial based
applications, so the cost is nil. The only thing involved is computer
and internet connection.

## Get yourself good terminal application

I recommend [iTerm2](https://iterm2.com/). It is free and has a lot of
features. You can use default Terminal.app, but it is not as good as
iTerm2.

Actually above statement is not true. I recommend either [Alacritty](https://alacritty.org/) or [Kitty](https://sw.kovidgoyal.net/kitty/). Both are free 
and have a lot of features. You can use also [Warp](https://www.warp.dev/) 
it's the most advanced terminal emulator for Mac. The difference between 
this termianl apps and iTerm2 is that they are using GPU to render the 
terminal. This means that they are faster and more responsive.

## Get yourself good text editor

I recommend [Visual Studio Code](https://code.visualstudio.com/). It is
free and has a lot of features. You can use default TextEdit.app, but
it is not as good as VSCode.

You can also use [Neovim](https://neovim.io/), but it's not for everyone. 
It's a bit more complicated to use, but it's very powerful. You can use it with
[Alacritty](https://alacritty.org/) or [Kitty](https://sw.kovidgoyal.net/kitty/).
It also works with [Warp](https://www.warp.dev/) and [iTerm2](https://iterm2.com/), Terminal.app also is capable of running Neovim. The difference between 
VS Code and Neovim is that Neovim is a terminal based text editor. This means 
that one you can use in the terminal and the other you can use in the GUI (normal system window). It's also 
very fast and responsive.

Right now the new upcoming text editor is [Zed](https://zed.dev/). It's made in Rust and it's very fast and responsive. It's also very powerful. It's also free and open source.


## Get yourself good browser

I recommend [Firefox](https://www.mozilla.org/en-US/firefox/new/). It is
free and has a lot of features. You can use default Safari.app, but it
is not as good as Firefox. Esspecially when it comes to security.
It's not that Safari is not secure, Firefox let's you install individual
SSL certificates that do not interfere with the system. This is very
important when you are testing SSL/TLS connections.

The second browser I recommend is [Opera GX](https://www.opera.com/gx).
It's a gaming browser, but it's also very good for hacking. It has a lot
of features like _free_ VPN, ad blocker, etc. It's also very fast and secure.

## Invest into good VPN

I recommend [ExpressVPN](https://www.expressrefer.com/refer-a-friend/30-days-free?referrer_id=92684050&utm_campaign=referrals&utm_medium=copy_link&utm_source=referral_dashboard). It is not free, but
it is very good. You can use free version, but it is limited to 3
countries and 1 device. You can use default VPN.app, but it is not
as good as ExpressVPN. With this VPN you can connect to 160 locations
in 94 countries. It's very fast and secure. It also has a lot of
features like split tunneling, kill switch, DNS leak protection,
etc. It's also very easy to use. You can use it on all your devices
and you can use it on all your devices at the same time. It's also
very cheap. It's only $8.32-13 per month. You can also use it for free
for 30 days.

It's __important to use VPN__ when you are hacking. Because, you might be locked
when doing your security assessment. You can also use VPN to hide your
identity. __Don't tell me that I didn't warn you__.

## What I use?

- nutek-apple.rb (Ruby script) _mini_ version
- Alacritty (Terminal) - in nutek-apple.rb
    - tmux (Terminal Multiplexer) - in nutek-apple.rb
        - tmux mouse support - `echo "set -g mouse on" >> ~/.tmux.conf`
- Warp (Terminal) - in nutek-apple.rb
- Neovim (Text Editor) - Vim is included in macOS as default
    - Coc (Vim Plugin)
    - Vim Plug (Vim Plugin Manager)
- Firefox (Browser) - in nutek-apple.rb
- Opera GX (Browser) - web browser that has a lot of features (Spotify, Messanger, WhatsApp, X, etc.)
- Homebrew (Package Manager) - in nutek-apple.rb
- ExpressVPN (VPN)
- VS Code (Text Editor)
- Python3 (Programming Language) - default in macOS, recommended to use
pyenv and pyenv-virtualenv to install newer version, use with matplotlib, numpy, pandas, sympy and jupyter for data science
- Ruby (Programming Language) - default in macOS, recommended to use rbenv
to install newer version, use with rails, sinatra, jekyll, etc.
- Rust (Programming Language), recommended to use rustup to install and use it to create CLI tools for example
- Go (Programming Language), recommended to use goenv to install and use it to create CLI tools for example
- One of the below:    
    - Podman (Container Engine) - in nutek-apple.rb
        - Podman Desktop (GUI for Podman) - in nutek-apple.rb
    - Docker (Container Engine) - in nutek-apple.rb
- Trello (Project Management) - AppStore
- Bard, ChatGPT and GitHub Copilot (AI) - __think__ before you enter anything into the prompt engine, don't let the data leak out, your data is your data, don't let anyone use it against you and others.
- JavaScript programming language prefferably installed using nvm (Node.js) - to build upon read materials and probably make webapps, D3.js, etc.
- Wireshark (Network Analyzer) - in nutek-apple.rb


I think you catched the drift. I use everything that is in nutek-apple.rb.
I also use mostly open source software. I also use some paid software,
but I think it's worth it. I also use some software that is not in
nutek-apple.rb.

## What kind of device you will need?

I recommend any macOS device that is capable of running macOS Big Sur. Although
above setup might work on older versions of macOS, but it's not tested.

You might use this setup on Linux, but it's not tested, and you will have to
manually tweak nutek-apple.rb to work with Linux. The rest of the setup should
work on Linux.

Windows is not supported. You can use Windows Subsystem for Linux, but it's not
tested. You will have to manually tweak nutek-apple.rb to work with Windows
Subsystem for Linux. The rest of the setup should work on Windows Subsystem for
Linux. You can also use Windows Terminal, but it's not tested. You will have to
manually tweak nutek-apple.rb to work with Windows Terminal. The rest of the
setup should work on Windows Terminal and Windows Desktop (10/11). You could
also use virtual machine with some flavour of Linux, but it's not tested. 
You will have to manually tweak nutek-apple.rb to work with virtual machine.
The rest of the setup should work on virtual machine, except for Podman, 
which might be tricky or impossible to run on virtual machine depending on
capabilities of your CPU.

You might also try [nutek-fedsec on GitHub](https://github.com/nutek-terminal/nutek-fedsec) and
[nutek-fedsec on Dockerhub](https://hub.docker.com/r/neosb/nutek-fedsec) 
insted of nutek-apple.rb. This is few GigaBytes Docker image powered by
Fedora that contains everything you will need to hack & slash, but it's not 
any more developed. It's open source, so you can fork it and develop it 
yourself. It's also free, so you can use it as you like.