# Data-transmission-through-sound in python

Part of IDP-EE2025 Course.

### Delatiled Description of Project

Given a data file (eg.text_file,image...) . We need to send this message from device to another using sound. 
For example , we have two laptops, so transmitter(speaker) of one laptop sends the audio signal of the encoded message to reciever(microphone) of other laptop and the reciever decodes the message and prints the file. Here the mode of transmission is audio.

### Setup
The project requires pyaudio, it can be installed via ```pip install``` after the prerequisite portaudio library has been installed.

	pip install pyaudio

### Convert the data file to bits

Here a binary image file of MONALISA is considered.

- Load the binary image 
   
      MonaLisa=np.load('binary_image.npy')
      
### Perform 4-QAM Modulation

As the continuous time modulation is not possible we need to discretise it with sampling freq of 50MHz and freq of modulation as 2MHz

### Synchronization 

- Add a known pilot signal with freq of 10KHz of finite length.
- Concatenate it with modulated signal.
- Convert it into .wav file to transmit.
- Transmitter part is done..

Now , Play the .wav file near the microphone of the laptop while instantiating the __PyAudio__ code in the reciever.

- Pyaudio code returns a .wav file 
- Use CORRELATION to find the when the actual signal starts.
- Decode the .wav file using Scipy based obtained correlation value .

### Demodulation

Use minimum distance decoding to demodulate.

### Final image

After demodulation , calculate the final bit error rate and plot the final recieved image.

           plt.imshow(d,'gray')
	   plt.show()

