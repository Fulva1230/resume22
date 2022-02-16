---
title: Introduction to My Master Research
subtitle: Control of a Mecanum Wheeled Platform

# Summary for listings and search engines
# summary: .

# Link this post with a project
projects: []

# Date published
date: "2022-02-16T12:00:00Z"

# Date updated
lastmod: "2022-02-16T12:00:00Z"

# Is this an unpublished draft?
draft: true

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 'A picture of my MWP'
  focal_point: ""
  placement: 1
  preview_only: false

authors:
- admin

# tags:
# categories:

---

## Overview

A Mecanum wheeled platform (MWP) is a mobile platform able to move in any way. It can move forward and backward, laterally, and turn with a 0 radious. These movements can happen simultaneously so that a MWP can move in a straight line with a changing orientation, or it can move in any direction without changing its orientation as in Fig. [1](#figure-mwp_any_direction).

{{< figure src="omnidirection.png" caption="A MWP can move in any direction without changing its orientation." id="mwp_any_direction" numbered="true">}}

## Control

The motion of a MWP is a nonlinear system. To control it following a pre-defined trajectory or a moving target, simply using linear control technique won't work well. Rather, a nonlinear and more advanced approach is needed. To address the problem, I developed a controller based on a super-twisting controller. Tested in simulations and experiments, the controller was verified to be effective and robust. 

Moreover, the controller is designed to be implemented easily like a PID controller. It doesn't need to simulate a MWP internally. As a result, there is no need to know the weight or dimension of a MWP to control it. It's beneficial because in practice, acquiring such information may be expensive. To implement the controller on a particular MWP, one only needs to program the control law in a micro-controller and tune the parameters. The controller is robust enough so that its performance is insensitive to parameter changes. If the selection of parameters falls in an acceptable range, then the performance is guaranteed.

The following video shows the effectiveness of the proposed controller. The MWP is controlled to follow the red cuboid, which is animated. It is robust enough so that moving or inclined ground, which isn't normally encountered, can even be handled. In a situation like hitting an obstacle, which will abruptly impose an external force on the MWP, the controller can also respond quickly to minimize the distance to its target.
{{< youtube jj2g6hYVu0w >}}

In the experiment, however, the MWP under control is not as smooth and stable as in the simulation, as in the following video. Mecanum wheels require a quite flat and clean ground. The meeting room in the video doesn't satisfy the condition. Moreover, the wheels were not installed on the base precisely enough since we prototyped the MWP quickly. Even a robust controller can not manage such a situation. Although the control in the experiment isn't as precise as in the simulation, stability is still well established. We conclude that the controller is sufficient powerful to be applied in practice.
{{< youtube Ezhma4tzR4k >}}

A potential application of the proposed controller is in autonomous mobile robots (AMR). An autonomous mobile robot should move without human interference. Without a controller, an MWP must be controlled by a driver or operator, which makes it not an AMR. On the other hand, if an AMR can generate a trajectory to follow with some artificial intelligence, with the controller, it can follow the trajectory without a mankind.
