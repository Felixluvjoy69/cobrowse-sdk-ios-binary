# CobrowseIO SDK - Remote Screenshare Service

With [Cobrowse.io](https://cobrowse.io)'s screen sharing technology for mobile apps you can see *exactly* what your customer sees on their mobile device, and provide realtime annotations to help solve customer support queries quickly.

## Try it out

You can try the Cobrowse.io service for **free** and **without signing up for an account**. Just follow the installation instructions below, then head to <https://cobrowse.io/trial> to use the trial dashboard.

These instructions will install a binary distribution of the Cobrowse.io SDK. Customers with a paid subscription can request source code access by [emailing us](mailto:hello@cobrowse.io).

## Installation

We recommend installing the CobrowseIO SDK using Cocoapods, add this to your Podfile:

```
pod 'CobrowseIO'
```

*Don't forget to run `pod install` after you've edited your Podfile.*

**Don't like Cocoapods?**

You can use the SDK by copying the framework from this repository directly to your project, and adding it to the binaries to be linked into your app in the "Build Phases" build step.

## Basic Setup

The CobrowseIO SDK can be used in your Objective C or Swift projects by:
1. Adding the appropriate code below into a view controller in your app.
2. Hook up a button to trigger the action (or call it programatically if you prefer).

### Swift
```swift
import CobrowseIO

class ExampleViewController: UIViewController {
    var sessionController: CBIOViewController!

    @IBAction func startCobrowse(sender: UIBarButtonItem) {
        self.sessionController = CBIOViewController()
        self.navigationController?.pushViewController(self.sessionController, animated: true)
    }

    // ... the rest of your view controller
}
```

For a full example written in Swift, see our Listr sample app at: https://github.com/cobrowseio/Listr

### Objective C
```objective-c
@import CobrowseIO;

@implementation ExampleViewController {
    CBIOViewController* sessionController;
}

-(IBAction) startCobrowse:(id)sender {
    sessionController = [[CBIOViewController alloc] init];
    [self.navigationController pushViewController:sessionController animated:YES];
}

// ... the rest of your view controller

@end
```

Make sure you've hooked up a trigger for the `startCobrowse` IBAction that we've just added, then head to <https://cobrowse.io/trial> and enter the 6 digit code that will be generated by your app when you trigger the action!

## Configuration

Once you've tested out your app using the trial dashboard you're ready to create an account and add in the free license key to your app. This will associate sessions from your mobile app with your Cobrowse account.

### Add your license key
Once you've signed up for a free account at [cobrowse.io](https://cobrowse.io), you'll be able to find your license key at <https://cobrowse.io/dashboard/settings>. Add this to your SDK setup:
```objective-c
CobrowseIO.instance.license = @"<your license key here>";
```
You can do this anywhere convenient, so long as it's run before displaying the CBIOViewController. We recommend adding it to the `didFinishLaunchingWithOptions` method of your app delegate.

## Requirements

* iOS 9.0 or later
