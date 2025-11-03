# Localhost Server and CPP files for GPIO Triggering the Confetti Poppers.
## Works with UI Interface https://github.com/AdaoH3/electronConfettiApp/tree/master
1. Server recieves time in format 00:00:00 from Electron JS app

2. Inputs seconds into triggerRelayTime C++ makefile through function
--
  @app.route('/trigger_relay', methods=['POST'])
  def trigger_relay():
  result = subprocess.run(['./triggerRelayTime', str_seconds], capture_output=True, text=True) 
4. C++ File
     
  a. Counts seconds till ending (then turns on the motor GPIO pin)
    
  b. Uses another GPIO as a light blinker.
    
    i. Wanted the blinker to speed up as the time gets shorter. To do this, used a timer and recorded my snaps of how fast I wanted the LED to blink at a certain time
      
    ii. After plotted points on an output delay per seconds graph, messed around with different math functions to determine the best way to build up suspense. Ended up using two different exponential functions with different decay rates for start and end and a linear function for intermission.
   
  <img width="873" height="546" alt="image" src="https://github.com/user-attachments/assets/210dbb93-1558-481f-8ef1-08d552f76b0d" /> (Plotted with juypter notebook)
    

6. Drill is triggered and motor spinned until confetti popper strings are pulled. 

