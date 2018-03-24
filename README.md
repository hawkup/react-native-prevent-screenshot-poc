# React Native Prevent Screenshot

### Prevent Capture Screen

* Android

  * Prevent capture screen by setFlag secure

  ```java
  getWindow().setFlags(WindowManager.LayoutParams.FLAG_SECURE, WindowManager.LayoutParams.FLAG_SECURE);
  ```

  * If you want to remove flag secure

  ```java
  getWindow().clearFlags(WindowManager.LayoutParams.FLAG_SECURE);
  ```

* iOS

### Hide Preview Screenshot

* Android

  * SetFlag secure already hide preview screenshot

  ```java
  getWindow().setFlags(WindowManager.LayoutParams.FLAG_SECURE, WindowManager.LayoutParams.FLAG_SECURE);
  ```

* iOS

  * Overlay screen by added 2 two into appDelegate.m

```code
- (void)applicationWillResignActive:(UIApplication *)application {

// fill screen with our own colour
UIView *colourView = [[UIView alloc]initWithFrame:self.window.frame];
colourView.backgroundColor = [UIColor whiteColor];
colourView.tag = 1234;
colourView.alpha = 0;
[self.window addSubview:colourView];
[self.window bringSubviewToFront:colourView];

// fade in the view
[UIView animateWithDuration:0.5 animations:^{
  colourView.alpha = 1;
}];
}

- (void)applicationDidBecomeActive:(UIApplication \*)application {
// grab a reference to our coloured view
UIView \*colourView = [self.window viewWithTag:1234];
// fade away colour view from main view
[UIView animateWithDuration:0.5 animations:^{
colourView.alpha = 0;
} completion:^(BOOL finished) {
// remove when finished fading
[colourView removeFromSuperview];
}];
}
```

#### Reference

* http://pinkstone.co.uk/how-to-control-the-preview-screenshot-in-the-ios-multitasking-switcher/
