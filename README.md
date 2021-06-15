# 2 Tier Application
<img width="708" alt="Screenshot 2021-06-15 at 10 03 31" src="https://user-images.githubusercontent.com/25173053/122054098-468d5280-cddf-11eb-8dde-3b4aed9b3631.png">

Once EC2 instances have been setup for the app and the db, we need to puth the app folder in the app instance. We do this by entering the command :- 
 
'sudo scp -i ~/.ssh/devop_bootcamp.pem -r app/ ubuntu@ec2-54-78-10-214.eu-west-1.compute.amazonaws.com:/home/ubuntu/' I do this from within the .ssh folder on my local setup. 

ssh into the instance using 'ssh -i "Permisson_file" user@IP_address'

Make the Provision.sh in app 
 
Do the Reverse Proxy by going into /etc/nginx/sites-available and editing the 'default' file. 

repeat the previous step in the /etc/nginx/sites-enabled folder

now run restart Nginx with the command sudo systemctl restart nginx

then enable Nginx by entering sudo systemctl enable nginx

now exit the app instance with exit

redo the first step but with the db folder and the db instance.

enter the db instance

open the db folder with cd db

run the provision script with sh provision.sh

check if mongo is running with the command systemctl status mongod

now exit the db and enter the app instance

we need to make a environment variable we can do this by first running nano .bashrc

at the bottom of the file add the line export DB_HOST="mongodb://[DB_IP_ADDRESS]:27017" where [DB_IP_ADDRESS] replace with the db ip address

exit the text editor and input the command source .bashrc

now open the seeds folder with the command cd app/seeds

run the seed file with node seed.js

after it has run go to the app folder by running cd ..

then run the app with node app.js

the app should now be running in the browser



