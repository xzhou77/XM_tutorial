# Tutorial for Python virtual env, docker, and Git
## - install Git, install Docker, Install Pyhton, install VS code
### - create a directory XM_tutorial
mkdir XM_tutorial
cd XM_tutorial
code
### open XM_turorial folder and select 'new Terminal'
pwd
### Create a new virutal env under .venv for dependency collection 
python -m venv .venv  
### Allow VS code to run virtual env
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
### Enable virtual env
.venv\scripts\activate
### install package required by the projects within the virtual env
pip install "fastapi[all]"
### test run in VS code terminal 
uvicorn main:app --reload
### Interactive API at from typing import Union
http://127.0.0.1:8000/docs
### Save the dependency to the requirements.txt for Docker container later
python -m pip freeze > requirements.txt 
### Or use pipreqs
pipreqs /<your_project_root_path>/
## In VS code, add Docker file to worksapce
### Build the docker container <test_image>  
docker build -t xzhou77/xm_tutorial .
### Run docker container at local port <8888> mapping to the contianer port <5000> 
docker run -d --name zxm1 -p 8888:8000 xzhou77/xm_tutorial
### Test and stop
docker ps -a
docker stop zxm1
docker rm zxm1
## Git repro
git init
### create a main branch
git branch -M main
### Login to Github and create a new repro there with README.md and .gitignore
git remote add origin https://github.com/xzhou77/XM_tutorial.git
### Add files to repro
git add .
### Add .gitignore and README.md
### Commit all the changes
git commit -m "first commit"
### Push to github
git push -u origin main 
## Cleanup
Docker ps
Docker stop <container id>
Docker rm <container id>
# Deactivate virtual env
