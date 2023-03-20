# PhoMeme Data Challenge Submissions

This repo holds the official PhoMeme data challenge leaderboards and describes the process for submitting runs.
All associated data for the challenges are held on [this page](https://phomemes.github.io/challenge/).

**NOTE** The instructions and formatting for this repository and leaderboard borrow heavily from the [MSMARCO-Document-Ranking-Submissions](https://github.com/microsoft/MSMARCO-Document-Ranking-Submissions) repository, which has an excellent set up for evaluations, "coopetition", and leaderboards for ML-based challenges.

## Submission Instructions

To make a submission, please follow these instructions:

1. Download the `*.partition.tar` challenge data from [Google Drive](https://drive.google.com/drive/folders/17Ehr0LZBBnXuHfW7gqJFqiRbDv2mr5gM?usp=sharing). 
   - Data for Challenge 1 and Challenge 2 are the same, where we have provided a sample of hashed accounts and images they have shared.
   - We provide two forms of this image data:
      - Dense embeddings of *all* images using the [EfficientNetB1](https://www.tensorflow.org/api_docs/python/tf/keras/applications/efficientnet/EfficientNetB1) model in `TestData.ActorEmbeddings`, or
      - A subsample of raw images for each hashed account, in `TestData.ActorImages`
   - Each dataset is partitioned by first character of the hashed account ID, so `0.partition.tar` contains data for all accounts whose hashed IDs start with `0`. Download all partition files to reconstruct the full dataset.



2. Based on which challenge you are submitting to, either create labels for each account in your selected dataset (Challenge 1), or create labels for the individual images in these datasets (Challenge 2). 
   - Challenge 1 submission details:
      - Each folder in the challenge data corresponds to a particular account ID.
      - For each account ID, generate two pairs of labels:
          - The first label, `inauthentic`, is for whether the account is authentic or not (`1 = inauthentic` or disinformation agent, `0 = authentic` or a legitimate account).
          - The second label, `campaign`, corresponds to the disinformation campaign with which this account is associated. If the `inauthentic` label is `0`, then this actor is legitimate, and its `campaign` label should be `"None"`. If the `inauthentic` label is `1`, then this `campaign` label should come from the following:
            - campaign.iranian
            - campaign.russian
            - campaign.venezuelan
      - Write this data out to a CSV file, called `run.csv`, that contains the following three fields:
         - `user_id` - Hashed user ID, corresponds to the folder's name
         - `inauthentic` - Binary for whether the account is a legitimate or authentic actor or not
         - `campaign` - Campaign ID
      - We provide a skeleton run file on GitHub [here](https://github.com/phomemes/phomemes.github.io/blob/main/leaderboards/eval/C1.run_skeleton.csv)
   - Challenge 2 submission details:
      - Each folder in the challenge data corresponds to a particular account ID, and each image in the account has a unique ID as well. E.g., account ID `0ebfaca2f71c9edf248dbd5950827358` has image `0ebfaca2f71c9edf248dbd5950827358-65d8174e3cebf675eba01ea198562688.jpg`.
      - For each image ID, generate two sets of labels:
          - The first set of labels contain `is_screenshot_label`, or whether the image contains a screenshot (`0 = no screenshot`, `1 = contains a screenshot`) and the associated confidence score `is_screenshot_score`, or`0.0-1.0`, generally describing something like the confidence that this image is a screenshot.
          - The second set of labels consist of scores for each image and its source platform: `discord_score,fb_score,fb-mobile_score,twitter_score,whatsapp_score`, where each field should be `0.0-1.0`, with higher values indicating more certainty that the image is from that platform.
      - Write this data out to a CSV file, called `run.csv`, that contains the following three eight:
         - `img_id` - Hashed user ID + img id, corresponds to the folder's name and the associated image
         - `is_screenshot_label` - Binary for whether the image is a screenshot
         - `is_screenshot_score` - Confidence that the image is a screenshot
         - `discord_score` - Confidence that the screenshot is from Discord
         - `fb_score` - Confidence that the screenshot is from Facebook
         - `fb-mobile_score` - Confidence that the screenshot is from FB Mobile
         - `twitter_score` - Confidence that the screenshot is from Twitter
         - `whatsapp_score` - Confidence that the screenshot is from WhatsApp

3. Decide on a submission id, which will be a permanent (public) unique key. The submission id should be of the form `yyyymmdd-foo`, where `foo` can be a suffix of your choice, e.g., your organization/group name.
Please keep the length reasonable.
See [here](https://github.com/phomemes/phomemes.github.io/tree/main/leaderboards/submissions/) for examples.
`yyyymmdd` should correspond to the submission date of your run.

4. In the directory `leaderboards/submissions/<CHALLENGE_ID>`, where `CHALLENGE_ID` is the challenge descriptor (one of `c1.disinfo`, `c2.screenshot`), create the following files:
   1. `leaderboards/submissions/<CHALLENGE_ID>/yyyymmdd-foo/run.csv` - run file containing your labels for this challenge
   2. `leaderboards/submissions/<CHALLENGE_ID>/yyyymmdd-foo/metadata.json`, in the following format:

       ```
         {
           "runtag": "<Run Name>",
           "date": "2022-05-28",
           "organization": "<ORGANIZATION>",
           "model_description": "<DESCRIPTION OF YOUR MODELING APPROACH>",
           "type": "automatic or manual",
           "paper": "http://<link-to-paper>",
           "code": "http://<link-to-Github-repo>"
         }
       ```
       Leave the value of `paper` and `code` empty (i.e., the empty string) if not available.
       These fields correspond to what is shown on the leaderboard.

5. Open a pull request against this repository.
The subject (title) of the pull request should be "Submission yyyymmdd-foo", where `yyyymmdd-foo` is the submission id you decided on.
This pull request should contain exactly three files:
   1. `leaderboards/submissions/<CHALLENGE_ID>/yyyymmdd-foo/run.csv` - the CSV run file with results
   2. `leaderboards/submissions/<CHALLENGE_ID>/yyyymmdd-foo/metadata.json` - the metadata file




### Frequency of Submission

We discourage modeling decisions based eval numbers to avoid overfitting to the set.
To ensure this, we request participants to submit:

1. No more than 2 runs in any given period of 7 days.
2. No more than 1 run with very small changes, such as different random seeds or different hyper-parameters (e.g., small changes in number of layers or number of training epochs).

Participants who may want to run ablation studies on their models are encouraged to do so using training data, not the testing data.

### Metadata Updates

The metadata you provide during run submission is meant to be permanent.
However, we do allow "reasonable" updates to the metadata as long as it abides by the spirit of the leaderboard (see above).
These reasons might include adding links to a paper or a code repository, fixing typos, clarifying the description of a run, etc.
However, we reserve the right to reject any changes.

It is generally expected that the team description in the metadata file will include the name of the organization (e.g., university or company).
In many cases, submissions explicitly list the contributors of the run.
It is _not_ permissible to submit a run under an alias (or a generic, nondescript team) to first determine "how you did", and then ask for a metadata change only after you've been shown to "do well".
We will reject metadata change requests in these circumstances.
Thus, you're advised to make the team description as specific as possible, so that you can claim "credit" for doing well.

Once you've created a new metadata JSON file (i.e., `leaderboards/submissions/<CHALLENGE_ID>/yyyymmdd-foo/metadata.json`), send us a pull request with it.
Please make the subject of the pull request something obvious like "Metadata change for yyyymmdd-foo".
Also, please make it clear to us that _you_ have "permission" to change the metadata, e.g., the person making the change request is the same person who performed the original submission. 

### Anonymous Submissions

We _do_ allow anonymous submissions.
Note that the purpose of an anonymous submission is to support blind reviewing for corresponding publications, not as a probing mechanism to see how well you do, and then only make your identity known if you do well.

Anonymous submissions should still contain accurate team and model information in the metadata JSON file, but on the leaderboard we will anonymize your entry.
By default, we allow an embargo period of anonymous submissions for up to nine months.
That is, after nine months, your identity will be revealed and the leaderboard will be updated accordingly.
Additional extensions to the embargo period based on exceptional circumstances can be discussed on a case-by-case basis; please get in touch with the organizers.

For an anonymous submission, the metadata JSON file should have an additional field:

```
"embargo_until": "yyyy/mm/dd"
```

Where the date in `yyyy/mm/dd` format cannot be more than nine months past the submission date.
For example, if the submission date is 2021/06/01, the longest possible embargo period is 2022/03/01.
Of course, you are free to specify a shorter embargo period if you wish.

Note that even with an anonymous submission, the submission id is publicly known, as well as the person performing the submission.
You might consider using a random string as the submission id, and you might consider creating a separate GitHub account for the sole purpose of submitting an anonymous run.
Neither is necessary; we only provide this information for your reference.


## Legal Notices

The documentation and other content in this repository is released under the [Creative Commons Attribution 4.0 International Public License](https://creativecommons.org/licenses/by/4.0/legalcode),
see the [LICENSE](LICENSE) file.
It grants you a license to any code in the repository under the [MIT License](https://opensource.org/licenses/MIT), see the
[LICENSE-CODE](LICENSE-CODE) file.

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found at http://go.microsoft.com/fwlink/?LinkID=254653.


