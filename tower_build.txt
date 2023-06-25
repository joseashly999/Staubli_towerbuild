speed 50 always                      # fixes the robot's speed
tool schunk                          # a customised tool for this particular staubli RX90
count=0
# The robot has been taught four positions SAFE, PICKUP, XPOS and YPOS
set xposnew=xpos
set xposnew=shift(xposnew by 0,40.3,0)
set yposnew=ypos
set yposnew=shift(yposnew by -40.3,0,0)
set a=xpos
set c=ypos
set b=xposnew
set d=yposnew                           # we create new variables so that the taught positions donot change during each iteration



openi                                  # opens the robot arm 
100 move safe                          # moves to the taught position SAFE. the line is given the number 100 so that the arm knows to return to this line after one loop
appro pickup, 50                       # approach the PICKUP position at a distance 50
moves pickup                           # moves to PICKUP positon in a straight line
closei                                 # closing the robot arm
depart 50                              # depart from PICKUP position to a distance 50
moves safe                             # moves to SAFE at a staright line
appro a,50                             # approaches the XPOS position at a distance 50
moves a                                # moving to the position
openi                                  # opening the arm and placing the stick
depart 50                              # departing from the position to a distance 50
move safe
appro pickup,50
moves pickup
closei
depart 50
move safe
appro b,50
moves b
openi
depart 50
move safe
appro pickup,50
moves pickup
closei
depart 50
move safe
appro c,50
moves c
openi
depart 50
appro pickup,50
moves pickup
closei
depart 50
move safe
appro d,50
moves d
openi
depart 50
move safe                  # after placing four stick, in order to build a tower the four positions are shifted to a height as shown below 
                            # along the x, y and z axis. refer README.md to know more

set a=shift(a by 0,0,19.4)
set b=shift(b by 0,0,19.4)
set c=shift(c by 0,0,19.4)
set d=shift(d by 0,0,19.4)
count=count+1             
if count<5 goto 100            # the loop itreates  5 times until the tower is 5 storey high
 

