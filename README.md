# spring-gumball
## CI Workflow (Part 1)
### Creating the workflow failed because I did not add the sping-gumball project to the repository before creating the workflow
![image](https://user-images.githubusercontent.com/73510978/168510171-ec08424a-19d1-40fa-a45d-38e94e90b1cf.png)
### You can see here that I uploaded files. I uploaded the spring-gumball project all in one directory into the repo (my repo had two directories:.github/workflows and spring-gumball, the gradlew file was inside the spring-gumball directory). The workflow run after uploading the spring-gumball project into the repo failed. It was still unable to locate the "gradlew" file.
![image](https://user-images.githubusercontent.com/73510978/168510884-a2434183-e229-4ba5-a0ae-e5c3ce92e80e.png)
![image](https://user-images.githubusercontent.com/73510978/168510662-08252222-7ffd-4342-92d3-66bac6c68061.png)
### At this point I thought something was wrong with the workflow itself so I modified it several times. Workflow runs continued to fail.
![image](https://user-images.githubusercontent.com/73510978/168511173-348546df-e01e-4eb5-9f73-2cf862ae3aaf.png)
![image](https://user-images.githubusercontent.com/73510978/168511273-f1af074b-2654-4d7a-b00e-2918b5eb7339.png)

### Some of the modifications to the workflow that I did include:
- Changing "chmod +x gradlew" to "chmod +x ./gradlew"
- Changing "unbuntu-latest" to "windows-latest"
- Changing "chmod +x gradlew to "git update-index --chmod=+x gradlew"

***Resources:***
- https://github.com/actions/starter-workflows/issues/171
- https://stackoverflow.com/questions/17668265/gradlew-permission-denied

### I thought I was uploading my spring-gumball project to the wrong location so I deleted the spring-gumball directory and uploaded it into the .github/workflows directory. Workflow continued to fail so I deleted the spring-gumball directory from the .github/workflows directory
![image](https://user-images.githubusercontent.com/73510978/168511760-096671d9-e992-4808-a98e-0ccf55ad9582.png)

### I kept playing around with the gradle workflow but it kept failing I even created another simpler gradle workflow but it kept failing as well so I ended up deleting it. Eventually, I decided to watch an old demo video of the lab (which I probably should have done from the beginning) and realized that I should not have uploaded all of the spring-gumball files into one directory. Instead I uploaded them as pictured below:
![image](https://user-images.githubusercontent.com/73510978/168512229-05ded018-0817-4e68-8783-1d8a3655fea1.png)

### After doing this, my gradle workflow finally ran successfully
![image](https://user-images.githubusercontent.com/73510978/168512406-3605ed6d-5577-40f7-884d-c3087f8d66f9.png)


## CD Workflow (Part 2)

### Service account:
![image](https://user-images.githubusercontent.com/73510978/168515278-60ff5143-e558-45ee-9c0d-b55e20c06324.png)
### Service account key:
![image](https://user-images.githubusercontent.com/73510978/168515302-cd0e5ae6-87dd-4389-bd28-6ebfc6d05d69.png)
### Github action secrets set:
![image](https://user-images.githubusercontent.com/73510978/168515367-168a884a-bc42-4836-afd6-4d236be4298b.png)
### Google workflow:
![image](https://user-images.githubusercontent.com/73510978/168515150-570c2e6d-702d-4ce4-b515-b61162b3cc2f.png)
### After creating a release I ran into this error:
![image](https://user-images.githubusercontent.com/73510978/168515944-899b33e2-472f-491b-b12c-da4cc5720cb4.png)
### I updated GKE_SA_KEY, reran then I got this error:
![image](https://user-images.githubusercontent.com/73510978/168516325-c03e0ad9-bb8f-4cbf-bd86-7084ec42f8dc.png)
### while trying to figure out how to fix the problem I ended up deleting the key I generated for my service account and made a new one. I updated GKE_SA_KEY then reran the release and ran into the following problem:
![image](https://user-images.githubusercontent.com/73510978/168520773-bda9fb12-3683-4c87-aba2-d06cfa0ccc28.png)

### I deleted the service account then made a new one and gave it the "owner" role. Then I created a new release. It resolved my issue but then I ran into another issue:
![image](https://user-images.githubusercontent.com/73510978/168522390-897cdb78-e3b2-4609-803b-d855cdb8062b.png)

### I fixed my deployment.yaml file then reran the release but I got the same error again. So, I created another release and the workflow ran successfully:
![image](https://user-images.githubusercontent.com/73510978/168523558-42e1ced0-0e54-42ba-b5d9-ea2c1f8d9be2.png)

### Successfull deployment in GKE:
![image](https://user-images.githubusercontent.com/73510978/168523627-30a9073d-f44a-4669-b5ac-a10065fd99ed.png)
![image](https://user-images.githubusercontent.com/73510978/168523587-591f2e5b-aaeb-4729-b775-e095977d598d.png)



