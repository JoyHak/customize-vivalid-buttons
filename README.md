Customize the visible buttons in Vivaldi as you like! Change the position, icons, color, size and make the extension icons truly monochrome! You can place buttons and extensions wherever you like, add or remove spaces, and make the toolbar *compact*, `w i d e` or **HUGE**! 

![](screenshots/promo1.png)
![](screenshots/promo2.png)

# Let's get started

1. Download the archive with all the files:
![](screenshots/download.png)   

2. Go to `C:\Program Files\Vivaldi\Application`

3. Open the *version* folder.

4. Go to `resources\vivaldi`

5. Copy the `window.html`, `public.js` files here and skip next step.

6.  Open the `window.html`. After the element `<body>` add the following line: `<script src="customise_buttons.js"/></script>`

7. Open the `public.js`. For each button you want to customize, create/copy a code block that should look like this:
![](screenshots/files.png)   

8. Read the rules on how to work with these parameters. Explore already existing code blocks to better understand what values to enter!

   > Parameters you are not interested in can be blank:  `' '`. The `buttons` config must not contain **extensions**, and the `extensions` config must not contain **buttons**!  

I recommend you use these mods in conjunction with the script:
- https://github.com/JoyHak/Vivaldi-CSS-mods
- https://github.com/quartz1216/vivaldi-gutter

# If you encounter any issues
![](screenshots/console.png)

1. Type `vivaldi:inspect/#apps` in your browser or open `open_console.lnk`.

2. Find the line that contains `window.html`

3. Click `inspect`.

4. Click the `console` tab. Read the errors and fix them in the script.

If something is still not working **after your fixes**, [open the issue](https://github.com/JoyHak/customize-vivaldi-buttons/issues/new/choose) or or go to the [topic on the forum](https://forum.vivaldi.net/post/803412). Don't forget to attach a screenshot and a description of the problem!

# Performance

I optimised not only the speed but also the readability of the script. I documented many optimisation tricks. Customizing 10 normal buttons, changing and moving 4 extensions, changing 4 extensions on another toolbar takes just from 7ms to 11ms: 
![](screenshots/profiling_0.png)
![](screenshots/profiling_1.png)

I will be glad if you suggest improvements and innovations and find a workaround to the limitations.

# Limitations

- I can't move buttons from invisible panes: if I close the status bar, I can't move any button from it.

- After adding tabs to the tab bar, the svg icon's height attribute disappears, making it invisible. Fixed by assigning it manually.

- Can't load SVG/PNG icons from disc: browser gives `fetch error`. Not fixed in any way. 

- Animation and position of extension popup window needs to be calculated somehow, the window sometimes moves off the screen.  

- I never got over the mutation observer, as it entered a perpetual loop after observing the toolbar: mutation observer generates a change, which triggers mutation observer, which generates a change, ... 
  I had the idea of assigning a hidden html class to the panel that would tell the observer ‘stop, everything is fine, buttons added’, but I never got round to implementing it.

- Initialisation of the script should be done via 
  `addEventListener(‘DOMContentLoaded’, (event) => {})`, but I haven't tested this feature
