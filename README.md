title: TFS-lab
description: Ontwikkelstraat met release management
author: Peter van Hemert
created:  2016 Sept 15
modified: 2016 Sept 15

---
# TFS-DevLab
Ontwikkelstraat met release management.

---

Install Hyper-V on windows 10
-----------------------------
1. Right click on the Windows button and select ‘Programs and Features’.

2. Select Turn Windows Features on or off.

3. Select Hyper-V and click OK.
 
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/enable_role_Hyper-V.png)

---

Create a Virtual Switch.
------------------------
Before you create a virtual machine in Hyper-V, you may want to provide a way for this virtual machine to connect to a physical network. Hyper-V includes software-based networking technology that allows a virtual machine's network card to connect to a virtual switch, providing network connectivity. Each virtual switch created in Hyper-V can be configured with one of three connection types:

* External Network – the virtual switch is connected to a physical network adapter which provides connectivity between the physical network, the Hyper-V host, and the virtual machine. In this configuration, you can also enable or disable the host's ability to communicate over the physically connected network card. This can be useful to isolate only VM traffic to a particular physical network card.

* Internal Network – the virtual switch is not connected to a physical network adapter. However, network connectivity exists between the Hyper-V host and any virtual machines connected to this switch.

* Private Network – the virtual switch is not connected to a physical network adapter and connectivity does not exist between the Hyper-V host and any virtual machines connected to this switch.

This exercise walks through how to create an external virtual switch using the Hyper-V Manager. When completed, your Hyper-V host contains a virtual switch that can be used to connect virtual machines to a physical network.

1. Open up Hyper-V Manager.

2. Right-click on the name of the Hyper-V host and select Virtual Switch Manager...

3. Under ‘Virtual Switches’, select New virtual network switch.

4. Under ‘What type of virtual switch do you want to create?’, select External.

5. Select the Create Virtual Switch button.

6. Under ‘Virtual Switch Properties’, give the new switch a name such as External VM Switch.

7. Under ‘Connection Type’, ensure that External Network has been selected.

8. Select the physical network card to be paired with the new virtual switch. This is the network card that is physically connected to the network.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/newswitch_upd.png)

9. Select Apply to create the virtual switch. At this point you will most likely see the following message. Click Yes to continue.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/pen_changes_upd.png)

10. Select OK to close the Virtual Switch Manager Window.

---

Create a Virtual Machine with Hyper-V Manager.
----------------------------------------------

These steps walk through how to manually create a virtual machine and deploy an operating system to this virtual machine.

1. In Hyper-V Manager, click Action > New > Virtual Machine to bring up the New Virtual Machine Wizard.

2. Review the ‘Before You Begin’ content and click Next.

3. Give the virtual machine a name.</br>
``Note: This is the name Hyper-V uses for the virtual machine, not the computer name given to the guest operating system that will be deployed inside the virtual machine.``

4. Choose a location where the virtual machine files will be stored such as c:\virtualmachine. You can also accept the default location. Click Next when done.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/new_vm_upd.png)

5. Select a generation for the machine and click Next.</br>
Generation 2 virtual machines were introduced with Windows Server 2012 R2 and provide a simplified virtual hardware model and some additional functionality. You can only install a 64-bit operating system on a Generation 2 virtual machine. For more information on Generation 2 virtual machines, see the Generation 2 Virtual Machine Overview.</br>
``If the new virtual machine is configured as Generation 2 and will be running a Linux distribution, secure boot will need to be disabled. For more information on secure boot, see Secure Boot.``

6. Select 2048 MB for the Startup Memory value and leave Use Dynamic Memory selected. Click the Next button.</br>
Memory is shared between a Hyper-V host and the virtual machine running on the host. The number of virtual machines that can run on a single host is in part dependent on available memory. A virtual machine can also be configured to use Dynamic Memory. When enabled, dynamic memory reclaims unused memory from the running virtual machine. This allows more virtual machines to run on the host. For more information on Dynamic Memory, see the Hyper-V Dynamic Memory Overview.

