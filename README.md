# motor_follow
This project contains two step motors, each have their own optical encoder. The slave motor will follow the master motor's speed.  
The control method is PID control. The pseudo code is as follows.  
The sampling frequency and control frequency is the same. It is 100Hz.
Encoder measure method is STM32 Timer encoder mode. Every timer interrupt the MCU will get the value of the motors' optical encoder and calculate the error.  
error = MASTER_MOTOR_OPTICAL_ENCODER_VALUE - SLAVE_MOTOR_OPTICAL_ENCODER_VALUE   
SLAVE_MOTOR_OPTICAL_ENCODER_VALUE = SLAVE_MOTOR_OPTICAL_ENCODER_VALUE - MASTER_MOTOR_OPTICAL_ENCODER_VALUE   
MASTER_MOTOR_OPTICAL_ENCODER_VALUE = 0  

All the details are in the main.c/HAL_TIM_PeriodElapsedCallback  
  
![image](https://github.com/throwfriedchicken/motor_follow/assets/72564911/3299ea63-da2a-4283-90ff-9748acac4407)
![image](https://github.com/throwfriedchicken/motor_follow/assets/72564911/65236f82-b0d8-4b66-a195-5dfce9104c46)
![image](https://github.com/throwfriedchicken/motor_follow/assets/72564911/0bf5dcb0-5ff6-42f4-aa55-645db833f2f5) 

