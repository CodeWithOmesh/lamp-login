# 💡 Lamp Login

A sign-up page lit by a desk lamp you can pull. Drag the cord down and the lamp clicks on with a real electrical hum, the light flickers in, and the form glows to life.

**Live demo:** https://codewithomesh.github.io/lamp-login/

**Watch the video:** https://www.youtube.com/@CodeWithOmesh

## Features

- Pull-cord interaction with spring physics (mouse and touch)
- Switch click and 120 Hz hum made with the Web Audio API, no audio files
- Flicker-on light beam and glowing form, all SVG + CSS
- Keyboard accessible (Tab to the cord, press Enter)
- One file, no libraries, no build step

## Run it

Download `index.html` and open it in any browser.

## The hum

```js
const hum = audioCtx.createOscillator();
const humGain = audioCtx.createGain();
hum.type = "sine";
hum.frequency.setValueAtTime(120, now + 0.05);
humGain.gain.setValueAtTime(0.001, now);
humGain.gain.linearRampToValueAtTime(0.06, now + 0.08);
humGain.gain.exponentialRampToValueAtTime(0.001, now + 0.35);
hum.connect(humGain);
humGain.connect(audioCtx.destination);
hum.start(now + 0.05);
hum.stop(now + 0.38);
```

A 120 Hz sine wave is the sound of mains electricity (twice the 60 Hz grid). The gain fades in fast and decays exponentially, so it sounds like a soft "vmm" instead of a click.

## Note

The form is a demo: it doesn't send data anywhere. Connect the submit handler to your own backend to use it for real.

## Credits

Idea inspired by a lamp login animation shared on social media. Hum code adapted from the original post.

---

Made by **Code with Omesh** · Follow for more satisfying things built with code.
