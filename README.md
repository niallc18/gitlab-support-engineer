# GitLab Associate Support Engineer

## Task 1 (Script)

The aim of this task was to produce a script that prints the usernames of all users on a Linux system together with their home directories. I used bash to create this script, and any documentation I used is referenced at the end of this file.

```shell

#!/bin/bash

getent passwd | while IFS=: read user a b c d homedir e; do
  echo "$user:$homedir"
done

```

- ```getent passwd``` command retrieves user information from the system's user database. You could also parse ```/etc/passwd``` but sometimes not all users will be located there.
- ```| while IFS=: read user a b c d homedir e;``` the pipe operator ```|``` is used to pass the output from the ```getent passwd``` into the input of the following ```IFS=: read user a b c d homedir e```. Each line of the input is read from the ```getent passwd``` and split into fields and assigned to variables ```user, a, b, c, d, homedir, e```.
- ```echo "$user:$homedir"``` prints the concatenated values of the ```user``` and ```homedir``` variables seperated by a ```:```.

## Task 2 (Git)

- Step 1: ```git add <file>``` then ```git commit -m "first commit"```
- Step 2: ```git add <file>``` then ```git commit -m "second commit"```
- Step 3: ```git checkout -b feature-branch```
- Step 4: ```git add <file>``` then ```git commit -m "awesome feature"```
- Step 5: ```git checkout master```
- Step 6: ```git add <file>``` then ```git commit -m "third commit"```
- Step 7: ```git merge feture-branch -m "merge"```
- Step 8: ```git add <file>``` then ```git commit -m "fourth commit"```

## Task 3 (Blog)

What is Git? Arguably the most common question when sitting in a lecture hall with first-year computer science students. Git (Global Information Tracker) is a distributed version control system that allows developers from all over the world to collaborate on projects. You may be wondering: how does Git allow developers to collaborate, and why is it so useful? 

Git makes use of version control, which ensures developers can track changes made to their code. It records every change over time, and is beneficial for many reasons, most notably it enables developers to revert changes back to a previous version. This is incredibly useful, and you can imagine how important this becomes within larger codebases that can sometimes produce code that is not compatible. Reverting is something developers would prefer not to do, but sometimes it can be handy and save the day!

Code review is a great feature of Git, as it enables developers to verify that code fits the requirements set out and provides a great learning opportunity for many developers. Git can integrate with various review tools and platforms, making it easy for developers to continuously improve their code and practices.

Branches are another great feature of Git; this plays into the point of collaboration. When using Git, developers can create a branch to work on separately from the master branch. This enables developers to work on separate features without affecting the codebase; this is efficient and applies to many development teams. Once a feature is completed, it can then be sent off for code review, and if granted, the feature branch can then be merged with the master branch. This now means the codebase is updated with the new feature, but without having to deal with unnecessary downtime or conflicts. 

Git is used by many and can quite simply make your development journey much simpler and pain-free!

## Task 4 (Bug)

I was recently working on a side project where I was building a patient registry system using Ruby and Rails. Everything was fairly simple, as the aim of this project was to improve my front-end skills by learning Tailwind. However, I ran into a slight problem with the logic of the application. I wanted to make it so there was just one login portal for users, and I set up roles as an attribute of a user. For example, a user by default was assigned 0 as their role, meaning they were a receptionist. I then had a separate admin panel, allowing for an admin to change the role integer to 1, meaning now they're a doctor. The issue lay within permissions, as by having one login portal, I needed to make it so views could only be rendered depending on the user's permissions. Therefore, I had to research how I could implement permissions, as again, the aim of this project was to keep it simple and learn tailwind. Fortunately, I came across a ruby gem called Pundit, which allowed me to create policies and give each role permission. For example, I could now ensure each action had to be authorised by a certain role. For example, a receptionist can create patient records, but only a doctor can delete them. Once I set up the policies, I was then able to make sure certain views would only render depending on the user's assigned role. This was a success, and I was able to focus on the front-end shortly after, and now I have a fully functioning, simple patient registry system.

## References

- https://www.geeksforgeeks.org/getent-command-in-linux-with-examples/
- https://medium.com/@linuxschooltech/what-is-the-getent-passwd-command-in-linux-90abb27ab723
- https://stackoverflow.com/questions/26479562/what-does-ifs-do-in-this-bash-loop-cat-file-while-ifs-read-r-line-do
