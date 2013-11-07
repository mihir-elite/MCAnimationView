# MCAnimationView
[![Build Status](https://travis-ci.org/mirego/MCAnimationView.png?branch=master)](https://travis-ci.org/mirego/MCAnimationView)
[![Coverage Status](https://coveralls.io/repos/mirego/MCAnimationView/badge.png?branch=master)](https://coveralls.io/r/mirego/MCAnimationView?branch=master)
[![Badge w/ Version](https://cocoapod-badges.herokuapp.com/v/MCAnimationView/badge.png)](https://cocoadocs.org/docsets/MCAnimationView)
[![Badge w/ Platform](https://cocoapod-badges.herokuapp.com/p/MCAnimationView/badge.png)](https://cocoadocs.org/docsets/MCAnimationView)

UIImageView alternative for animations that doesn't need to load all the images in memory at once and provide a callback when animation is done.

## Example Usage

```objc
- (void)funWithAnimations
{
  /*
    Load 48 images in images array for animation.
    load0001.png
    load0002.png
    ...
    load0048.png
  */
  NSUInteger quantity = 48;
  NSMutableArray* images = [@[] mutableCopy];
  for (NSUInteger index=1; index<=quantity; index++) {
    NSString* imageName = [NSString stringWithFormat:@"load%04d.png", index];
    UIImage* image = [UIImage imageNamed:imageName];
    [images addObject:image];
  }

  /*
    Create the animation view and use it.
  */
  MCAnimationView* animationView = [[MCAnimationView alloc] initWithFrame:CGRectZero];
  [animationView setAnimation:images];
  [animationView setAnimationDuration:2.0f]; // 2 seconds,

  /*
    Start the animation
  */
  [animationView playAnimationRepeatCount:5 willPlayBlock:^(NSUInteger repetition) {
    // Animation will play
  } didPlayBlock:^(NSUInteger repetition) {
    // Animation done playing
  }];

  /*
    When you're done playing it.
  */
  [animationView stopAnimations];
}
```

## Adding to your project

If you're using [`CocoaPods`](http://cocoapods.org/), there's nothing simpler.
Add the following to your [`Podfile`](http://docs.cocoapods.org/podfile.html)
and run `pod install`

```ruby
pod 'MCAnimationView', :git => 'https://github.com/mirego/MCAnimationView.git'
```

Don't forget to `#import "MCAnimationView.h"` where it's needed.

## License

MCAnimationView is © 2013 [Mirego](http://www.mirego.com) and may be freely
distributed under the [New BSD license](http://opensource.org/licenses/BSD-3-Clause).
See the [`LICENSE.md`](https://github.com/mirego/MCAnimationView/blob/master/LICENSE.md) file.

## About Mirego

Mirego is a team of passionate people who believe that work is a place where you can innovate and have fun. We proudly build mobile applications for [iPhone](http://mirego.com/en/iphone-app-development/ "iPhone application development"), [iPad](http://mirego.com/en/ipad-app-development/ "iPad application development"), [Android](http://mirego.com/en/android-app-development/ "Android application development"), [Blackberry](http://mirego.com/en/blackberry-app-development/ "Blackberry application development"), [Windows Phone](http://mirego.com/en/windows-phone-app-development/ "Windows Phone application development") and [Windows 8](http://mirego.com/en/windows-8-app-development/ "Windows 8 application development") in beautiful Quebec City.

We also love [open-source software](http://open.mirego.com/) and we try to extract as much code as possible from our projects to give back to the community.
