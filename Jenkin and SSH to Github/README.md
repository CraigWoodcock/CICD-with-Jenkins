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