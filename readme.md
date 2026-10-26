# Channel Simulation: Different Signal-to-Noise Ratios for Gaussian Channel (Rayleigh Channel) with BPSK and QPSK Modulation Error Rate Simulation [Attached All MATLAB Code]

MATLABSimulation codeclc\nclose all\nclear\nSNR=0:1:20;                 %SNR variation range\nSNR1=0.5*(10.^(SNR/10));    % Convert the signal-to-noise ratio to Cartesian coordinates\nN=1000000;                  % Simulation points\nM1=2;                       %BPSK\nM2=4;                       %QPSK\nx1=randi([0,1],1,N);         % Generate random signals\nx2=randi([0,3],1,N);\nR=raylrnd(0.5,1,N);         % Generate Rayleigh signal\nh1=pskmod(x1,M1);            %BPSK modulation\nh2=pskmod(x2,M2);            %QPSK modulation\nH1=h1.*R;                   %BPSK through Rayleigh channel\nH2=h2.*R;                   %QPSK through Rayleigh channel\nfor i=1:length(SNR)\n    yAn1=awgn(h1,SNR(i),'measured'); \n    yA1=pskdemod(yAn1,M1);     \n    [bit_A1,~]=biterr(x1,yA1); \n    BPSK_AWGN(i)=bit_A1/N;\n    \n    yAn2=awgn(h2,SNR(i),'measured'); \n    yA2=pskdemod(yAn2,M2);     \n    [bit_A2,~]=biterr(x2,yA2); \n    QPSK_AWGN(i)=bit_A2/N;\n    \n    yRn1=awgn(H1,SNR(i),'measured');\n    yR1=pskdemod(yRn1,M1);     \n    [bit_R1,~]=biterr(x1,yR1);\n    BPSK_Ray(i)=bit_R1/N; \n    \n    yRn2=awgn(H2,SNR(i),'measured');\n    yR2=pskdemod(yRn2,M2);     \n    [bit_R2,~]=biterr(x2,yR2);\n    QPSK_Ray(i)=bit_R2/N; \n    \nend\n% QPSK_t_AWGN=1/2*erfc(sqrt(10.^(SNR/10)/2));   %AWGNUnder the channelQPSKTheoretical bit error rate\n% QPSK_t_Ray = -(1/4)*((1-sqrt(SNR1./(SNR1+1))).^2 + (1-sqrt(SNR1./(SNR1+1))))\n​\n% Draw a graph\nfigure\nsemilogy(SNR,BPSK_AWGN,'r*');hold on;\nsemilogy(SNR,QPSK_AWGN,'yo');\nsemilogy(SNR,BPSK_Ray,':b*');\nsemilogy(SNR,QPSK_Ray,':go'); grid on;\naxis([-1 20 10^-4 1]);\nlegend('BPSK-AWGNSimulation','QPSK-AWGNSimulation','BPSK-RayleighSimulation','QPSK-RayleighSimulation');\ntitle('PSKError performance analysis');\nxlabel('Signal-to-noise ratio (dB)');ylabel('BER');\nMATLABSimulation results  

## Images

![(Channel Simulation)BPSK and QPSK Modulation Bit Error Rate Simulations for Gaussian Channels (Rayleigh Channels) at Different Signal-to-Noise Ratios [Attached: All MATLAB Code]](01.jpg)
![(Channel Simulation)BPSK and QPSK Modulation Bit Error Rate Simulations for Gaussian Channels (Rayleigh Channels) at Different Signal-to-Noise Ratios [Attached: All MATLAB Code]](02.jpg)
![(Channel Simulation)BPSK and QPSK Modulation Bit Error Rate Simulations for Gaussian Channels (Rayleigh Channels) at Different Signal-to-Noise Ratios [Attached: All MATLAB Code]](03.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
