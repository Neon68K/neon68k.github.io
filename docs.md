---
title: X68000 Games Setup for MiSTer
--- 

The Sharp X68000 computer is a system that uses a lot of different resolutions across 15kHz, 24kHz and 31kHz, so we will need to use the VGA scaler, and add some settings for its more uncommon resolutions.

(The X68000 core also does not support Direct Video (yet?), so if you are using a RetroTink 4K scaler, auto-configuration of the scaler settings will not work — you will have to load a profile manually or just use the defaults.)

Add this configuration to your `MiSTer.ini`:
```
[X68000]
forced_scandoubler=0
vga_scaler=1
direct_video=0

[video=224x496]
vscale_mode=1
video_mode=448,992,60

[video=256x240]
vscale_mode=1
video_mode=256,240,60

[video=256x256]
vscale_mode=1
video_mode=256,256,60

[video=256x512]
vscale_mode=1
video_mode=512,1024,60

[video=304x448]
vscale_mode=1
video_mode=304,448,60

[video=512x240]
vscale_mode=1
video_mode=512,240,60

[video=512x256]
vscale_mode=1
video_mode=512,256,60

[video=512x512]
vscale_mode=1
video_mode=512,512,60

[video=640x480]
vscale_mode=1
video_mode=640,480,60

[video=768x512]
vscale_mode=1
video_mode=768,512,60

[video=1024x1024]
vscale_mode=1
video_mode=1024,1024,60
```

### English + Japanese Games

We have separated out the games where you need to understand Japanese to get any enjoyment out of a game to a separate `Japanese` folder. There are games in the English folder where text or speech is in Japanese, but the games are easy to navigate and play even if you don't know it.

If you *do* understand Japanese, unpack both the `English` and `Japanese` folders, as you can think of it as an add-on pack to the English one.

### Keyboard + Mouse Games

Since not everyone uses MiSTer with a keyboard and mouse — although highly recommended when using the computer cores — we have separated out the games that require that setup to a separate folder. Unpack these if you have the necessary equipment connected to your MiSTer.

### Unpacking the Games

The X68000 core does not support HDFs inside ZIP files. So you will need to unpack the games you want to play.

**Windows:** For unpacking multiple files, on Windows, we recommend using 7zip, selecting all the ZIP files you want, and using the "Extract here" right click menu item. If asked to overwrite duplicate files, just say "Yes to All".

**macOS:** Most of the unpacking apps will unfortunately create a dedicated folder for every game when you unpack (even if they say they won't, like in the case of Keka or The Unarchiver, or the built-in Archive Utility), so the most efficient way is to use the Terminal:

```
cd FolderWithYourFiles
for f in *.zip; do unzip -o "$f" -d ./; done
````

(If you are uncomfortable using the Terminal, just unpack all the files and move the folders manually)

Once unpacked, copy all the folders to the root of your MiSTer. The folders look like this:

```
_Computer
config
docs
games
```

If asked, use the "Merge" option to merge the folders.

### Launching a Game

The games will launch directly from the MiSTer menu, you can find them under `Computer` → `X68000 Games` — there is no need to launch the X68000 core separately. Every time you pick a new game from the list, it will re-load the core and boot the game.


<script>
        document.addEventListener("DOMContentLoaded", function () {
            // Select h3 and below
            const headings = document.querySelectorAll("h3[id], h4[id], h5[id], h6[id]");

            headings.forEach((heading) => {
                // Make the heading clickable
                heading.classList.add("clickable-heading");

                // Add a click event listener that will navigate to the anchor link
                heading.addEventListener("click", function () {
                    const slug = heading.id;
                    window.location.hash = `#${slug}`;
                });

                // Add a visual indicator (e.g., a link icon that appears on hover)
                const linkIcon = document.createElement("span");
                linkIcon.innerHTML = " 🔗";
                linkIcon.style.opacity = "0";
                linkIcon.style.transition = "opacity 0.2s";
                linkIcon.style.fontSize = "80%";

                heading.appendChild(linkIcon);

                // Show the link icon when hovering over the heading
                heading.addEventListener("mouseover", () => {
                    linkIcon.style.opacity = "1";
                });
                heading.addEventListener("mouseout", () => {
                    linkIcon.style.opacity = "0";
                });
            });
        });
</script>
