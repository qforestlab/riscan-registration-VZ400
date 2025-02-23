# Fine co-registration with MSA
After the coarse co-registration, the point clouds are matching but there's still an error on this. To improve the co-registration (reduce this error), we use the MSA algorithm which uses plane patches to match the different scans more closely. 
This can be done after one or multiple scan positions are coarsely registered. The next slides are based on doing the fine registration after one scan position has been coarsely registered.

This shows you an example of the error which may be left after coarse co-registration. See how the point clouds of the two scanpositions (white verus blue color) are not matching.
![RiSCAN_PRO_project](./img/07_fine_co-registration-0.png)

## Steps 
1. Click *Registration*.
2. Click *Multi Station Adjustment*.
3. Click *Start adjustment...*.

![RiSCAN_PRO_project](./img/07_fine_co-registration-1.png)

4. Make sure the registered scan positions are activated by selecting them and right-click.
5. Click *Activate*. A check symbol will apear left next to the scan (see next slide).
6. Make sure the other scan positions which haven't been registered yet are deactivated. If they are activated (checked) do step 1 and click *Deactivate*.

![RiSCAN_PRO_project](./img/07_fine_co-registration-2.png)

7. Make sure the registered scan positions which have already gone through fine co-registration are locked by selecting them and right-click.
8. Click on *Lock position and orientation*. Froozen scan positions (such as ScanPos001) are automatically locked. 

![RiSCAN_PRO_project](./img/07_fine_co-registration-3.png)

9. Make sure the scan position which you want to finely co-register is unlocked by selecting it and right clicking.
10. Click on *Unlock position and orientation*.

![RiSCAN_PRO_project](./img/07_fine_co-registration-4.png)

11. Under *INPUT DATA* make sure *Use plane patches* is indicated. Ignore the tiepoint, tieobjects and measured scan positions.
12. Under *PARAMETERS* the most important one is search radius (which you should choose as the distance you think the error between the two scans is approximately). The other parameters can generally stay unchanged.

![RiSCAN_PRO_project](./img/07_fine_co-registration-5.png)

More information on the other parameters can be found on the help page of RiSCAN PRO:

![RiSCAN_PRO_project](./img/07_fine_co-registration-6.png)

13. To start the adjustment, you set your parameters based on the error you observe.
14. Click *Calculate*. 

![RiSCAN_PRO_project](./img/07_fine_co-registration-7.png)

It can be good to visualise your point clouds (ScanPos001 and ScanPos002 in this case) to see what MSA is doing and if the adjustment is improving the co-registration between scans.

![RiSCAN_PRO_project](./img/07_fine_co-registration-8.png)

15. The numbers under *ΔX, ΔY, ΔZ, ΔRoll* etc. show how much the SOP changed (the point cloud translated and rotated). 
16. Under *STATISTICS*, the *Error (StdDev) [m]* also gives an idea of the resulting error. 

![RiSCAN_PRO_project](./img/07_fine_co-registration-9.png)

17. Generally an *Error (StdDev) [m]* </= 1 cm is good. So you can reduce the *Search radius* to approximately 2 times the error. 
18. Click *Calculate*.
19. Repeat the process till the co-registration looks good/doesn't really change anymore.

![RiSCAN_PRO_project](./img/07_fine_co-registration-10.png)

20. Now the error is below 1 cm. This scan position is finely co-registered now.
21. Right-click the scan position.
22. Click *Lock position and orientation*.
23. IF something went wrong during the MSA adjustment you can undo an adjustment by clicking *Undo last* (which undoes the last adjustment) or *Undo all* (which undoes everything you did since you opened the MSA screen).

![RiSCAN_PRO_project](./img/07_fine_co-registration-11.png)

Now you repeat the coarse and fine registration steps with the next scan position till all the scan positions are finely co-registered.
Because of this sequential process errors can propagate towards the end of the scan positions. Therefore it's advised to run MSA algorithm once more on all the scan positions.

24. Open MSA (see steps 1-3).
25. Activate all scan positions (see steps 4-5). 
26. Unlock all scan positions (see steps 9-10) expect for ScanPos001 which is frozen.
27. Set the *Search radius [m]* to a low number such as 5 cm.
28. Click *Calculate*.

![RiSCAN_PRO_project](./img/07_fine_co-registration-12.png)

It is important to visually check the results of the final co-registration. 
29. Visualise all point clouds in different colors (see previous steps).
30. Set *Top view*.
31. Set *Orthogonal view*.
32. Rotate the point clouds so they are aligned with the X-Y axis in the grid.
33. Click *Selection mode > Shape > Rectangle selection*. 
34. Select the plot based on the scan positions you see.

![RiSCAN_PRO_project](./img/07_fine_co-registration-13.png)

35. Click *Show only selected area*.
36. Click on the *Height filter*.

![RiSCAN_PRO_project](./img/07_fine_co-registration-14.png)

37. Use the *Height filter* to take slices through the plot in both X, Y and Z. 
38. Go through the plot and check the point clouds of different scan positions (in different colors) are matching.
39. If something is off try to correct it using MSA. (see below to know if something is "correctable".)

![RiSCAN_PRO_project](./img/07_fine_co-registration-15.png)

When is something bad registration (and can be fixed) and when is it just wind (and cannot be fixed)?

When you see ghosting effects (an object is in the point cloud multiple times on a slightly different position in different scans) that are mostly present in the branches but not in the stems, with the effect bigger towards the top, this is most likely due to wind. Leaves can easily be moved by wind, therefore we focus on stems to check wether the co-registration is OK. 

![RiSCAN_PRO_project](./img/07_fine_co-registration-16.png)


