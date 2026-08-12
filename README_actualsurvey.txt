REAL VIDEO SURVEY — 31 TRIAL DESIGN

GITHUB FILES
------------
Upload ONLY the contents of the folder "github_upload":

  index.html
  video_links.csv

Fill video_links.csv with one YouTube URL for every VideoID 1-50.

Format:
  video_id,youtube_url
  1,https://youtu.be/XXXXXXXXXXX
  2,https://youtu.be/YYYYYYYYYYY
  ...
  50,https://youtu.be/ZZZZZZZZZZZ

The survey also accepts normal YouTube watch URLs and bare YouTube IDs.

SURVEY DESIGN
-------------
Each participant receives:

  10 same-participant / different-detection pairs
  15 similar-situation pairs
   5 random subjective-only stress pairs
     - different participants
     - not in the same similar-situation group
   1 identical-video attention check

Total shown: 31 trials.
Main analysis: 30 trials.

The attention check is inserted after a random 10-20 analysis trials,
so it appears as displayed Trial 11-21.

The attention-check pair is removed automatically from the main pairwise
analysis by the decoder. It is written to decoded_quality_control.csv.

SOURCE CODES
------------
1 = same_participant_different_detection
2 = similar_situation
3 = random_subjective_stress
9 = attention_check

PARTIAL RESULTS
---------------
The participant can use "Save partial result" during the survey.
If the same participant later submits a more complete result, the decoder
automatically keeps the submission with the largest number of completed trials.

RESEARCHER-ONLY FILES
---------------------
Keep these OUTSIDE GitHub:

  researcher_only/decode_forms_result_codes_real31.py
  researcher_only/video_survey_private_key.pem

The private RSA key must never be uploaded to GitHub.

DECODING
--------
Install once:

  python -m pip install cryptography

Then run, for example:

  python decode_forms_result_codes_real31.py --input "VideoSurvey_FormsResponses.csv" --private_key "video_survey_private_key.pem" --video_mode real --output_dir "decoded_output"

Outputs:

  decoded_participant_demographics.csv
  decoded_pairwise_responses.csv
  decoded_quality_control.csv

The pairwise CSV excludes the attention-check trial.
