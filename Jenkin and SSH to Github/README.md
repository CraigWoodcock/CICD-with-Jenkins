## Merging changes from jenkins to github

1. create a new job.
    - give it a description and enter the following details

![new job](<Screenshot 2024-01-10 113401.png>)

2. next scroll down to 'Git'.
    - Enter these details

![git](<Screenshot 2024-01-10 112125.png>)

3. next is build steps:
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