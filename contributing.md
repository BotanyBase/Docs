---
layout: default
title: Contributing
---

# Contributing

BotanyBase's database is made out of the community's contribution!

If you'd like to help out, this is the place to be!
There are currently 2 ways to contribute:

- [Automated, with approval](#Automated)
- [Pull Request, with approval](#PullRequest)

---

## Automated
<a id="Automated"></a>

This method is regarded as the easiest due to its no-code simplicity.

1. Go to this [link](https://botanybase.github.io/contribute/add)
2. Fill in the plant details correctly

{: .new }
> Do Note!
> 
> Note that for `climates` you can only choose 1 of the 5
> 

3. Press submit and wait
4. Done!

{: .Warning}
> Warning!
>
> The Automated system can get overloaded as it has a 50 monthly submission limit, to avoid issues like this from happening, simply use the Pull Request method!
> 

---

## Pull Request
<a id="PullRequest"></a>

May be seen as complicated to some, but we will go through step by step.

1. Head to our [repository](https://github.com/BotanyBase/botanybase.github.io)
2. Go and look for the folder `data`
3. Under that folder, there are multiple files, choose the climate file
   eg. if your plant is a Tropical plant, go to `tropical.json`
4. Now, here is where you will need some Javascript Object Notation Knownledge.
   There are 5 parameters, some are required, some are optional:
   - `name` required:
     This is the plant name, set it to your plant name
   - `image` required:
   - `climate` required, important notes:
     Must be in the same climate name as the file,
     eg. you are in `tropical.json`, set `climate` to `Tropical` (CAPS MATTER)
     The image of the plant, choose a good picture for it, **must be an external URL**
   - `description` required:
     A short description of the plant, keep it less than 50 words
   - `height` optional:
     Just additional info
   - `special_features` optional, depreciated:
     Ignore if not needed
5. Now if you already haven't, create a Fork (this should be done before step 4. by Github automatically)
6. Then create a Pull Request, and wait for our team to approve, do check on it in case we need you to make changes
7. You're all set! Thanks!
