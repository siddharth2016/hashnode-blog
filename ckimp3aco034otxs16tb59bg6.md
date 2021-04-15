## Update Image - README, See random image on your GitHub Profile README

Yep, you read it right ! There is a GitHub Action that lets you put a random image (from a collection of yours) on your GitHub Profile README. Here I am again, with another no-so-useful GitHub Action ! Not saw the previous Action ? Check it out [here](https://blog.codekaro.info/quote-readme-see-wonderful-quotesfun-facts-on-your-github-profile-readme).

---

The result before diving into steps:

![result.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837154448/zW_ezA7yy.png)

Here the image highlighted will keep on changing in every 24 hours (from a collection of my images), you can use a collection of your preferred images and see them changing on your GitHub Profile README, with a new profile image to start each day !

---

Without dragging it further, keeping it short and simple, here are the steps:

### 1. Update your Profile `README.md` file. 

Add following in you Profile `README.md`, wherever you want your images to appear. Do not forget to commit the file 😉

```html
<!--START_SECTION:update_image-->
<!--END_SECTION:update_image-->
```

It should look something like this:

![step_1_image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837190541/PBRrwxA_w.png)

Profile `README.md` should be present in `<username>/<username>` repository. Need to know more about profile repository/README, check out official [docs](https://docs.github.com/en/free-pro-team@latest/github/setting-up-and-managing-your-github-profile/managing-your-profile-readme).

### 2. Add your preferred images.

You need to have your own collection of images that you want to be displayed on your README.

Create a folder `.github/images` on your GitHub Profile Repository to store the images.

To create this folder, you can do a `git push` from your local repository (given images are in `.github/images` folder). Check [this](https://stackoverflow.com/questions/12258399/how-do-i-create-a-folder-in-a-github-repository) for more info on creating a folder on a GitHub Repository.

It should look something like this:

![step_2_github_images_folder.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837236867/DwTzKUS_Z.png)

### 3. Add workflow (yaml) file.

Now, click on `Actions` tab on top of your profile repository `<username>/<username>`.

![step_3_actions_tab.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837266163/-7CR4YmhU.png)

Then, set up a workflow yourself.

![step_3_setup_workflow.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837282956/Vx332oW45.png)

Remove all the pre-entered contents of the yaml file and add the following:

```yaml
name: Update Image Readme

on:
  workflow_dispatch:
  schedule:
    # Runs at 1 UTC everyday
    - cron: "0 1 * * *"

jobs:
  update-readme:
    name: Update Image README
    runs-on: ubuntu-latest
    steps:
      - uses: siddharth2016/update-readme-image@main
        with:
          IMG_ALT: <alt-message> #image alt to be displayed if image is not mapped correctly
```

There are more options available to customize your workflow, check out a more detailed explanation [here](https://github.com/marketplace/actions/update-image-readme).

Name this yaml file as `update-image-readme.yml` or whatever suits you best and commit the workflow yaml file.

### 4. Test your action and see the Magic 🧙‍♂️

Now, again go to `Actions` tab.

![step_3_actions_tab.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837387299/-kTlBqS8z.png)

Click `Update Image Readme` under workflows.

![step_4_update_image_readme.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837411142/FfTgKW6r-.png)

Then `Run workflow`->`Run workflow`, wait for it to complete.

![step_4_run_workflow.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837433373/S7lcvZUGF.png)

And once the action is done then check your Profile README and see a random image (from your collection) !

![step_4_result.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1607837455981/DqMIm8N9K.png)


Additionally you can link it back to the original repository to show your support for this action !

Change `README.md` like this

```html
<a href="https://github.com/marketplace/actions/update-image-readme">
<!--START_SECTION:update_image-->
<!--END_SECTION:update_image-->
</a>
```
---

Well, that was it, if you followed these steps you would be seeing an amazing image from your collection on your Profile README.

Share your Profile README Images screenshot in the comments below 👇

If you faced any issues, please comment here or create an issue on [this](https://github.com/siddharth2016/update-readme-image) repository.

If you liked this not-so-useful action, then give it a star ⭐

If you loved this not-so-useful action, then let's connect and contribute to make this a little bit useful !

- Just starting your Open Source Journey ? Do not forget to check out [Hello Open Source](https://github.com/siddharth2016/hello-open-source) !

- Need inspiration or a different perspective on the Python projects or just out there to explore? Check [Awesome Python Repos](https://github.com/siddharth2016/awesome-python-repos)

- Want to make a simple and awesome game from scratch ? Check [PongPong](https://github.com/siddharth2016/PongPong)

Till next time !

Namaste 🙏