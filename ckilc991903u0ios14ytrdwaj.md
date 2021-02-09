## Quote - README, See wonderful quotes/fun-facts on your GitHub Profile README

Yep, you read it right ! There is a GitHub Action that lets you put an awe-inspiring fact or a famous quote on your GitHub Profile README, so that every morning, when you begin your work, you laugh, feel inspired and be determined.

---

The result before diving into steps:

![Sample Output](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754600750/tvDGCLguE.png)


Without dragging it further, keeping it short and simple, here are the steps:

### 1. Update your Profile `README.md` file. 

Add following in you Profile `README.md`, wherever you want quotes/fun-facts to appear. Do not forget to commit the file 😉

```html
<!--STARTS_HERE_QUOTE_README-->
<!--ENDS_HERE_QUOTE_README-->
```

It should look something like this:

![Step 1 Image](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754671536/gjVQcYmY9.png)

Profile `README.md` should be present in `<username>/<username>` repository. Need to know more about profile repository/README, check out official [docs](https://docs.github.com/en/free-pro-team@latest/github/setting-up-and-managing-your-github-profile/managing-your-profile-readme).

### 2. Add workflow (yaml) file.

Now, click on `Actions` tab on top of your profile repository `<username>/<username>`.

![Step 2 Actions Tab](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754761331/BjkM814vx.png)


Then, set up a workflow yourself.

![Step 2 Setup Workflow](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754800999/pQPyBFYBH.png)


Remove all the pre-entered contents of the yaml file and add the following:

```yaml
name: Update Quote Readme

on:
  workflow_dispatch:
  schedule:
    # Runs at 2 UTC everyday
    - cron: "0 2 * * *"

jobs:
  update-readme:
    name: Update Quote README
    runs-on: ubuntu-latest
    steps:
      - uses: siddharth2016/quote-readme@main
        with:
          COMMIT_MESSAGE: <your-commit-message>       # default - Update with quote-readme
          OPTION: both            # default - both, can be one of (quote, funfact, both), if 'both' then will display either a quote or a fact
```

`COMMIT_MESSAGE` and `OPTION` variables are not needed, unless you want custom commit message and do not want to see either quotes or fun-facts on `README.md`

Name this yaml file as `update-quote-readme.yml` or whatever suits you best and commit the workflow yaml file.

### 3. Test your action and see the Magic 🧙‍♂️

Now, again go to `Actions` tab.

![Step 3 Actions Tab](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754874022/8QH0uImma.png)


Click `Update Quote Readme` under workflows.

![Step 3 Update Quote Readme](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754901918/fR4TJyl9b.png)


Then `Run workflow`->`Run workflow`, wait for it to complete.

![Step 3 Run Workflow](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754929095/xxocyyA2G.png)


And once the action is done then check your Profile README for a wonderful quote or a fun-fact !

![Step 3 Result](https://cdn.hashnode.com/res/hashnode/image/upload/v1607754951620/yi4mJoh8_.png)


Additionally you can link it back to the original repository to show your support for this action !

Change `README.md` like this

```html
<a href='https://github.com/marketplace/actions/quote-readme'>
<!--STARTS_HERE_QUOTE_README-->
<!--ENDS_HERE_QUOTE_README-->
</a>
```

---

Well, that was it, if you followed these steps you would be seeing an awe-inspiring quote or a fact on your Profile README.

Share your Profile README quotes/facts screenshot in the comments below 👇

If you faced any issues, please comment here or create an issue on [this](https://github.com/siddharth2016/quote-readme) repository.

If you liked this not-so-useful action, then give it a star ⭐

If you loved this not-so-useful action, then [let's connect](https://blog.codekaro.info/lets-connect) and contribute to make this a little bit useful !

Just starting your Open Source Journey ? Do not forget to check out [Hello Open Source](https://github.com/siddharth2016/hello-open-source) !

Want to make a simple and awesome game from scratch ? Check [PongPong](https://github.com/siddharth2016/PongPong)

Till next time !

Namaste 🙏