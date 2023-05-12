Fprint with Linux

step 1:
    Make sure polkit is installed

Step 2:

    Install fprintd, fprint grosshack

    sudo pacman -S fprintd imagemagick
    paru -S pam-fprint-grosshack

    https://aur.archlinux.org/pam-fprint-grosshack.git
    https://gitlab.com/mishakmak/pam-fprint-grosshack


Step 3:
edit required files in ```/etc/pam.d``` and add the following lines on top

    auth		sufficient  	pam_fprintd_grosshack.so

    auth		sufficient  	pam_unix.so try_first_pass nullok

    auth		sufficient  	pam_fprintd.so


        login:      system local login
        polkit-1:   policy kit authentication popups
        sudo:       use sudo with fingerpeint
        sddm:       login to sddm with fingerprint
        
    add these lines to any other files required to authenticate with fingerprint. 

Step 4:
    enroll fingerprints using
    ```fprintd-enroll```

scan your right index finger for about 5 - 15 times

Step 5:
    verify your fingerprint is working by trying to run a command as sudo
    ```sudo su```
    
    you should be able to use your fingerprint to authenticate sudo


References:
    https://wiki.archlinux.org/title/Fprint
    https://www.freedesktop.org/wiki/Software/fprint/