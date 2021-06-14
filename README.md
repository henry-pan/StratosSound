# SonusStratos

[Live on Heroku!](https://sonusstratos.herokuapp.com/#/)

SonusStratos is a audio sharing application that allows users to post audio tracks and listen to audio tracks posted by other users. Users may also post comments on audio tracks.

# Built With

* Ruby on Rails
* PostgreSQL
* React
* Redux
* SCSS
* Amazon Web Services (AWS) S3
* Heroku

# Features

## Discover

Users can view and listen to featured tracks uploaded to SonusStratos on the Discover page. There are multiple carousels that users can scroll through to browse tracks.

![Carousel](https://github.com/henry-pan/SonusStratos/blob/main/docs/carousel.gif)

The carousel was implemented using a CSS rule `scroll-behavior: smooth` on the container element, and a `handleScroll` function called by some buttons. The function  manipulates the container element's `scrollLeft` property, accessed by a hook.

```javascript
// frontend/components/carousel/carousel.jsx

handleScroll(dir) {
  let inc = this.state.increment;
  let pos = this.state.scrollPosition;

  // Reduce increment if pos at a container edge
  if (pos === 0 || pos === this.state.scrollMax) inc -= 34;

  if (dir === "left") inc *= -1;
  pos += inc;

  this.scrollElement.current.scrollLeft = pos;
  this.setState({ scrollPosition: Math.max(0, Math.min(pos, this.state.scrollMax)) });
}
```

Each track can be played by clicking the play button, which opens the playbar and plays the track. By clicking on the title or album art of a track, users can navigate to the track's page to view other details like the description or user comments.

## Uploading / Track Pages

Logged in users can upload new tracks to SonusStratos. Each track can optionally be given an album art. Once uploaded, users can edit the title, description, and album art by accessing the track's page.

## Continuous Play

Once a track is played, it appears on the playbar on the bottom of the screen. The track will continue to play even as users navigate around the site. In addition, users can restart the track, toggle looping, and adjust the volume. Users can click on the seek bar to jump around the current track. Clicking the duration on the right of the seek bar will toggle between track duration and duration remaining.

## Comments

Logged in users can leave comments on tracks by navigating to a track's page and entering a comment in the comment box. Users can delete their own comments, and the uploader of the track can delete any comment on their track. When the uploader leaves a comment on their own track, their comment is highlighted in gray.

## User Pages

Users can edit their username, full name, city, country, bio, and profile picture on their user page. This page also displays the tracks the user has uploaded.

# Planned Features

* Likes - Allow for users to "like" a track, which makes it appear on their user page sidebar.
* Dark Mode - A toggle to change the color scheme of the site.
