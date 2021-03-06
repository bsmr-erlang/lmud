# λMUD

<a href="https://raw.github.com/lfex/lmud/master/resources/images/El-Mud.png"><img src="resources/images/El-Mud.png"/></a><br/>

λMUD (pronounded "L-MUD" or "El-MUD") is a rather minimalistic MUD server,
written in Erlang and LFE, making use of the excellent OTP libraries.

The aim is to have solid support for exploration, roleplaying, and in-game
economies deployed on a highly fault-tolerant environment (which supports
hot-code loads) where system crashes or reboots are more of an exotic
curiosity than a commonplace thing.

Erlang/OTP is an excellent match for MUD development, with strong support
for concurrency through light-weight processes, hot code upgrades, near-
transparent mechanisms for distributed computing, etc.

This project has dual ancestry: originally based on the
[ErlyMUD](https://bitbucket.org/jwarlander/erlymud) code, it
derives much of its new MUDness from
[TinyMUD](http://en.wikipedia.org/wiki/TinyMUD) servers like
[TinyMUSH](http://en.wikipedia.org/wiki/TinyMUSH),
[PennMUSH](http://www.pennmush.org/),
etc.


## Getting Started

ErlyMUD expects that you have Erlang 17 and rebar installed. Once you have
that taken care of, follow these steps:

  1. Download the latest:

     ```sh
     $ git clone https://github.com/lfex/lmud.git
     ```

  1. Change directory, compile the source, and make a release:

     ```sh
     $ cd lmud
     $ make rel
     ```

  1. Start up λMUD:

     ```sh
     $ make run
     ```

  1. From another terminal, connect to the game:

     ```sh
     $ rlwrap telnet localhost 1203
     ```
     Note that ``rlwrap`` gives you readline support in telnet, allowing you
     to use a command history like with your system shell (including such
     things as searching the command history with ``^r``).

     If your other terminal session is in the ``lmud`` working dir, you can
     use thr following convenience ``make`` target:

     ```sh
     $ make connect
     ```

     At which point you should see something like this:

     ```
      Trying 127.0.0.1...
      Connected to localhost.
      Escape character is '^]'.

      Welcome to:

                                    ....
                                  .'   ,:
                                .'      \.___..
                              .'      .-'   _.'
                              '.\  \/...-''`\
                                :.'   /   \  :
                                 :    () () /
                                 (_ .  '--' ':
                                   / |_'-- .'
                                   \   \  .'_\
                                  .|__  \/_/:
                                 /          :\.
                                .' -./      .'{\|))
              __        .        :    ...    ::::::::::-.
              \ \       ;;,.    ;;;   ;;     ;;; ;;,   `';,
               \ \      [[[[, ,[[[[, [['     [[[ `[[     [[
                > \     $$$$$$$$"$$$ $$      $$$  $$,    $$
               / ^ \  o_888 Y88" 888o88    .d888  888_,o8P'
              /_/ \_\ "MMMM  M'  "MMM "YmmMMMM""  MMMMP"`


      An El-MUD Game Server, v0.4.0


      ------------------------------------------------------------------------------
        If you are loging in for the first time, enter the character name
        you would like to have (case insensitive) at the "Login" prompt.
      ------------------------------------------------------------------------------


      Login:
     ```

  1. Create a user.

  1. Have fun!


## Current Status

λMUD presents what's currently at least a minimally playable environment.
It's possible to connect, create a password-protected user account, and log
in to the game. Once there, you can communicate with other players, walk
around between rooms, and handle items.

## Game Features

  * Rooms have a title, and brief + long descriptions.
    * The brief description is used when walking into / through a room,
      and is intended to only show the most obvious features of the room.
    * When using the "look" command, the long description will be shown
      instead.
  * Items can be picked up, dropped and looked at;
    * "get sword", "drop sword"
    * If an item is 'attached', it can't be picked up. Instead it belongs to
      the room, and is used to add detail descriptions so that you can for
      example do "look painting" and see a more in-depth description of that
      part of the room.
  * You can see who is logged on, talk to other players, and use emotes.
    * "who", "tell <who> <what>", "say <something>", "emote <something>"
  * Navigation is currently restricted to the basics;
    * "go west", "west", etc..
