# ml

I am completely new to Machine Learning. I have been a software engineer for seven years using technologies like [Clojure](https://clojure.org/), [C#/.NET](https://www.microsoft.com/net), [Java](https://www.java.com), and [NodeJS](https://nodejs.org). In my various jobs as a full stack developer, I've had several unique and challenging problems to solve—but none so intriguing as the problems Machine Learning is solving now.

This is a space for me to share various machine learning projects I work on. I intend to work, primarily, on small example projects that will be contained in this repo though if I feel a project deserves its own repo I'll put a link in this README.

## Setup

I use a Google Cloud VM for the code I test. I borrowed the majority of the setup from [fast.ai](http://course.fast.ai/).

- Create VM instance with GPU (you may need to request access to use a GPU).
  - Note that GPUs are only available in a [few select regions](https://cloud.google.com/compute/docs/gpus/).
  - I use an Ubuntu instance with a 30GB drive.˚
- Install (while installation is taking place you can work on the Networking section)
  - ssh into the instance `gcloud compute --project [name] ssh --zone [zone] [vm name]`
  - `wget http://files.fast.ai/files/install-gpu.sh`
  - `bash install-gpu.sh`
    - follow prompts
  - verify the GPU is running `nvidia-smi`
    - (for some reason the script doesn't always install cuda follow directions here: https://cloud.google.com/compute/docs/gpus/add-gpus#install-driver-manual also seen below)
       - curl -O http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
       - sudo dpkg -i cuda-repo-ubuntu1604_8.0.61-1_amd64.deb
       - sudo apt-get update
       - sudo apt-get install cuda
   - reset VM
- Networking
  - On the VM page, click the VM's name.
  - Under Network, click "default"
  - Click "Add firewall rule"
    - network: default
        - priority: 1000
        - direction: ingress
        - action on match: allow
        - source filters: public IP of your computer's network (you may have to keep an eye on your external IP and change this from time to time)
        - protocols and ports: allow all
- Start Notebook
  - Note this does not contain the data that fast.ai uses, but you can get that from [files.fast.ai](http://files.fast.ai).
  - After all previous steps are complete.
    - `jupyter notebook --ip=0.0.0.0`
    - navigate to the address indicated in the console substituting 0.0.0.0 with the IP of your VM.