**Option 1**:  SSH from a local datalab docker (**not working at this moment)
		
- Install [Docker](https://docs.docker.com/docker-for-windows/).
- Follow section "Install the "datalab" Docker container on your computer" of instructions [here](https://cloud.google.com/datalab/docs/quickstarts/quickstart-gcp) to SSH from a local datalab Docker.
			
**Option 2**:  SSH with PuTTY

*Set up the credentials* (once only)

- Download [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) and [WinSCP](https://winscp.net/eng/download.php#download2).
- Install WinSCP with default settings.
- Open WinSCP. At the lower-left corner click "Tools->Run PuTTYgen->Generate". Then move your mouse around to create randomness that's needed for key generation.
- Put an easy-to-remember username (e.g your Kerberos) to "Key comment"
- Click "Save private key" and save to `C:\User\[your_Windows_username]\.ssh\google_compute_engine.ppk`.
	
- Copy and paste the Public key generated in the top box to your Google Cloud instance ('[VM instances](https://console.cloud.google.com/compute/instances/)'->click your instance->Edit->SSH Keys -> Add item->Save).
 
*Establish a SSH connection* (every time)
	
- Open PuTTY and go to Connection->SSH->Auth->Browse. Navigate to `C:\User\[your_Windows_username]\.ssh\google_compute_engine.ppk`
- Go to Connection->SSH->Tunnels. Set source port as `localhost:8081` and destination port as `localhost:8080`. Click "Add".
- Go to Session. Type in USERNAME@IP-ADDRESS, where USERNAME is the easy-to-remember username you set for "Key comment" in previous steps, and IP-ADDRESS is the external IP of your instance which you can find in the [console](https://console.cloud.google.com/compute/instances/).
- Click "Open"
	
