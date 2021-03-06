# Reviews, The Next Generation

We are returning to your reviews application. *Surprise!*

![Surprise](./photofunky.gif)

You can create a new repository or use the same one. If you'd like to use the same one, but would like to keep track of the previous version of your project, you can create a branch or use an annotated tag.

[Here](./rubric.md) lies the rubric.

## Review Tags

If you didn't include tags before, add them. These should have a many-to-many relationship with reviews.

Clicking on a tag should take the user to a page which displays the reviews associated with that tag.

Using appropriate HTML elements and AJAX, allow the user to add and remove tags from reviews. Be careful not to create a new tag if a tag with that name already exists.

## Review Comments

Add comments to reviews. Comments should be listed on a review's page after the review's content.

Create a form on a review's page that adds a comment to a review. Perform an old school form submission rather than using AJAX. After submitting a comment, the user should be returned to the review page, now including the comment that was just submitted.

### Things to ponder

What is the relationship between a review and its comments from the relational database perspective? Does a review or its comment own the relationship?

How can we best semantically represent review comments from an HTML perspective?

## Stretch tasks

- Create snazzy confirmation prompts for removing tags
- Use ES6 syntax
- Oh, you've already thought of a few things. Do those, but keep them simple.