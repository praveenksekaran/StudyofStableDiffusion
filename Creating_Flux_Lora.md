# Basics
- there are no template avaliable for Flux on Jarvis Labs like Khoya SS. Hence template has to be setup

#### Prerequisite
1. JarvisLabs Account
2. HuggingFace Account

# Step 1: Setup JarvisLabs
1. Choose PyTourch Template (JarvisLabs --> Dashboard --> Templates --> PyTourch) 
2. Select A6000 instance with storage above 120 GB
3. Open Visual Studio code
   - Choose a Theme and "Mark as done"
   - Click Folder Explorer frpom left Nav. Click Open Folder and choose "/home/" 
5. Access the Terminal (CTRL + ~ ) or button in VS called Toggle botton view 

# Step 2: Install AI Toolkit
AI Tool kit is 3rd party appplication used to train Flux LoRA.

#### Step 2.1 Clone the repository
Run the below code in VS Terminal
```bash
# Clone the AI Toolkit repository from GitHub
git clone https://github.com/ostris/ai-toolkit.git

# Change directory to the cloned repository
cd ai-toolkit

# Initialize and update Git submodules recursively (if any)
git submodule update --init --recursive
```

#### Step 2.2 Set Up Python Env
Create  virtual Env. Can use Condo but git is easier
Activate virtual Env.

```bash
# Create a virtual environment named 'venv'
python3 -m venv venv

# Activate the virtual environment
source venv/bin/activate
```
Note: if Virtual Env is active. then the command prompt will have (venv) suffixed 
E.g. (venv) root@instance:~/home#

#### Step 2.3 Install Dependencies 

```bash
# Install PyTorch (specific version might be needed based on hardware. hence use A6000)
# Note: Will take 5 -10 mins for the first time
pip3 install torch

# Install other dependencies from requirements.txt
pip3 install -r requirements.txt
```

#### Step 2.4 Create Env file 
- Go to Left Nav --> select ai-toolkit folder --> Create file icon --> name it ".env" 
![image](https://github.com/user-attachments/assets/b9b345e4-dce3-42fa-ab89-7c617b7170d0)

or 

```bash
# Create a .env file if it doesn't exist
touch .env
```
# Step 3: Configure Hugging Face 

#### Get token from Hugging Face 
- Follow material from Flux_Basics.md

#### Update .env with Token 
```bash
# Add the following lines manually 
HF_TOKEN=YOUR_HUGGINGFACE_TOKEN

or

# Add using command
echo "HF_TOKEN=<YOUR_HUGGINGFACE_TOKEN>" >> .env
```
#### Login to HF 
```bash
# Log in to Hugging Face CLI (this may prompt for credentials)
huggingface-cli login

# Paste token when prompted and Enter
# Add token as git credential? (Y/n). Dont respond, just Enter 
```
# Step 4
# Step 5: Launch Flux Train UI
```bash
# Run the training UI script
python flux_train_ui.py
```
# Step 6: Access the Gradio Interface 
- In the terminal, Click on the Gradio link (displayed as "**Running on the public URL:___________**") to open the user interface
- you are now ready to start training your Flux LoRA model!

# Step 7: Train your Flux LoRA
#### Data Preparation 
- in the UI, give a name like "acqua_flux_zwx" or "dhruv_flux_zwx" follows [Name]_[model]_[instance token]
- for trigger words " Photo of zwx perfume, 'Acqua di Gio' perfume" or "Photo of zwx boy" follows [subject instance token],<[product name]> 
![image](https://github.com/user-attachments/assets/69ae3430-74a7-4683-8e1c-d1bca20e8daf)

- Upload images (Size or extending is not concern)
- once completed, in the pop-up click "Add AI captions with Florence-2"
- watch all the activities in Terminal
![image](https://github.com/user-attachments/assets/752c719d-5a69-4c38-bcec-faac557dcb15)

#### Configure Training 
- Increase the "steps" to 2000-3000 (Default 1000). idea is to over train and then choose the right model
- "Learning Rate" (default 0.0004) value can be set between 0.0001 - 0.0005
     - lesser the value more features are trained on i.e. towards 0.0001
     - larger the value less features are trained i.e. towards 0.0005
     - for perfume bottle with Text, its product and we need more features hence for products 0.00025
     - for faces 0.0004
     - for Styles 0.00015
  - "Rank": Size of the matrix. Higher the rank, more featues and vice versa. Also higer the rank, higer the training time.
      - Faces: 16
      - Styles: 64
      - Products: 32
   - "Model to train" : dev
   - "Low VRAM" : False. as we are using A6000. if we are using A5000 then True
  ![image](https://github.com/user-attachments/assets/0ca18e0b-caf5-4057-9fcf-631669740402)

#### Advance options 
- "Sample_every" : after how many steps you need to take sample
- "Save_every" : after how many steps you need to save the model
- "max_steps_saves_to_keep" : models are overwritten after certain steps. keep this value higher than steps/save_every
![image](https://github.com/user-attachments/assets/93235e1c-2473-4aa8-bdb3-3193682b02ed)

#### Add Sample Prompts 
![image](https://github.com/user-attachments/assets/5abac3cb-ecf2-4f06-8b65-a69b7c927328)

#### Start Training 
- click on start training
- Check progress in VS Code Terminal

# Step 7: Use the model 

#### Download the model 
- the model is avaliable under ai-toolkit folder structure
![image](https://github.com/user-attachments/assets/7473f651-13ab-46f0-ad28-af78df729e0f)

#### Upload to ComfyUI 
- Go to comfyUI juyperlabs
- go to ~/ComfyUI/models/loras
- Drag and drop the downloaded model or use upload icon 
![image](https://github.com/user-attachments/assets/03f2c913-d90a-40f9-ab7d-702b9bd942f5)

#### use in WF 

![image](https://github.com/user-attachments/assets/3c9079e7-f439-45e9-9350-7ce9cc4f219b)














