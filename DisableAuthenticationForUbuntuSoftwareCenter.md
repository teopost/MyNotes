How To Disable Authentication For Ubuntu Software Center
-----

I don't care for typing a password in just to install software in Ubuntu. In fact I don't care for this in any platform, even the app store from Apple on my iPhone. So I've disabled it as I'm the only user of this computer. Here is how to do it:

1. Hold down ALT and press F2, this will bring up the "Run a command" dialogue box.

2. Type this exactly, copy and paste doesn't work here (for me, anyway) into the box:

gksudo gedit /usr/share/polkit-1/actions/org.debian.apt.policy (do not put .xml at the end)

This will open gedit with the proper access for editing this policy, which is owned by ROOT.

3. Hold CTRL and hit F, in the search box copy and paste this:

org.debian.apt.install-or-remove-packages

4. Under the line that says <defaults>, edit the next 3 lines to this:

    <allow_any>yes</allow_any>
    <allow_inactive>yes</allow_inactive>
    <allow_active>yes</allow_active>

5. Hit Save and exit, you do not need to restart Ubuntu.

Now go to the Ubuntu Software Center and find something you wish to install, did it ask for your password?
