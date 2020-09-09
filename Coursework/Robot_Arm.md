# Shirt-Folding Robot Arm
September-December 2018 
{: .text-right}

**Introduction to Robotics** is a hands-on course offered by CUHK Department of Mechanical and Automation Engineering. In the course, I learnt about motion planning, kinematics, and dynamics of robotic systems, with help of a real [robotic arm](http://www.cuhk.edu.hk/english/features/darwin-lau.html){:target="_blank" rel="noopener"}. We were also tasked to come up with and demonstrate an innovative idea for the use of the robotic arm, so that we could apply what we learnt in a practical scenario. 

## Idea
I, along with 2 team members, planned to use the robot arm to fold clothes. Since the power the robot arm's motor was not large enough to hold a real shirt, we decided to do a demonstration using a mini-sized shirt.

![](../assets/images/robot arm/shirt.png){:width="60%"}

## End Effector
The flipping motion was achieved by sliding a trapezoidal plank under the shirt and quickly lifting it. To connect the plank and the robot arm, we designed and 3D-printed a revolute joint, so the angle of the plank was fixed between 0 and -45 degree to the horizontal. This design allowed the plank to stay parallel to the table when sliding under the shirt. The range of motion could be adjusted by adjusting the position of the screw. We found that 45 degree worked the best through trials and experimentation. 

![](../assets/images/robot arm/end effector 1.JPG){:width="70%"}

![](../assets/images/robot arm/end effector 2.JPG){:width="70%"}

![](../assets/images/robot arm/end effector 3.JPG){:width="70%"}

## Set Up
The T-shirt is placed on a platform with height 3cm so that the slightly elevated plank can pass through the bottom of the clothes. The platform is about 20cm away from the base of the robot arm.

![](../assets/images/robot arm/set up.jpg){:width="50%"}

## trajectory planning
We used Arduino to program the robot arm's movement. The path of the end effector is designed in the task space and converted to angle command using inverse kinematics. We use cubic trajectory to produce a smoother motion.

Below shows the sequence of motion and the corresponding coordinates:

1. The end effector starts at the position to the right of the T-shirt.
2. The plank slides under the shirt for 5.5cm. 
3. All the servos are disabled so the end effector drops. The plank and the edge of the platform act as a lever and create a flipping motion.
4. The end effector is positioned at the bottom of the shirt. 
5. The end effector slides under the shirt for 7cm.
6. The end effector moves upward, flipping the shirt. 

<style type="text/css">
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0lax">Time (s)</th>
    <th class="tg-0lax">x (mm)</th>
    <th class="tg-0lax">y (mm)</th>
    <th class="tg-0lax">z (mm)</th>
    <th class="tg-0lax"></th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">2~4</td>
    <td class="tg-0lax">120</td>
    <td class="tg-0lax">220</td>
    <td class="tg-0lax">40</td>
    <td class="tg-0lax">(1)</td>
  </tr>
  <tr>
    <td class="tg-0lax">4~5</td>
    <td class="tg-0lax">120 → 65</td>
    <td class="tg-0lax">220 → 320</td>
    <td class="tg-0lax">40 → 30</td>
    <td class="tg-0lax">(2)</td>
  </tr>
  <tr>
    <td class="tg-0lax">5~7</td>
    <td class="tg-0lax">65</td>
    <td class="tg-0lax">320</td>
    <td class="tg-0lax">30</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">7~9</td>
    <td class="tg-0lax">/</td>
    <td class="tg-0lax">/</td>
    <td class="tg-0lax">/</td>
    <td class="tg-0lax">(3)</td>
  </tr>
  <tr>
    <td class="tg-0lax">9~11</td>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax">220</td>
    <td class="tg-0lax">45 → 30</td>
    <td class="tg-0lax">(4)</td>
  </tr>
  <tr>
    <td class="tg-0lax">11~12</td>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax">220 → 290</td>
    <td class="tg-0lax">30</td>
    <td class="tg-0lax">(5)</td>
  </tr>
  <tr>
    <td class="tg-0lax">12~14</td>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax">290</td>
    <td class="tg-0lax">30</td>
    <td class="tg-0lax"></td>
  </tr>
  <tr>
    <td class="tg-0lax">14~15</td>
    <td class="tg-0lax">0</td>
    <td class="tg-0lax">290 → 310</td>
    <td class="tg-0lax">30 → 2000</td>
    <td class="tg-0lax">(6)</td>
  </tr>
</tbody>
</table>

<!--
Time (s)	x (mm)	  y (mm)	  z (mm)	
2~4	      120	      220	      40	      (1)
4~5	      120 → 65	220 → 320	40 → 30	  (2)
5~7	      65	      320	      30	
7~9	      /	        /	        /	        (3)
9~11	    0	        220	      45 → 30	  (4)
11~12	    0	        220 → 290	30	      (5)
12~14	    0	        290	      30	
14~15	    0	        290 → 310	30 → 2000	(6)
-->

## Demonstration
<figure class="video_container">
  <iframe src="https://www.youtube.com/embed/pkln_JUA41Y" frameborder="0" allowfullscreen="true" style="width:100%; height:400px"> </iframe>
</figure>
