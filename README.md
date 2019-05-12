# BentoStarter / Trusted Web Activity

I used [svgomg-twa](https://github.com/GoogleChromeLabs/svgomg-twa) repos from GoogleChromeLabs to create this android app.

This project uses the
[Trusted Web Activities](https://developers.google.com/web/updates/2017/10/using-twa) technology
to wrap [BentoStarter](https://github.com/kefranabg/bento-starter) in an Android Application.

## Running the Demo (from GoogleChromeLabs/svgomg-twa)

1. Clone the project
``
git clone https://github.com/GoogleChromeLabs/svgomg-twa.git
``

2. Import the Project into Android Studio, using File > New > Import Project, and select the folder
to which the project was cloned.

3. Run the Project (Ctrl+R)

### Enabling Debug

TWAs require [Digital AssetLinks](https://developers.google.com/digital-asset-links/) to be setup
on both the application and on the website, in order to enable the validation that allows Chrome to
open the page in full-screen.

For security reasons, the signing key compatible with the setup on
https://svgomg.firebaseapp.com/ is not committed with the sample code.

It is possible to setup Chrome to skip validation on device to enable testing.

Here are the 2 steps required to achieve this:

1. Enable Chrome to accept command-line parameters:

On the Android Device, go to the Chrome version being used to test the TWA and navigate to
`chrome://flags`. Search for a setting called `Enable commmand line on non-rooted devices` and
change it to `Enabled`. Restarting the browser *multiple* times may be required.

2. Create an Android file with the command-line parameters that allow skipping the TWA validation.

Add a file at `/data/local/tmp/chrome-command-line`, with the content
`_ --disable-digital-asset-link-verification-for-url="https://svgomg.firebaseapp.com"`. Make sure
there's not newline at the end of the line, or it may break the launcher.

For convenience, a shell script that creates this file is available in this repository. Run it
by executing `./enable-debug.sh https://svgomg.firebaseapp.com`.

To debug a different PWA, execute the script with a different host:
`./enable-debug.sh https://example.com`
