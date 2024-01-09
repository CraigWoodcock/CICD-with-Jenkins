# CICD Pipelines

## What is a Pipeline?

 It's a series of automated steps or actions that software code goes through, such as building, testing, and deploying. Each step in the pipeline ensures that the code is functioning correctly and is ready for use, just like each stage in a non-technical pipeline ensures the product is ready for its next phase.

## How to create a job on jenkins

1. Log in, Go to 'Dashboard' and choose '+ New Item'.
2. Enter a name, Choose 'Freestyle' and then 'OK'.
3. Give it a Description, 'Discard Old Builds' -> enter max builds to keep.

![Configure](<../Screenshots/Jenkins/Screenshot 2024-01-09 155742.png>)


4. Scroll to the bottom, 'Add Build Step' and choose 'Execute Shell'.

![Build Step](<../Screenshots/Jenkins/Screenshot 2024-01-09 155814.png>)

5. Add commands and press 'Apply' and 'Save'.
  
![Add Code](<../Screenshots/Jenkins/Screenshot 2024-01-09 160042.png>)


## how to create a Pipeline
1. Create a second job following the steps above. Run the job to test it works

2. Configure the first job.

Scroll to the bottom, 'Post Build Action' -> 'Build Other Projects'.

![Alt text](<../Screenshots/Jenkins/Screenshot 2024-01-09 161720.png>)

3. Select your job from the list, 'Apply' and 'Save'




generate new ssh key,
- store .pub on github
  - inside repo settings -> deploy keys -> add deploy key.
  - paste public key and add.