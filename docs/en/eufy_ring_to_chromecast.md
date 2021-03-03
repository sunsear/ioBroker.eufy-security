This installation lets your Eufy doorbell ring on your Google Home speakers (Chromecasts)

1. Install ioBroker, I put it onto a raspberry PI. Instructions [here](https://www.iobroker.net/#en/documentation/install/linux.md)
2. Install and configure eufy-security, instructions [here](https://github.com/sunsear/ioBroker.eufy-security/tree/master/docs/en) (until @bropat merges these back)
3. Install chromecast and script adapters in iobroker (Just find them in the adapters view and press plus
4. Add a new blockly script. You can import mine and start from there. Image below
6. You need to change a few things:
  A. click ringing and navigate to: eufy-security.0 -> [basestation] -> cameras -> [doorbell] -> ringing
  B. Create a speaker group for the evening in Google home and put the name instead of deurbel_avond
  CD. Create a speaker group for the day in Google home and put the name instead of deurbel_overdag
  D. Change the ringtone to something you like. Just find a url online. You can use mine, but it is just that, my voice ;-)
6. Hit save and check the logs and test

