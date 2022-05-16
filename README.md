# Lucas-Kanade Tracking
This project contains three sections. In the first section, I developed a Lucas-Kanade (LK) tracker with onoe single template. In the seconod section, I Implemented a motion subtraction method for tracking moving pixels in a scene. In the final section, I studied efficient tracking such as inverse composition. Since this is a class assignment, my code is not published on GitHub.

The following two papers are useful for understanding Lucas-Kanade tracking and optical flows:
- [Simon Baker, et al. *Lucas-Kanade 20 Years On: A Unifying Framework: Part 1*, CMU-RI-TR-02-16, Robotics Institute, Carnegie Mellon University, 2002](https://www.ri.cmu.edu/pub_files/pub3/baker_simon_2002_3/baker_simon_2002_3.pdf.)
- [Simon Baker, et al. *Lucas-Kanade 20 Years On: A Unifying Framework: Part 2*, CMU-RI-TR-02-35, Robotics Institute, Carnegie Mellon University, 2002](https://www.ri.cmu.edu/pub_files/pub3/baker_simon_2003_3/baker_simon_2003_3.pdf.)

## How Lucas-Kanade Works
<img src="https://github.com/HonglingLei/Lucas-Kanade-Tracking/blob/main/data/Lucas-Kanade.png" width="700" />
<img src="https://github.com/HonglingLei/Lucas-Kanade-Tracking/blob/main/data/Q1.1.png" width="700" />

*↑ Credit: CMU 16720 Computer Vision assignment 3 writeup*

<img src="https://github.com/HonglingLei/Lucas-Kanade-Tracking/blob/main/data/Q1.1_answer.png" width="600" />


## Tracker 1: Template Matching
The first tracker tracks a particular template that is moving in the scene. For each frame, I extracted a rectangle describing the picel coordinates, and compared it with the previous frame to find the least-different/most-similar area. This is done by iterating until the total pixel changes fall below a threshold. A useful package is `RectBivariateSpline` in `scipy.interpolate`.

However, sometimes the image content we are tracking in the first frame can differ from the one in the last frame, because we update the template after processing each frame and the error can accumulate. This is known as the template drifting problem, and several correction methods are ellaborated in [this paper *The Template Update Problem*](https://www.ri.cmu.edu/pub_files/pub4/matthews_iain_2003_2/matthews_iain_2003_2.pdf) by Iain Matthews et al. I used the strategy 3 mentioned in page 4 for drift correction. When the change from the previous frame to the current one is small enough, I used the previous frame region as the updated template. However, if the extracted area varies too much, I used the original template to correct it to make sure it's on the right track.

I tested my tracker on the following two videos, where my targets were the car and the girl, respectively.
![tracking_girl](https://github.com/HonglingLei/Lucas-Kanade-Tracking/blob/main/data/tracking_girl.gif)

