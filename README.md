# Analysis of P, PI and PID Controllers using MATLAB
## Aim:
To analyse the effect of P, PI and PID controllers for the system having open loop transfer function, G(S)=1/(S^2+10S+20) using MATLAB. 
## Apparatus Required:
Computer with MATLAB software

## Theory:
	A controller is a device introduced in the system to modify the error signal and to produce a control signal. 
	The way the controller produces the control signal is called the control action.

Consider the following unity feedback system,
 <img width="823" height="281" alt="image" src="https://github.com/user-attachments/assets/36e49512-cf47-4fec-b00c-f79dc0af1c5f" />

### Proportional (P) Controller:
The proportional controller produces an output, which is proportional to error signal.<br>
u(t)∝e(t) <br>
⇒u(t)=Kpe(t) <br>
Apply Laplace transform on both the sides - <br>
U(s)=KpE(s) <br>
U(s)/E(s)=Kp <br>
Therefore, the transfer function of the proportional controller is Kp.

### Proportional Integral (PI) Controller:
The proportional integral controller produces an output, which is the combination of outputs of the proportional and integral controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s)E(s) <br>
U(s)/E(s)=Kp+Ki/s <br>
Therefore, the transfer function of proportional integral controller is Kp+Kis. <br>

### Proportional Integral Derivative (PID) Controller:
The proportional integral derivative controller produces an output, which is the combination of the outputs of proportional, integral and derivative controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt+ Kd (de(t)/dt) <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s+Kds)E(s) <br>
U(s)/E(s)=Kp+Ki/s+Kd s <br>
Therefore, the transfer function of the proportional integral derivative controller is Kp+Ki/s+Kd s

### Characteristics of Kp, Ki and Kd terms:

Increasing the proportional gain ( ) has the effect of proportionally increasing the control signal for the same level of error. The fact that the controller will "push" harder for a given level of error tends to cause the closed-loop system to react more quickly, but also to overshoot more. Another effect of increasing   is that it tends to reduce, but not eliminate, the steady-state error.
The addition of a derivative term to the controller ( ) adds the ability of the controller to "anticipate" error. With derivative control, the control signal can become large if the error begins sloping upward, even while the magnitude of the error is still relatively small. This anticipation tends to add damping to the system, thereby decreasing overshoot. The addition of a derivative term, however, has no effect on the steady-state error.
The addition of an integral term to the controller ( ) tends to help reduce steady-state error. If there is a persistent, steady error, the integrator builds and builds, thereby increasing the control signal and driving the error down. 
 


## Procedure:
	Open MATLAB software
	Open a new script file.
	Type the program.
	Save and Execute the program.
	Determine the steady state error and analyse the controllers.
## Program: 
### Without Controller (Open loop System)
num=[1]
den=[1 10 20]
sys=tf(num,den)
subplot(2,2,1)
step(sys)
title('open loop system')

### With P-Controller
Kp=300;
c1=pid(Kp)
G1=feedback(c1*sys,1)
subplot(2,2,2)
step(G1)
title('P-CONTROLLER')


### With PI Controller
Kp=30;
Ki=70;
c2=pid(Kp,Ki)
G2=feedback(c2*sys,1)
subplot(2,2,3)
step(G2)
title('Pi-CONTROLLER')

### With PID Controller
Kp=350;
Ki=300;
Kd=50;
c3=pid(Kp,Ki,Kd)
G3=feedback(c3*sys,1)
subplot(2,2,4)
step(G3)
title('Pid-CONTROLLER')

## Output: 
### Without Controller (Open loop System)
![WhatsApp Image 2025-11-11 at 22 50 53_d6b0fef6](https://github.com/user-attachments/assets/1b898fa0-c5f7-45fd-b765-29d6d4213338)



### With P-Controller
![WhatsApp Image 2025-11-11 at 22 50 52_d3393825](https://github.com/user-attachments/assets/ee4f4e5a-42ad-4948-80b1-7434dee262b4)


### With PI Controller
![WhatsApp Image 2025-11-11 at 22 50 52_1186afd5](https://github.com/user-attachments/assets/59359ad2-f7e7-4b89-ab77-54dbd110cbc8)


### With PID Controller
![WhatsApp Image 2025-11-11 at 22 50 53_a2e40f6b](https://github.com/user-attachments/assets/09c4a80e-d83b-4241-a025-0030373e4482)



## Result:
Thus the P, PI and PID controllers for the given system was analysed and the following conclusions were arrived using MATLAB. <br>
### With-out controller 
Delay time = 0.458
Rise time =  0.999
Peak time =  1.56
Settling time = 1.96
Steady State Error = 0
### With P Controller 
Delay time =  0.0887      
Rise time =   0.16       
Peak time =   0.19        
Settling time = 1.1      
Steady State Error = 0.1    
### With PI Controller 
Delay time =  0.303       
Rise time =   0.649           
Peak time =   0.82      
Settling time =  1.87          
Steady State Error =  0.87     
### With PID Controller 
Delay time =   0.0243     
Rise time =    0.0615       
Peak time =    1.04      
Settling time =  0.882          
Steady State Error =  0.018     




