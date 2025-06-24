# MULRED Dataset

MULRED is a multimodal Reddit dataset compiled from posts on r/india, containing both text and image data, along with the thematic flairs assigned to each post.
The dataset was originally used in the thesis _"Classification of Reddit Posts"_ by Maksymilian Piotrowski for the task of predicting flairs based on posts content. The dataset includes only multimodal posts which contain both a text body (`selftext`) and either an image, or a hyperlink that makes Reddit display an image.  

### Data sources

All the text data comes from the publicly available subreddit r/india and was downloaded using Reddit data dump available at [https://academictorrents.com](https://academictorrents.com/details/1614740ac8c94505e4ecb9d88be8bed7b6afddd4).  
The image data is downloaded directly from Reddit, including external images attached to hyperlinks (as Reddit hosts their downloadable "previews").

### File structure

Every post is represented by two files - one for text content and one for image content. The naming convention is the following:  
- `post_x.json` for text files (where _x_ is the post ID)  
- either `post_ximage.jpg`, `post_ximage.jpeg` or `post_ximage.png` for image files

### Flair distribution

The dataset is balanced across most flairs, with slight variations in the number of posts for certain categories. There is a total of 3300 posts.

| Nr  | Flair              | Number of posts |
|-----|--------------------|-----------------|
| 1   | AskIndia           | 500             |
| 2   | Politics           | 500             |
| 3   | Crime              | 500             |
| 4   | Rant/Vent          | 500             |
| 5   | Policy/Economy     | 500             |
| 6   | Law & Courts       | 405             |
| 7   | Scheduled          | 395             |

### Image content description

All images are scaled to 224x224 size, which may alter their original aspect ratio.

### Text content description

The text content json files contain the following fields:

| Field Name               | Description                                                     |
| ------------------------ | --------------------------------------------------------------- |
| `id`                     | Unique post identifier                                          |
| `title`                  | Title of the post                                               |
| `url`                    | URL linked in the post                                          |
| `selftext`               | Main text body of the post                                      |
| `flair`                  | Flair (label) assigned to the post by the user or moderator     |
| `score`                  | Reddit upvote score of the post                                 |
| `num_comments`           | Number of comments on the post                                  |
| `created_utc`            | Timestamp of post creation in UTC format (Unix epoch)           |
| `convurl`                | URL of the downloaded image                                     |
| `comments`               | List of text comments                                           |
| `cleaned_text`           | Preprocessed version of the post selftext and title             |
| `cleaned_title`          | Preprocessed version of the post title                          |
| `cleaned_selftext`       | Preprocessed version of the post selftext                       |
| `cleaned_comments`       | Preprocessed version of the concatenated comments               |
| `light_cleaned_title`    | Partially preprocessed version of the post title                |
| `light_cleaned_selftext` | Partially preprocessed version of the post body                 |
| `light_cleaned_comments` | Partially preprocessed version of concatenated comments         |

Fields marked as "preprocessed" have undergone text normalization (lowercasing, punctuation removal, stopword filtering, etc.). "Partially preprocessed" fields retain more of the original structure.