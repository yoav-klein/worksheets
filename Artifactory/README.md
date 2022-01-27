
# Artifactory
---

_Required infrastructure_

- Windows machine
- Permissions to our `artifactory-lab` repo in Artifactory.
- The `TrainingArtifactory` Git repository.

_Required knowledge_
- Basic git skills
- Basic command-line skills (Powershell/cmd)


# Intro
---

## Learning materials
https://jfrog.com/knowledge-base/what-is-an-artifact-repository/

One of these:

https://www.youtube.com/watch?v=051LQzmYPkI
https://www.youtube.com/watch?v=Zbwom40sXgE

## Questions
1. What is an “Artifact Repository”?
2. Artifactory is part of a larger suite of products, what are they?
3. What is it used for? Why not store our artifacts on a file server?
4. What kind of packages can you manage in Artifactory?
5. What repository types are there in Artifactory? Explain about them.

## Keywords
- Repository
- Artifact
- Package management/package types
- Checksum storage
- Local/Virtual/Remote repository

## Getting to know the UI
[Application Module - JFrog Documentation](https://www.jfrog.com/confluence/display/JFROG/Application+Module)

[Browsing Artifacts - JFrog Documentation](https://www.jfrog.com/confluence/display/JFROG/Browsing+Artifacts)

1. Get yourself familiar with the User Interface of Artifactory.
2. Upload some file from your local machine to the artifactory-lab repository.
3. Download the file to your local machine.
4. Delete the file you just uploaded.
5. Now upload it again to a folder named “Test/Artifactory”
6. Now try uploading an entire directory. Is that possible?
7. Try uploading a bunch of files together.
8. Where can you find the checksums of a file you uploaded?

# Working with the CLI
---
[CLI for JFrog Artifactory](https://www.jfrog.com/confluence/display/CLI/CLI+for+JFrog+Artifactory#CLIforJFrogArtifactory-BuildingPythonPackages)

### Setting up infrastructure
1. Download the JFrog CLI. Keep in mind that there’s a difference between V1 and V2, we’ll be working with V2.
2. Generate an APIKEY for yourself using the UI.
3. Clone the “TrainingArtifactory” git repository to your machine. We’ll be working from there.

## Questions
1. How do you perform authentication when using the CLI?
2. What’s the synopsis of the upload command? What’s the difference between a Target path that ends with a / and one that doesn’t? Read the docs carefully.
3. What is the difference between an access token and APIKEY?

## Commands
- upload
- download
- copy
- move
- delete
- set-properties
- search


## Exercises
IMPORTANT NOTE: We use the `artifactory-lab` repository along this exercise. You're not the only one using it, so do everything in a folder with your name. So for example, in the exercise "Upload the file app to `artifactory-lab/stage/rc-1.1/`" - Upload it to `artifactory-lab/<your-name>/stage/rc-1.1`  

### Upload and delete
1. Upload the file `app.exe` to the root of the repository.
How do you authenticate to the server?

2. Don’t use the `--url`, `--user` and `--password` every time, configure these as a server with the ID `artifactory-lab`. (Hint: `jf config`)
3. Delete the `app.exe` file using the CLI.

4. Upload the file `app.exe` to the `stage/rc-1.1/` directory, this time add the properties `branch=main` and `config=release` to the file. Browse to the UI and make sure you got the properties right.

5. Upload all the `config` directory to the artifactory-lab repository to `stage/rc-1.1/` (keeping the `config/` directory).

6. Delete the `config` directory from the repo. Make sure the directory is deleted as well (!)
7.  upload it again, this time:
- don’t keep the directory structure.
- Put a type=config property on all the files.

8. Delete all the files you uploaded in the previous exercise, using the `type=config` property.

9. Upload all the files ending with `.dll` to the `artifactory-lab/stage/rc-1.1/Windows` directory.

10. Upload all the files with the `.zip` extension to the `stage/rc-1.1/zipFiles` folder.

11. I don’t like the hierarchy in the `zipFiles` folder. Delete this folder and make it so that all the zip files will be in the same hierarchy in the `zipFiles` folder. (i.e. package.zip and sound.zip in the same folder).

12. Upload all the files in the `config` directory to the `stage/rc-1.1/config` directory, except for the YAML files.

### Download
13. Create a new directory and cd into it. Now download the stage/rc-1.1/app.exe to the current directory. 

14. Was it downloaded to the “stage/rc-1.1” directory? How can you disable this?

15. Download all the config directory.

16. Again, we don’t want all the “stage/rc-1.1/” thing. How can you download ONLY the config directory while maintaining its structure (i.e. the extra-config directory)? (Hint: placeholders)

### Using FileSpecs
Delete all you’ve done so far.

17. Learn about file specs, and do all the above exercises using file specs instead of the command line commands.

18. Delete all the repository.
Create a file spec that will upload: `app`, all the `.so` files and all the `config` files to the `Linux` folder, and `app.exe`, all the `.dll` files and all the `config` files to the `Windows` folder.

### Set properties
19. Set on all `*.so` and `*.dll` files the property `type=lib`

### Copy
20. Copy both `app` and `app.exe` to `artifactory-lab/release/1.1/bin` folder

### Search
21. Search all the files in the `stage/rc-1.1/Windows` directory, and use Powershell’s ConvertFrom-Json to print the SHA1 of them.

# Build Integration
---

[Build Integration](https://www.jfrog.com/confluence/display/JFROG/Build+Integration)

## Keywords
- Build info
- Build name/ build number
- Module
- Dependencies vs Artifacts

## Questions
1. What is build integration in Artifactory? Read about it.
2. What is it good for?
3. What is the relation between build name, build number, modules, artifacts and dependencies?
5. What kind of information can you collect on a specific build?

## Commands
- build-add-git
- build-collect-env
- build-publish
- build-promote

## Exercises
First - delete all the repository from the previous exercises, and upload all the `lib/` directory.

1. Download all the `.so`  files so that they will be appended to the dependency list of Build name `MyApp` number 2 module `Linux`.

2. Upload the `app`  file to the `bin` folder so it will be appended to the artifacts list of that build and module.

3. Download all the `*.dll` files so they will be appended to the dependency list of same build name & number, module `Windows`.

4. Upload the `app.exe` file to the `bin` folder so it will be appended to the artifacts list of that module.

5. Collect the git information and environment variables to that build.

6. Collect the environment variables to that build

7. Publish the build to Artifactory and browse the UI to see the various information about the build.

## Recommended to further learn:

- AQL
- Artifactory REST API