7. On the Configure Networking wizard, select a virtual switch for the virtual machine and click Next. For more information, see Create a Virtual Switch.

8. Give the virtual hard drive a name, select a location or keep the default, and finally specify a size. Click Next when ready.</br>
A virtual hard drive provides storage for a virtual machine similar to a physical hard drive. A virtual hard drive is required so that you can install an operating system on the virtual machine.</br></br>
![](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/new_vhd_upd.png)

9. On the Installation Options wizard, select Install an operating system from a bootable image file and then select an operating system .iso file. Click Next once completed.</br>
When creating a virtual machine, you can configure some operating system installation options. The three options available are:</br>
- Install an operating system later – this option makes no additional modification to the virtual machine.
- Install an operating system from a bootable image file – this is similar to inserting a CD into the physical CD-ROM drive of a physical computer. To configure this option, select a .iso image. This image will be mounted to the virtual CD-ROM drive of the virtual machine. The boot order of the virtual machine is changed to boot first from the CD-ROM drive.
- Install an operating system from a network-based installation server – This option is not available unless you have connected the virtual machine to a network switch. In this configuration, the virtual machine attempts to boot from the network.

10. Review the virtual machine details and click Finish to complete the virtual machine creation.






Solarized
=========

## Precision colors for machines and people

[![solarized dualmode](https://github.com/petervanhemert/TFS-DevLab/blob/master/Images/enable_role_Hyper-V.png)](#features)

Solarized is a sixteen color palette (eight monotones, eight accent colors)
designed for use with terminal and gui applications. It has several [unique
properties](#features). I designed this colorscheme with both precise
[CIELAB](http://en.wikipedia.org/wiki/Lab_color_space) lightness relationships
and a refined set of hues based on fixed color wheel relationships. It has been
tested extensively in real world use on color calibrated displays (as well as
uncalibrated/intentionally miscalibrated displays) and in a variety of lighting
conditions.

***See the [changelog] for what's new in the most recent release.***

![solarized palette](https://github.com/altercation/solarized/raw/master/img/solarized-palette.png)

![solarized vim](https://github.com/altercation/solarized/raw/master/img/solarized-vim.png)

Currently available in formats for (cf [screenshots](#screenshots) below):

### Editors & IDEs

*   **Vim** by [me](https://github.com/altercation) (the Vim-only portion of Solarized is
    [available here](https://github.com/altercation/vim-colors-solarized), for use with
    Pathogen, etc.). See also the [Vim README](http://ethanschoonover.com/solarized/vim-colors-solarized).
*   **Emacs** courtesy of [Greg Pfeil](http://blog.technomadic.org)
    ([@sellout](http://twitter.com/sellout))
    in the main repo and in a [standalone repository][Emacs Repository]
*   **IntelliJ IDEA**
    courtesy of [Johan Kaving](https://github.com/jkaving) and
    ([@flangy](http://twitter.com/flangy))
    in the main repo and in a [standalone repository][IntelliJ Repository]
*   **NetBeans** courtesy of [Brian Fenton](https://github.com/fentie) and
    in the main repo and in a [standalone repository][NetBeans Repository]
*   **SeeStyle theme for Coda & SubEthaEdit** courtesy of
    [Justin Hileman](http://justinhileman.com/)
    ([@bobthecow](http://twitter.com/bobthecow)),
    in the main repo and in a
    [standalone repository][SeeStyle-Coda-SubEthaEdit Repository]
*   **TextMate** --- ***NOTE:*** Dark Theme is work in progress\
    courtesy of [Tom Martin](http://thedeplorableword.net/)
    ([@deplorableword](http://twitter.com/deplorableword))
    in the main repo and in a [standalone repository][TextMate Repository]
    (with key work from [Mark Story](http://mark-story.com)
    and [Brian Mathiyakom](http://brian.rarevisions.net))
*   **TextWrangler & BBEdit** courtesy of [Rui Carmo](http://the.taoofmac.com)
    ([@taoofmac](http://twitter.com/taoofmac))
    in the main repo and in a [standalone repository][TextWrangler-BBEdit Repository]
*   **Visual Studio** courtesy of [David Thibault](http://www.leddt.com)
    ([@leddt](http://twitter.com/leddt))
    in the main repo and in a [standalone repository][Visual Studio Repository]

*   **Xcode** work in progress ports are available for [Xcode 3] and [Xcode 4]
    and will be pulled into the main Solarized project soon.

### Terminal Emulators

* **Xresources** / Xdefaults
* **iTerm2**
* **OS X Terminal.app**
* **Putty** courtesy [Brant Bobby](http://www.control-v.net)
    and on [GitHub](https://github.com/brantb)
* **Xfce terminal** courtesy [Sasha Gerrand](http://sgerrand.com)
    and on [GitHub](https://github.com/sgerrand)

### Other Applications

*   **Mutt** e-mail client also by [me] (*just* the Mutt colorscheme is
    [available here][Mutt Repository])

### Palettes

* **Adobe Photoshop** Palette (inc. L\*a\*b values)
* **Apple Color Picker** Palettes
* **GIMP** Palette

Don't see the application you want to use it in? Download the palettes (or pull
the values from the table below) and create your own. Submit it back and I'll
happily note the contribution and include it on this page.  See also the
[Usage & Development](#usage-development) section below for details on the
specific values to be used in different contexts.

Download
--------

### [Click here to download latest version](http://ethanschoonover.com/solarized/files/solarized.zip)

Current release is **v1.0.0beta2**. See the [changelog] for details on what's
new in this release.

### Fresh Code on GitHub

You can also use the following links to access application specific downloads
and git repositories:

*   **Canonical Project Page:**

    Downloads, screenshots and more information are always available from the
    project page: <http://ethanschoonover.com/solarized>

*   **Full Git Repository:**

    The full git repository is at: <https://github.com/altercation/solarized>
    Get it using the following command:

        $ git clone git://github.com/altercation/solarized.git

*   **Application Specific Repositories:**

    You can clone repositories specific to many of the application specific
    color themes. See links in the list above or select from this list:

    * [Vim Repository]
    * [Mutt Repository]
    * [Emacs Repository]
    * [IntelliJ Repository]
    * [NetBeans Repository]
    * [SeeStyle-Coda-SubEthaEdit Repository]
    * [TextMate Repository]
    * [TextWrangler-BBEdit Repository]
    * [Visual Studio Repository]

    * [Xcode 3 work in progress][Xcode 3]
    * [Xcode 4 work in progress][Xcode 4]

Note that through the magic of [git-subtree](https://github.com/apenwarr/git-subtree)
these repositories are all kept in sync, so you can pull any of them and get the most up-to-date version.

Features
--------

1. **Selective contrast**

    On a sunny summer day I love to read a book outside. Not right in the sun;
    that's too bright. I'll hunt for a shady spot under a tree. The shaded
    paper contrasts with the crisp text nicely. If you were to actually measure
    the contrast between the two, you'd find it is much lower than black text
    on a white background (or white on black) on your display device of choice.
    Black text on white from a computer display is akin to reading a book in
    direct sunlight and tires the eye.

    ![solarized selective contrast](https://github.com/altercation/solarized/raw/master/img/solarized-selcon.png)

    Solarized reduces *brightness contrast* but, unlike many low contrast
    colorschemes, retains *contrasting hues* (based on colorwheel relations)
    for syntax highlighting readability.

2. **Both sides of the force**

    ![solarized dualmode](https://github.com/altercation/solarized/raw/master/img/solarized-dualmode.png)

    I often switch between dark and light modes when editing text and code.
    Solarized retains the same selective contrast relationships and overall
    feel when switching between the light and dark background modes. A *lot* of
    thought, planning and testing has gone into making both modes feel like
    part of a unified colorscheme.

3. **16/5 palette modes**

    ![solarized palettes](https://github.com/altercation/solarized/raw/master/img/solarized-165.png)

    Solarized works as a sixteen color palette for compatibility with common
    terminal based applications / emulators. In addition, it has been carefully
    designed to scale down to a variety of five color palettes (four base
    monotones plus one accent color) for use in design work such as web design.
    In every case it retains a strong personality but doesn't overwhelm.

5.  **Precision, symmetry**

    ![solarized symmetry](https://github.com/altercation/solarized/raw/master/img/solarized-sym.png)

    The monotones have symmetric CIELAB lightness differences, so switching
    from dark to light mode retains the same perceived contrast in brightness
    between each value. Each mode is equally readable. The accent colors are
    based off specific colorwheel relations and subsequently translated to
    CIELAB to ensure perceptual uniformity in terms of lightness. The hues
    themselves, as with the monotone \*a\*b values, have been adjusted within
    a small range to achieve the most pleasing combination of colors.

    See also the [Usage & Development](#usage-development) section below for
    details on the specific values to be used in different contexts.

    This makes colorscheme inversion trivial. Here, for instance, is a sass
    (scss) snippet that inverts solarized based on the class of the html tag
    (e.g. `<html class="dark red">` to give a dark background with red accent):

        $base03:    #002b36;
        $base02:    #073642;
        $base01:    #586e75;
        $base00:    #657b83;
        $base0:     #839496;
        $base1:     #93a1a1;
        $base2:     #eee8d5;
        $base3:     #fdf6e3;
        $yellow:    #b58900;
        $orange:    #cb4b16;
        $red:       #dc322f;
        $magenta:   #d33682;
        $violet:    #6c71c4;
        $blue:      #268bd2;
        $cyan:      #2aa198;
        $green:     #859900;
        @mixin rebase($rebase03,$rebase02,$rebase01,$rebase00,$rebase0,$rebase1,$rebase2,$rebase3)
        {
            background-color:$rebase03;
            color:$rebase0;
            * { color:$rebase0; }
            h1,h2,h3,h4,h5,h6 { color:$rebase1; border-color: $rebase0; }
            a, a:active, a:visited { color: $rebase1; }
        }
        @mixin accentize($accent) {
            a, a:active, a:visited, code.url { color: $accent; }
            h1,h2,h3,h4,h5,h6 {color:$accent}
        }
        /* light is default mode, so pair with general html definition */
        html, .light { @include rebase($base3,$base2,$base1,$base0,$base00,$base01,$base02,$base03)}
        .dark  { @include rebase($base03,$base02,$base01,$base00,$base0,$base1,$base2,$base3)}
        html * {
            color-profile: sRGB;
            rendering-intent: auto;
        }

    See also [the full css stylesheet for this site](https://github.com/altercation/ethanschoonover.com/blob/master/resources/css/style.css).

Installation
------------

Installation instructions for each version of the colorscheme are included in
the subdirectory README files. Note that for Vim (and possibly for Mutt) you
may want to clone the specific repository (for instance if you are using
Pathogen). See the links at the top of this file.

Font Samples
------------

Solarized has been designed to handle fonts of various weights and retain
readability, from the classic Terminus to the beefy Menlo.

![font samples - light](https://github.com/altercation/solarized/raw/master/img/solarized-fontsamples-light.png)
![font samples - dark](https://github.com/altercation/solarized/raw/master/img/solarized-fontsamples-dark.png)

Clockwise from upper left: Menlo, Letter Gothic, Terminus, Andale Mono.

Preview all code samples in specific font faces by selecting a link from this
list:

* [DejaVu Sans 18](http://ethanschoonover.com/solarized/img/dejavusans18/)
* [DejaVu Sans 14](http://ethanschoonover.com/solarized/img/dejavusans14/)
* [Letter Gothic 18](http://ethanschoonover.com/solarized/img/lettergothic18/)
* [Letter Gothic 14](http://ethanschoonover.com/solarized/img/lettergothic14/)

* [Andale Mono 14](http://ethanschoonover.com/solarized/img/andalemono14/)
* [Monaco 14](http://ethanschoonover.com/solarized/img/monaco14/)
* [Skyhook Mono 14](http://ethanschoonover.com/solarized/img/skyhookmono14/)

* [Terminus 12](http://ethanschoonover.com/solarized/img/terminus12/)
* [Terminus 20](http://ethanschoonover.com/solarized/img/terminus20/)

Screenshots
-----------

Click to view.

### Mutt

[![mutt dark](https://github.com/altercation/solarized/raw/master/img/screen-mutt-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-mutt-dark.png)
[![mutt light](https://github.com/altercation/solarized/raw/master/img/screen-mutt-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-mutt-light.png)

### C (Vim)

[![c dark](https://github.com/altercation/solarized/raw/master/img/screen-c-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-c-dark.png)
[![c light](https://github.com/altercation/solarized/raw/master/img/screen-c-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-c-light.png)

### Haskell (Vim)

[![haskell dark](https://github.com/altercation/solarized/raw/master/img/screen-haskell-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-haskell-dark.png)
[![haskell light](https://github.com/altercation/solarized/raw/master/img/screen-haskell-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-haskell-light.png)

### HTML (Vim)

[![html dark](https://github.com/altercation/solarized/raw/master/img/screen-html-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-html-dark.png)
[![html light](https://github.com/altercation/solarized/raw/master/img/screen-html-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-html-light.png)

### Java (Vim)

[![java dark](https://github.com/altercation/solarized/raw/master/img/screen-java-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-java-dark.png)
[![java light](https://github.com/altercation/solarized/raw/master/img/screen-java-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-java-light.png)

### Javascript (Vim)

[![javascript dark](https://github.com/altercation/solarized/raw/master/img/screen-javascript-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-javascript-dark.png)
[![javascript light](https://github.com/altercation/solarized/raw/master/img/screen-javascript-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-javascript-light.png)

### Pandoc Markdown (Vim)

These screen shots show Vim running with my own [Pandoc Kit Syntax](http://ethanschoonover.com/pandockit/).

[![pandoc dark](https://github.com/altercation/solarized/raw/master/img/screen-pandoc-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-pandoc-dark.png)
[![pandoc light](https://github.com/altercation/solarized/raw/master/img/screen-pandoc-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-pandoc-light.png)

### Perl (Vim)

[![perl dark](https://github.com/altercation/solarized/raw/master/img/screen-perl-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-perl-dark.png)
[![perl light](https://github.com/altercation/solarized/raw/master/img/screen-perl-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-perl-light.png)

### PHP (Vim)

[![php dark](https://github.com/altercation/solarized/raw/master/img/screen-php-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-php-dark.png)
[![php light](https://github.com/altercation/solarized/raw/master/img/screen-php-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-php-light.png)

### Python (Vim)

[![python dark](https://github.com/altercation/solarized/raw/master/img/screen-python-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-python-dark.png)
[![python light](https://github.com/altercation/solarized/raw/master/img/screen-python-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-python-light.png)

### Ruby (Vim)

[![ruby dark](https://github.com/altercation/solarized/raw/master/img/screen-ruby-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-ruby-dark.png)
[![ruby light](https://github.com/altercation/solarized/raw/master/img/screen-ruby-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-ruby-light.png)

### Shell (Vim)

[![shell dark](https://github.com/altercation/solarized/raw/master/img/screen-shell-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-shell-dark.png)
[![shell light](https://github.com/altercation/solarized/raw/master/img/screen-shell-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-shell-light.png)

### TeX (Vim)

[![tex dark](https://github.com/altercation/solarized/raw/master/img/screen-tex-dark-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-tex-dark.png)
[![tex light](https://github.com/altercation/solarized/raw/master/img/screen-tex-light-th.png)](https://github.com/altercation/solarized/raw/master/img/screen-tex-light.png)

The Values
----------

L\*a\*b values are canonical (White D65, Reference D50), other values are
matched in sRGB space.

    SOLARIZED HEX     16/8 TERMCOL  XTERM/HEX   L*A*B      RGB         HSB
    --------- ------- ---- -------  ----------- ---------- ----------- -----------
    base03    #002b36  8/4 brblack  234 #1c1c1c 15 -12 -12   0  43  54 193 100  21
    base02    #073642  0/4 black    235 #262626 20 -12 -12   7  54  66 192  90  26
    base01    #586e75 10/7 brgreen  240 #585858 45 -07 -07  88 110 117 194  25  46
    base00    #657b83 11/7 bryellow 241 #626262 50 -07 -07 101 123 131 195  23  51
    base0     #839496 12/6 brblue   244 #808080 60 -06 -03 131 148 150 186  13  59
    base1     #93a1a1 14/4 brcyan   245 #8a8a8a 65 -05 -02 147 161 161 180   9  63
    base2     #eee8d5  7/7 white    254 #e4e4e4 92 -00  10 238 232 213  44  11  93
    base3     #fdf6e3 15/7 brwhite  230 #ffffd7 97  00  10 253 246 227  44  10  99
    yellow    #b58900  3/3 yellow   136 #af8700 60  10  65 181 137   0  45 100  71
    orange    #cb4b16  9/3 brred    166 #d75f00 50  50  55 203  75  22  18  89  80
    red       #dc322f  1/1 red      160 #d70000 50  65  45 220  50  47   1  79  86
    magenta   #d33682  5/5 magenta  125 #af005f 50  65 -05 211  54 130 331  74  83
    violet    #6c71c4 13/5 brmagenta 61 #5f5faf 50  15 -45 108 113 196 237  45  77
    blue      #268bd2  4/4 blue      33 #0087ff 55 -10 -45  38 139 210 205  82  82
    cyan      #2aa198  6/6 cyan      37 #00afaf 60 -35 -05  42 161 152 175  74  63
    green     #859900  2/2 green     64 #5f8700 60 -20  65 133 153   0  68 100  60

Usage & Development
-------------------

If you are considering developing a port for Solarized, please see also the
[developer notes](http://ethanschoonover.com/solarized/DEVELOPERS) for
information about optional repository structure and readme formats.

Solarized flips between light and dark modes. In each mode, four monotones form
the core values (with an optional fifth for emphasized content).

![value samples - dark](https://github.com/altercation/solarized/raw/master/img/solarized-values-dark.png)

![value samples - light](https://github.com/altercation/solarized/raw/master/img/solarized-values-light.png)

Thus in the case of a dark background colorscheme, the normal relationship for
background and body text is `base03:base0` (please note that body text is
**not** `base00`).  Note also that in cases where the background and foreground
can be specified as a pair value, text can be highlighted using a combination
of `base02:base1`. The L\*a\*b lightness difference between `base03:base0` and
`base02:base1` is identical by design, resulting in identical readability
against both normal and highlighted backgrounds. An example use case is folded
text in Vim which uses `base02` for the background and `base1` for the
foreground.

The values in this example are simply inverted in the case of a light
background.



[Vim Repository]: https://github.com/altercation/vim-colors-solarized
[Mutt Repository]: https://github.com/altercation/mutt-colors-solarized
[Emacs Repository]: https://github.com/sellout/emacs-color-theme-solarized
[IntelliJ Repository]: https://github.com/jkaving/intellij-colors-solarized
[NetBeans Repository]: https://github.com/fentie/netbeans-colors-solarized
[SeeStyle-Coda-SubEthaEdit Repository]: https://github.com/bobthecow/solarized-seestyle
[TextMate Repository]: https://github.com/deplorableword/textmate-solarized
[TextWrangler-BBEdit Repository]: https://github.com/rcarmo/textwrangler-bbedit-solarized
[Visual Studio Repository]: https://github.com/leddt/visualstudio-colors-solarized
[Xcode 3]: https://github.com/shayne/solarized/tree/master/apple-xcode3-solarized
[Xcode 4]: https://github.com/brianmichel/solarized/tree/master/apple-xcode4-solarized
[me]: http://ethanschoonover.com/colophon
[changelog]: http://ethanschoonover.com/solarized/CHANGELOG
[Vim README]: http://ethanschoonover.com/solarized/vim-colors-solarized
