# Fbank_MFCC_phthon
  implement fbank and MFCC with python
  
  第一步：读取音频文件，获得data和sample rate，一般进行resample到固定值，避免不同音频采样率；
  
  第二步：预处理，比如归一化、预加重，提升高频特性；
  
  第三步：分帧、加窗，frame的形状是（帧数，帧长）一般帧长25ms，步长10ms
  
  第四步：设置STFT算法的filter大小NFFT；求FFT，输出数据形状（帧数，num_fre）其中num_fre = NFFT/2
  
  第五步：求频谱能量，对每个频率幅值求平方，输出数据形状（帧数，num_fre）
  
  第六步：设置Mel滤波器组，滤波器个数（频率轨道）num_filter、最小频率、最大频率、滤波器分布，计算过滤结果。输出数据形状（帧数，num_filter）
  
  第七步：对过滤器组的输出求log，得到fbank
  
  ==这一步的计算结果就是fbank==
  
  第七步：对fbank计算余弦反变换DCT，得到MFCC，取1:13维，加上每帧能量，共13维，作为每帧的倒谱系数。

# compact in English
  
  1. Frame the signal into short frames.
  
  2. For each frame calculate the periodogram estimate of the power spectrum.
  
  3. Apply the mel filterbank to the power spectra, sum the energy in each filter.
  
  4. Take the logarithm of all filterbank energies.
  
  5. Take the DCT of the log filterbank energies.
  
  6. Keep DCT coefficients 2-13, discard the rest.
