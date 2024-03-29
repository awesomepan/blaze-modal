blaze-modal
=========================

**Note: You'll probably just be happier using the Bootstrap3 modal js.  This package almost is awesome, but has some critical layout issues that's currently preventing it from being useful.  I'd remove it from Atmosphere if there were controls.  But there are not.  So.**  

Modal dialogs using the new Meteor Blaze rendering engine.  

So, after trying probably five or six libraries for creating overlays, I said to heck with it, I'm just going to write a native overlay template for Meteor.  Dead simple, super easy to use, and works like charm. 

=========================
### Installation

First, install the reactive-overlays package from the command line, like so:

````
mrt add blaze-modal
````

Alternatively, if you'd like to bypass Atmosphere, and install directly from GitHub, you could update your application's smart.json file, like so:

````
{
  "meteor": {
    "branch": "master"
  },
  "packages": {
    "blaze-modal": {
      "git": "https://github.com/awatson1978/blaze-modal.git"
    }
  }
}
````

=========================
### Document Object Model

Second, add the reactiveOverlaysTemplate to your application, which adds the nececssary overlay templates.  In theory, you should be able to add the template just about anywhere in the application, but the recommend location is at the footer of your application container.  So, something like so:  

````
<template name="appContainerTemplate">
    <div class="app-content">
        ... my application code ...
    </div>
    {{> reactiveOverlaysTemplate }}
</template>
````

=========================
### Controllers

The beauty of using a native spark template for creating an overlay, instead of a third party library, is the only thing you need to do is set the following Session variable, and Bam! You got an overlay!
````js
    Session.set('show_reactive_overlay', true);
````

However, people usually want more than just an overlay mask.  They want to display images and templates **on top** of that overlay mask.  Fair enough.  We expose three simple functions to manage the overlay:


````js
showImageOverlay(elementId)
showTutorialOverlay(elementId)
hideOverlay()
````

So, for instance, if you want to use a thumbnail as a trigger, and display a nice big photograph, you would want to use something like the following:

````js
Template.samplePageTemplate.events({
    'click .thumbnail-image-a': function(){
        showImageOverlay('#fullsizeImageA');
    }
});
````

**Note:  the following is untested.**
The reactive overlays should also work with a block of HTML code for creating tutorial pages.  You should be able to do something like this:

````js
Template.samplePageTemplate.events({
    'click .tutorial-icon': function(){
        showImageOverlay('#currentPageTutorial');
    }
});
````

=========================
### License

MIT License. Use as you wish, including for commercial purposes.  
