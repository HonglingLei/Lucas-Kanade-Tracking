# Lucas-Kanade Tracking
This project contains three sections. In the first section, I developed a Lucas-Kanade (LK) tracker with onoe single template. In the seconod section, I Implemented a motion subtraction method for tracking moving pixels in a scene. In the final section, I studied efficient tracking such as inverse composition. Since this is a class assignment, my code is not published on GitHub.


## Concepts and Mathematics
### Useful Resources
The following two papers are useful for understanding Lucas-Kanade tracking and optical flows:
- [Simon Baker, et al. *Lucas-Kanade 20 Years On: A Unifying Framework: Part 1*, CMU-RI-TR-02-16, Robotics Institute, Carnegie Mellon University, 2002](https://www.ri.cmu.edu/pub_files/pub3/baker_simon_2002_3/baker_simon_2002_3.pdf.)
- [Simon Baker, et al. *Lucas-Kanade 20 Years On: A Unifying Framework: Part 2*, CMU-RI-TR-02-35, Robotics Institute, Carnegie Mellon University, 2002](https://www.ri.cmu.edu/pub_files/pub3/baker_simon_2003_3/baker_simon_2003_3.pdf.)

### How Lucas-Kanade Works
In the scenario of two-dimensional tracking with a pure translation warp function, W(x; p) = x + p. 
