---
layout: post
title:  "Browse anonymously with Tor Browser"
published: true
tags: 
 - tor
priority: 0.8
---
Using [Tor](https://www.torproject.org/) has never been simpler than nowadays. I decided to install Tor Browser
after a while not using it and found out that the community did an amazing effort to get the best and easiest
experience that is possible. There is no need anymore to install Tor in your system and then to install Tor Browser
independently, it just comes all in one!

# Download Tor Browser

Just open a browser and go to `https://www.torproject.org/download/download-easy.html.en`. Careful, you need to
download 2 files! Apart from the packaged application, download the sig file in order to verify that the download
was not tampered with.

I will use the version 6.5.1 for this post, the latest stable as of writing.

    $ ls -l Downloads
    -rw-rw-r--. 1 user user 70922496 27. Mar 14:32 tor-browser-linux64-6.5.1_en-US.tar.xz
    -rw-rw-r--. 1 user user      801 27. Mar 14:32 tor-browser-linux64-6.5.1_en-US.tar.xz.asc

# Verify the key

This part is not very clear from their 
[documentation](https://www.torproject.org/docs/verifying-signatures.html.en) but you might want to take a look at it
yourself.

Important to note is the Key ID used for signing the download: 0x4E2C6E8793298290. I would recommend taking a look
at it in the [MIT key server](http://pgp.mit.edu/pks/lookup?op=vindex&search=0x4E2C6E8793298290). Don't be afraid
by its contents, it is actually simpler than it looks:

    pub  4096R/93298290 2014-12-15            

    uid Tor Browser Developers (signing key) <torbrowser@torproject.org>
    sig  sig3  93298290 2014-12-15 __________ __________ [selfsig]
    sig  sig   4B7C3223 2014-12-15 __________ __________ Georg Koppen <gk@torproject.org>
    sig  sig   63FEE659 2015-01-13 __________ __________ Erinn Clark <erinn@debian.org>
    sig  exp   5E4FD2FE 2015-02-25 2017-02-26 __________ A Sign Key
    sig  sig   1B678A63 2015-02-26 __________ __________ Nicolas Vigier (boklm) <boklm@mars-attacks.org>
    sig  sig   95C877E5 2015-03-01 __________ __________ Paulo Garcia <macrinus1789@gmail.com>
    sig  sig   906653DD 2015-03-07 __________ __________ Rod Sherwin <rodsherwin@mykolab.com>
    sig  sig3  2CDB8B35 2015-03-11 2020-03-09 __________ Isis! <isis@patternsinthevoid.net>
        Policy URL: https://blog.patternsinthevoid.net/policy.txt
        Notation data: isis@patternsinthevoid.net 0A6A58A14B5946ABDE18E207A3ADB67A2CDB8B35
    sig  sig   8B9E4469 2015-03-15 __________ __________ []
    sig  sig   597ED095 2015-03-16 __________ __________ Keith Ye <kloaler@gmail.com>
    sig  sig   CD62C2F3 2015-03-25 __________ __________ []
    sig  sig   8247DD45 2015-03-25 __________ __________ Adrian Reed Smith (PrimaryKey) <adrianrsmith93@gmail.com>
    sig  sig   29023DF9 2015-04-03 __________ __________ Lunar <lunar@anargeek.net>
    sig  sig   3A98820F 2015-04-06 2019-04-06 __________ Jannis Wiese <mail@janniswiese.com>
    sig  sig   28C2A300 2015-04-09 __________ __________ Steve Revilak <steve@srevilak.net>
    sig  sig   8E4B1E28 2015-04-11 __________ __________ Billy Fielding <bfielding@riseup.net>
    sig  sig   EE80A754 2015-04-16 __________ __________ Adrian Smith (Primary Key) <adrianrsmith93@gmail.com>
    sig  sig   6951B4FA 2015-04-18 __________ __________ Jens Stomber <jens.stomber@gmx.de>
    sig  sig   3B94A7C4 2015-05-19 __________ __________ Allan Javier Aguilar Castillo <allanaguilar@riseup.net>
    sig  sig   11C5A0A8 2015-06-10 __________ __________ []
    sig  sig   1D003298 2015-07-01 __________ __________ Alec Burgdorf <aeburgd@gmail.com>
    sig  sig   0CAAD493 2015-07-08 __________ __________ Ким Николай Герасимович <nikolay.kim@ocrv.ru>
    sig  sig   56C5DD90 2015-07-14 __________ __________ Matthias Kahlenberger <Matthias@Kahlenberger.de>
    sig  sig   B5C852D1 2015-07-23 __________ __________ []
    sig  sig   99C8A397 2015-07-27 __________ __________ Alec Burgdorf <aeburgd@gmail.com>
    sig  sig   9E7383A1 2015-08-05 __________ __________ Corwyn <corwyn@astrally.com>
    sig  sig   9E7383A1 2015-08-05 __________ __________ Corwyn <corwyn@astrally.com>
    sig  sig   9E7383A1 2015-08-22 __________ __________ Corwyn <corwyn@astrally.com>
    sig  sig   EFCBF2ED 2015-08-25 __________ __________ Henri Puchta (privat use) <puchta.h@gmail.com>
    sig  sig3  93298290 2015-08-26 __________ 2020-08-24 [selfsig]
    sig  sig   C4D68105 2015-09-25 __________ __________ Aeris 4K
    sig  sig   CF38B160 2015-09-30 __________ __________ Tom van der Woerdt <info@tvdw.eu>
    sig  sig   3AFA4518 2015-10-02 __________ __________ []
    sig  sig   19F78451 2015-10-03 __________ __________ Roger Dingledine <arma@mit.edu>
    sig  sig   8B223611 2015-10-06 __________ __________ Katharina Schott <kamaschott@posteo.de>
    sig  sig   3F46D41E 2015-10-09 __________ __________ Karsten Loesing <karsten@torproject.org>
    sig  sig2  5FBBDBCE 2015-10-10 2018-10-09 __________ Ximin Luo <infinity0@pwned.gg>
        Policy URL: git://github.com/infinity0/pubkeys.git
    sig  sig   8E092A8D 2015-10-13 __________ __________ Stuart Attenborrow <stuarta0@gmail.com>
    sig  sig2  968F094B 2015-10-18 2019-10-18 __________ Tim Wilson-Brown (teor) <teor2345@gmail.com>
    sig  sig   92D08217 2015-11-19 __________ __________ Jeremy Rapich <jrapich@sigaint.org>
    sig  exp3  93744570 2015-11-22 2016-11-23 __________ Peter M (DFTBA)
    sig  sig   67B4ECEA 2015-12-12 __________ __________ Wang Ting Mao (Wtm/Tim/Mao) <micromaomao@gmail.com>
    sig  sig   140D54E8 2015-12-19 __________ __________ []
    sig  sig   9E7383A1 2015-12-20 __________ __________ Corwyn <corwyn@astrally.com>
    sig  sig   A586D0E6 2015-12-26 __________ __________ #359_m <359@osmocudo.net>
    sig  sig   1249039F 2015-12-31 __________ __________ Wesley G aka Morthawt <morthawt@morthawt.com>
    sig  sig   66C1828D 2015-12-31 __________ __________ TutsTeach <TutsTeach@Outlook.com>
    sig  sig   B692FD6B 2016-01-08 __________ __________ []
    sig  sig   125397BB 2016-01-25 __________ __________ []
    sig  sig   B8E7626C 2016-02-08 __________ __________ soz zos <soz@zos.com>
    sig  sig   CD994F73 2016-03-03 __________ __________ Micah Lee <micah@micahflee.com>
    sig  sig2  6E0E9923 2016-03-03 __________ __________ Mike Tigas <mike@tig.as>
        Policy URL: https://mike.tig.as/pgp/policy/
    sig  sig   1889F2C3 2016-03-11 __________ __________ []
    sig  sig3  84AF7F0C 2016-03-15 __________ __________ Ola Bini <ola@olabini.se>
    sig  sig3  BB77E554 2016-03-15 __________ __________ Ola Bini <obini@thoughtworks.com>
    sig  sig3  C9D6F090 2016-03-15 __________ __________ Ola Bini <ola.bini@riseup.net>
    sig  sig   A611E7D9 2016-03-18 __________ __________ Mon Mon (I'm the Mon) <monny@mon.com>
    sig  sig   A8537894 2016-03-29 __________ __________ Andrea Luzzi (Personale) <epicsj30@gmail.com>
    sig  sig2  DB96AE93 2016-05-02 __________ __________ Mark Henrick <mshenrick@gmail.com>
    sig  sig   111F8875 2016-05-02 __________ __________ shikong <wudimenghuan@gmail.com>
    sig  sig2  DB96AE93 2016-05-19 __________ __________ Mark Henrick <mshenrick@gmail.com>
    sig  sig2  5D7EDDA9 2016-05-21 2020-05-21 __________ Ludger Heide <ludger.heide@gmail.com>
    sig  sig   C413CD98 2016-06-20 __________ __________ []
    sig  sig1  0A7CD172 2016-06-24 2018-06-24 __________ Wilfred de Kok (FSFE Fellow 2876) <wilfred@fsfe.org>
    sig  sig   C9DAF7AA 2016-07-09 __________ __________ Mao Wtm (https://maowtm.org) <micromaomao@gmail.com>
    sig  sig   EEB57015 2016-07-09 __________ __________ []
    sig  sig   CE3A08AB 2016-07-11 __________ __________ KRYPTEIA.ORG (Freedom is what we reap from this way of life, my friend.) <administrator@krypteia.org>
    sig  sig   9DA54065 2016-08-05 __________ __________ Kevin Froman <beardog@firemail.cc>
    sig  sig   EC44CAB7 2016-08-25 __________ __________ wywz999 (123) <1169604427@qq.com>
    sig  sig   51EDFE28 2016-08-25 __________ __________ []
    sig  sig   5754B8AD 2016-08-26 __________ __________ 大禹治水2017 <1169604427@qq.com>
    sig  sig   7C48AFA6 2016-08-27 __________ __________ dfjs2017 <zhyzhx@nsn.com>
    sig  sig   A758227C 2016-08-29 __________ __________ Alexander Chepurko <alexander.chepurko@gmail.com>
    sig  sig   176CEF90 2016-09-02 __________ __________ Ethan R. Jones <doubleplusgood23@gmail.com>
    sig  sig3  2CDB8B35 2016-09-11 2021-09-10 __________ Isis! <isis@patternsinthevoid.net>
        Policy URL: https://blog.patternsinthevoid.net/policy.txt
        Notation data: isis@patternsinthevoid.net 0A6A58A14B5946ABDE18E207A3ADB67A2CDB8B35
    sig  sig   24A4FFDA 2016-09-18 2017-09-18 __________ Big Ron <bigdickronnie@hmamail.com>
    sig  sig   39481D96 2016-09-22 __________ __________ []
    sig  sig   D9AF0B5D 2016-09-29 __________ __________ Emily Shepherd <emily@emilyshepherd.me>
        Policy URL: https://emilyshepherd.me/signing-policy.txt
    sig  sig   A9ED0EBF 2016-10-05 __________ __________ Dustan Ingenthron <dustan@posteo.net>
    sig  sig   7B1CFEC6 2016-10-10 __________ __________ Yuhanon Noble Corcair <fakename@fakeserver.com>
    sig  sig   B0918824 2016-10-10 __________ __________ Seán P. Corcoran <Sean@PCorcoran.com>
    sig  sig   80DE31DA 2016-10-11 __________ __________ TweakerRebel (General signing key) <TweakerRebel@yell.com>
    sig  sig   75BB7E37 2016-10-19 __________ __________ Abhi Kalyan (BrainDelta Official email ID) <abhi@braindelta.com>
    sig  sig   B5C20ED6 2016-10-29 __________ __________ Aleksander Alekseev <mail@eax.me>
    sig  sig3  35A8D2E2 2016-11-12 2020-11-12 __________ Edward Navarro (Personal key EN) <contacto@edwardnavarro.com>
    sig  sig   5BBD8102 2016-11-13 __________ __________ Herr Hitler <adolf@hitler.kaufen>
    sig  sig   D7EC4028 2016-11-15 __________ __________ Thomas Sviund <thomassviund@firemail.cc>
    sig  sig   2F12037E 2016-12-04 __________ __________ Leon Albers <albersle@hs-albsig.de>
    sig  sig   93D3967D 2016-12-05 __________ __________ gandhi run (/0) <gandhi.run@hotmail.fr>
    sig  sig   7E7D7C55 2016-12-06 __________ __________ Deneys De Beer (Personal PGP key) <development@d-software.co.za>
    sig  sig   5656BAD4 2017-01-20 __________ __________ Artem M. (Waale) <waale@protonmail.com>
    sig  sig3  82A9CF81 2017-02-01 __________ __________ anonymous
    sig  sig   2B5F3234 2017-02-03 __________ __________ Brandon Conley <bjconley@aerialdevs.com>
    sig  sig1  C029B916 2017-02-16 2021-02-16 __________ Gluek <mrgluek@gmail.com>
    sig  sig   A9366B4C 2017-03-01 __________ __________ Slizzz' (y) <slizzz@telegram.me>
    sig  sig   A9366B4C 2017-03-01 __________ __________ Slizzz' (y) <slizzz@telegram.me>
    sig  sig   FB470BEE 2017-03-10 __________ __________ Info-Screen <Info-Screen@Info-Screen.me>
    sig  sig   318FB504 2017-03-25 __________ __________ Jay Amorin (jay.amorin) <jay.amorin@gmail.com>

    sub  4096R/F65C2036 2014-12-15            
    sig sbind  93298290 2014-12-15 __________ __________ []
    sig sbind  93298290 2015-08-26 __________ 2017-08-25 []

    sub  4096R/D40814E0 2014-12-15            
    sig sbind  93298290 2014-12-15 __________ __________ []
    sig sbind  93298290 2015-08-26 __________ 2017-08-25 []

    sub  4096R/589839A3 2014-12-15            
    sig sbind  93298290 2014-12-15 __________ __________ []
    sig revok  93298290 2015-08-26 __________ __________ []

    sub  4096R/C3C07136 2016-08-24            
    sig sbind  93298290 2016-08-24 __________ 2018-08-24 []

What matters is to check that core members of the Tor community signed it. In case somebody managed to tamper the
download, you would either find that the signature does not match what you downloaded or that the key used for signing
is a different one, therefore the value in this quick check.

I always work with a subset of the core team:

    Georg Koppen <gk@torproject.org>
    Karsten Loesing <karsten@torproject.org>
    Erinn Clark <erinn@debian.org>

They all appear in the [Core Tor People](https://www.torproject.org/about/corepeople.html.en) page.

# Verify the download

Now the funny part. A couple of commands and we will know if what we downloaded is what we intended to!

Import the key from a key server:

    $ gpg2 --keyserver pgp.mit.edu --recv-keys 0x4E2C6E8793298290

Now verify that the fingerprint is correct:

    $ gpg2 --fingerprint 0x4E2C6E8793298290
    pub   rsa4096 2014-12-15 [C] [expires: 2020-08-24]
          EF6E 286D DA85 EA2A 4BA7  DE68 4E2C 6E87 9329 8290
    uid           [ unknown] Tor Browser Developers (signing key) <torbrowser@torproject.org>
    sub   rsa4096 2014-12-15 [S] [expires: 2017-08-25]
    sub   rsa4096 2014-12-15 [S] [expires: 2017-08-25]
    sub   rsa4096 2016-08-24 [S] [expires: 2018-08-24]

You should see that the fingerprint is EF6E 286D DA85 EA2A 4BA7  DE68 4E2C 6E87 9329 8290.

And finally, verify the download:

    $ gpg2 --verify tor-browser-linux64-6.5.1_en-US.tar.xz.asc tor-browser-linux64-6.5.1_en-US.tar.xz
    gpg: Signature made Mo 06 Mar 2017 16:11:54 CET using RSA key ID D1483FA6C3C07136
    gpg: Good signature from "Tor Browser Developers (signing key) <torbrowser@torproject.org>" [unknown]
    gpg: WARNING: This key is not certified with a trusted signature!
    gpg:          There is no indication that the signature belongs to the owner.
    Primary key fingerprint: EF6E 286D DA85 EA2A 4BA7  DE68 4E2C 6E87 9329 8290
         Subkey fingerprint: A430 0A6B C93C 0877 A445  1486 D148 3FA6 C3C0 7136

The output should say "Good signature" :)

In case you are curious, valid subkeys as of this writing are:

    5242 013F 02AF C851 B1C7  36B8 7017 ADCE F65C 2036
    BA1E E421 BBB4 5263 180E  1FC7 2E1A C68E D408 14E0
    A430 0A6B C93C 0877 A445  1486 D148 3FA6 C3C0 7136

Do not worry for the warning, it just means that the signature isn't trusted by your GnuPG installation. To avoid it
you would need to include any of the signers in your [web of trust](https://en.wikipedia.org/wiki/Web_of_trust).

# Unpack Tor Browser

This is an easy one!

    $ tar xvfJ tor-browser-linux64-6.5.1_en-US.tar.xz

# Add Tor Browser to the menu

I found out that Tor Browser has an option to add itself to your applications menu. Cool feature, Tor Browser team!

    $ cd tor-browser_en-US
    $ ./start-tor-browser.desktop --register-app
    Launching './Browser/start-tor-browser --detach --register-app'...
    Tor Browser has been registered as a desktop app for this user in ~/.local/share/applications/

Time to launch your Tor Browser and start surfing anonymously!
