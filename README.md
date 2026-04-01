# Digital-Signal-Processing--FIR-BAND-PASS-FILTER-DESIGN
## AIM:
To generate design of Band Pass FIR digital filter using Window.
## Software Required:
MAT LAB R2012.
## Algorithm:
Step 1: Open MATLAB and Write the program.

Step 2: Read the values of cut off frequency wc.

Step 2: Read the values of Order of the filter N.

Step 3: Find out the desired impulse response of the Band Pass filter Coefficient.

Step 4: Find out the windowing sequence.

Step 5: Plot the magnitude spectrum with x-label and y-label with suitable title.

Step 6: Terminate the program.

## PROGRAM: 
```
clc;
clear all;
close all;

wc1 = input('Enter lower cutoff frequency (in radians): ');
wc2 = input('Enter higher cutoff frequency (in radians): ');
N   = input('Enter the filter length: ');

alpha = (N-1)/2;
eps = 0.001;

n = 0:1:N-1;

% Ideal Band Stop Impulse Response
hd = (sin(pi*(n - alpha + eps)) - ...
     (sin(wc2*(n - alpha + eps)) - sin(wc1*(n - alpha + eps)))) ...
     ./ (pi*(n - alpha + eps));

% Center value correction
hd(alpha+1) = 1 - (wc2 - wc1)/pi;

% Hamming Window
wh = 0.54 - 0.46*cos((2*pi*n)/(N-1));

% Apply window
hn = hd .* wh;

% Frequency response
w = 0:0.01:pi;
h = freqz(hn,1,w);

% Plot
plot(w/pi, abs(h), 'r', 'LineWidth', 2);
xlabel('Normalized Frequency (\times\pi rad/sample)');
ylabel('Magnitude');
title('Band Stop Filter using Hamming Window');
grid on;
```

## OUTPUT:

<img width="685" height="522" alt="image" src="https://github.com/user-attachments/assets/24ddd0ec-ce71-4f19-81cd-d2f31092646d" />


## RESULT:

![WhatsApp Image 2026-04-01 at 14 40 05](https://github.com/user-attachments/assets/c8f83aea-ae35-433e-a760-1c9aae881ba2)

