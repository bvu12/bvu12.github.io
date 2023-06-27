---
title: "piano2sheet"
date: 2021-05-03
draft: false
icon: piano2sheet
description: "Converts Synthesia videos to sheet music."
internalUrl: /projects/piano2sheet/
weight: 40
---

{{< alert "github" >}}
Check out the code on [Github](https://github.com/cooldecola/piano2sheet)!
{{< /alert >}}

Converts Synthesia videos to sheet music.

## Demo

![Demo showing that the keyboard notes are being tracked as they are played](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/11_snippet.gif)

## Learning objectives

The story behind this project is that both myself and a friend were interested in the field of Computer Science; however, neither of us knew the first thing about coding. This was the very first project we worked on to see if we had the motivation to learn a new skill on our own time.

- [x] Attempt to learn a programming language (<mark>Python</mark>) through online resources
- [x] Share the knowledge we've learned and encourage each other
- [ ] Wrap up a project together - unfortunately, we got as far as detecting the notes, as seen in the `.gif` above!
- [x] Determine whether or not this is a career we could see ourselves pursuing - the answer to this is an emphatic **YES**

## Technologies used

| Technology                        | Description                                                                                                           |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| [Python](https://www.python.org/) | used in conjunction with `Jupyter` to develop the script                                                              |
| [OpenCV](https://opencv.org/)     | an open-source library with many computer vision tools that were helpful in detecting the keyboard notes being played |

## How does it work

As MIDI keyboards are capable of [exporting key presses to Synthesia](https://www.synthesiagame.com/keyboards/Help/desktop/midi) in a very systematic manner, we can use this to detect which keys are being played, and when.

> **1. The video output is consistently ordered**

There are 52 white keys and 36 black keys on a standard piano.

![Picture of a Synthesia keyboard](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/1_piano.png)

> **2. The key portion can be extracted**

We can crop and threshold the image to identify the keys.

![Cropped and thresholding image of the keyboard](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/2_piano_thresholded.png)

> **3. We can run detection algorithms on the thresholded image**

Check out this GIF that highlights the detected black keys. This can be similarly performed for the white keys.

![Animation of the black keys being deteced](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/3_detect_black_keys.gif)

> **4. From any image, we can perform the same thresholding**

Side-by-side comparison of the raw image and thesholded image.

![Notes played in Synthesia](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/4_raw_snapshot.png)
![Thresholded image](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/5_thresholded_snapshot.png)

> **5. Fully connected notes need to be segmented**

This image shows two distinctly coloured notes that can be thresholded by using a histogram and identifying the peak.

![Two overlapping notes](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/6_segmented_snapshot.png)

The result is:

![First note detected](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/7_pinpoint.png)
![Second note detected](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/9_pinpoint2.png)

> **6. And the full detection run on the image**

![Detection on all notes](https://raw.githubusercontent.com/cooldecola/piano2sheet/main/README_images/10_output.png)

> **7. Perform this on every frame of the video**

[Check out the .gif above](#demo)
