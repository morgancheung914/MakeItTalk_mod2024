# Virtual Machine
- This repo was ran and tested on the GCP machine morgan/make_it_talk. Many dependencies that were not in bar machines were installed here. 
- If you are running on the GCP VM, you can use the conda environment foa directly

# Environment
python 2.7 on Linux Ubuntu: 
conda create --name foa python=2.7 tensorflow=1.15
pip install -r requirements_2.txt
conda install opencv==4.1.0 -c conda-forge

# Download Pretrained Models 



Download the following pre-trained models to `examples/ckpt` folder for testing your own animation.

| Model |  Link to the model | 
| :-------------: | :---------------: |
| Voice Conversion  | [Link](https://drive.google.com/file/d/1ZiwPp_h62LtjU0DwpelLUoodKPR85K7x/view?usp=sharing)  |
| Speech Content Module  | [Link](https://drive.google.com/file/d/1r3bfEvTVl6pCNw5xwUhEglwDHjWtAqQp/view?usp=sharing)  |
| Speaker-aware Module  | [Link](https://drive.google.com/file/d/1rV0jkyDqPW-aDJcj7xSO6Zt1zSXqn1mu/view?usp=sharing)  |
| Image2Image Translation Module  | [Link](https://drive.google.com/file/d/1i2LJXKp-yWKIEEgJ7C6cE3_2NirfY_0a/view?usp=sharing)  |
| Non-photorealistic Warping (.exe)  | [Link](https://drive.google.com/file/d/1rlj0PAUMdX8TLuywsn6ds_G6L63nAu0P/view?usp=sharing)  |

# Puppet format
- a .png file of the head without background and a background image of the puppet has to be put in examples_cartoon
- see bear7.png under examples_cartoon for an example 
- Refer to MakeIttalk's repository if needed 

# Run FOA script to configure puppet landmarks
`python main_gen_new_puppet.py bear7.png`

Once said could not connect to any X display:

## Setup
- Configure:
	- on Linux machine, run `vim /etc/ssh/sshd_config`, enable X11Forwarding by uncomment the line for X11Forwarding

	- on local machine, Enable x11 forwarding in your ssh config
        - Sample config:
        ```
        Host 34.150.94.164
        HostName 34.150.94.164
        ForwardX11 yes
        ForwardX11Trusted yes
        IdentityFile C:\Users\Intern\Documents\test-code\intern@laptop-3m6cfhf7
        User intern
        ```
    

- Download Xming and Putty
- start XLaunch
	- run `$echo $DISPLAY` on your local machine, write the port number to the display argument in XLaunch

	
- Test if X11 forwarding is correctly set:
	xclock or xeyes

- The Xming window showing the landmarks of the puppet will show up. Autodetected landmarks are poor, may need manually adjust
- After adjustment, press Q twice, after Delauney Triangulation is finished, press Q once more.
- The landmark information is saved under examples_cartoon



