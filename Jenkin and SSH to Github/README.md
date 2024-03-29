## Merging changes from jenkins to github

1. create a new job.
    - give it a description and enter the following details

![new job](<Screenshot 2024-01-10 113401.png>)

2. next scroll down to 'Git'.
    - Enter these details
   

![git](<Screenshot 2024-01-10 112125.png>)

   - press 'add' on credentials
   - enter these details and paste the private key
  
![Alt text](<Screenshot 2024-01-10 120406.png>)


1. next is build steps:
    - Scroll down -> 'Add Build Step' -> 'invoke top-level targets'

![build steps](<Screenshot 2024-01-10 105253.png>)

4. Choose Maven version,
    - goals = code to run (we are using maven but we do not need to add `mvn` to the command).
    - set the path in the repo to your pom.xml

![mvn](<Screenshot 2024-01-10 105740.png>)

5. 'Apply' and 'Save'
    - Now run the job
    - and check the console output 
  
![console output](<Screenshot 2024-01-10 115530.png>)


6. Add the Build trigger, this will be to trigger jenkins.
   - Choose this option to look for changes to github repo.
  
![Alt text](<Screenshot 2024-01-10 120644.png>)

7. Change the branch that jenkins should listen on.
   - Set this to the 'dev' branch

![Alt text](<Screenshot 2024-01-10 120810.png>)

8. Next we need to add the webhook to github.
   - Github repo settings -> webhooks -> 'Add Webhook'

![Alt text](<Screenshot 2024-01-10 121224.png>)



1.  Now Make a change to the file.
    - commit and push to github and check jenkins to see the jobs running

![Alt text](<Screenshot 2024-01-10 143254.png>)

## making job 2

 Create new job
 add git repo info.<br>
 this needs to http link.
![Alt text](<../Screenshots/Job 2/Screenshot 2024-01-12 164819.png>)

 Source Code Management
This needs to be ssh link
![Alt text](<../Screenshots/Job 2/Screenshot 2024-01-12 165450.png>)
 Add Behaviours
![Alt text](<../Screenshots/Job 2/Screenshot 2024-01-12 165605.png>)
 post build actions -> Git Publisher 
   - enter these details
![Alt text](<../Screenshots/Job 2/Screenshot 2024-01-12 165411.png>)
 
 now attach job 2 to job 1
   - go to job 1 -> configure -> post build actions and choose 2
![Alt text](<../Screenshots/Job 2/Screenshot 2024-01-10 151057.png>)

## making job 3

1. Create a freestyle new job
2. add the following build trigger to look for job 2:
![Build Trigger](<../Screenshots/Screenshot 2024-01-15 160009.png>)
3. add pem file for SSH Agent:
![Alt text](<../Screenshots/Screenshot 2024-01-15 160247.png>)
4. under build steps, add ssh agent and add the following commands:
```
ssh -o StrictHostKeyChecking=no ubuntu@ec2-18-201-19-112.eu-west-1.compute.amazonaws.com "sudo chmod 777 -R /repo"
scp -o StrictHostKeyChecking=no -r ../craig-jsonvh-job1-CI-test/springapi ubuntu@ec2-18-201-19-112.eu-west-1.compute.amazonaws.com:/repo
ssh -o StrictHostKeyChecking=no -i ubuntu ubuntu@ec2-18-201-19-112.eu-west-1.compute.amazonaws.com "cd /repo/springapi; sudo mvn clean package spring-boot:start"
```


## blockers

job 2 failed because i forgot to add the github project

![Alt text](<../Screenshots/Job 2/Screenshot 2024-01-10 153208.png>)