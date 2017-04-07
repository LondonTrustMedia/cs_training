# PIA Support

This repo contains the primary package of support training for PIA.

This website is the sole property of London Trust Media. This confidential website contains trade secrets and proprietary information relating to Private Internet Access and London Trust Media. No use or disclosure of the information contained herein is permitted without the prior written consent of London Trust Media. All marks, trademarks and product names used in this document are the property of their respective owners.


## SOURCE CODE HANDLING

Source code for this site should **only** be handled by LTM. Don't give people outside LTM access to all of the source for this site.

If necessary, you can give them the source for a specific article so they can make changes directly and send it back to you, but make them well aware of the disclaimer above that applies to all material in here.


## Converting Videos

To convert videos to mkv/mp4, I recommend using [Handbreak](https://handbrake.fr). It's a free, open-source video converter that just works brilliantly.


## Preparing

So to get this repo ready (to start testing/building it), do this:

1. Install [Jekyll](https://jekyllrb.com).
2. Copy the videos folder into this repo as `./videos/`.

And afterwards, do one of the following so you can actually use it.


### Build Instructions

1. `jekyll build`
2. Your built site is in `./_site/`.


### Development Instructions

1. `jekyll serve -w`
2. Head to http://localhost:4000/support/
