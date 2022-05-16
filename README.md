# spring-gumball
## CI Workflow (Part 1)
Creating the workflow failed because I did not add the sping-gumball project to the repository before running the workflow
![image](https://user-images.githubusercontent.com/73510978/168510171-ec08424a-19d1-40fa-a45d-38e94e90b1cf.png)
You can see here that I uploaded files. I uploaded the spring-gumball project all in one directory into the repo (my repo had two directories: workflow and spring-gumball the gradlew file was inside the spring-gumball directory). The workflow run after uploading the spring-gumball project into the repo failed. It was still unable to locate the "gradlew" file.
![image](https://user-images.githubusercontent.com/73510978/168510884-a2434183-e229-4ba5-a0ae-e5c3ce92e80e.png)
![image](https://user-images.githubusercontent.com/73510978/168510662-08252222-7ffd-4342-92d3-66bac6c68061.png)
At this point I thought something was wrong with the workflow itself so I modified it several times. Workflow runs continued to fail.
![image](https://user-images.githubusercontent.com/73510978/168511173-348546df-e01e-4eb5-9f73-2cf862ae3aaf.png)
![image](https://user-images.githubusercontent.com/73510978/168511273-f1af074b-2654-4d7a-b00e-2918b5eb7339.png)

Some of the modifications to the workflow that I did include:
- Changing "chmod +x gradlew" to "chmod +x ./gradlew"
- Changing "unbuntu-latest" to "windows-latest"
- Changing "chmod +x gradlew to "git update-index --chmod=+x gradlew"

I then deleted the spring-gumball directory and moved it into the workflow directory. Workflow continued to fail so I deleted the spring-gumball directory from the workflow directory
![image](https://user-images.githubusercontent.com/73510978/168511760-096671d9-e992-4808-a98e-0ccf55ad9582.png)

I kept playing around with the gradle workflow but it kept failing I even created another simpler gradle workflow but it kept failing as well so I ended up deleting it. Eventually, I decided to watch an old demo video of the lab (which I probably should have done from the beginning) and realized that I should not have uploaded all of the spring-gumball files into one directory. Instead I uploaded them as pictured below:
![image](https://user-images.githubusercontent.com/73510978/168512229-05ded018-0817-4e68-8783-1d8a3655fea1.png)

After doing this, my gradle workflow finally ran successfully
![image](https://user-images.githubusercontent.com/73510978/168512406-3605ed6d-5577-40f7-884d-c3087f8d66f9.png)





