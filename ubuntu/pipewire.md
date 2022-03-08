
# Pulseaudio -> Pipewire for improved HSP/HFP audio quality
The standard pulseaudio that comes with 20.04 does not support high quality headset mode. Pipewire supports HSP/HFP with mSBC codec using 16 kHZ instead of the standard 8 kHz that CVSD codec offers, resulting in much better audio quality.
Tested with Bose qc35. Installation:

```
# Add ppa for latest pipewire build
sudo add-apt-repository ppa:pipewire-debian/pipewire-upstream
sudo apt update
# Install components
sudo apt install gstreamer1.0-pipewire pipewire-media-session libspa-0.2-bluetooth libspa-0.2-jack pipewire pipewire-audio-client-libraries
# If got problem, you can run:
sudo apt --fix-broken install
# Then re-run
sudo apt install gstreamer1.0-pipewire pipewire-media-session libspa-0.2-bluetooth libspa-0.2-jack pipewire pipewire-audio-client-libraries

# Reload new user services
systemctl --user daemon-reload
# Disable PulseAudio user service
systemctl --user --now disable pulseaudio.service pulseaudio.socket
# Mask PulseAudio user service (to prevent future update from re-enabling it)
systemctl --user mask pulseaudio
# Enable Pipewire user services
systemctl --user --now enable pipewire pipewire-pulse
# Enable Pipewire media session user service
systemctl --user --now enable pipewire-media-session.service
```
Source: https://www.reddit.com/r/pop_os/comments/q9u1uh/enjoy_my_bose_qc35_with_music_and_web_meeting_on/
