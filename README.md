# GJAlertController
## Description
The fork of GJAlertController.

Use the UIAlertController directly even in iOS 7. This library will choose to use `UIAlertView` or `UIActionSheet` when needed.

### Import

#### Copy and import

Drag and drop the files in GJAlertController folder to the project.

#### CocoaPods

`pod 'GJAlertController, :git => 'https://github.com/gowalla/AFNetworking.git'`

### Usage：directly use `UIAlerController` regardless of the iOS version

```Objective-C
// create instance
UIAlertController *alertVC = [UIAlertController alertControllerWithTitle:@"title" message:@"message" preferredStyle:UIAlertControllerStyleAlert];

//add action
[alertVC addAction:[UIAlertAction actionWithTitle:@"ok" style:UIAlertActionStyleDefault handler:^(UIAlertAction * _Nonnull action) {
    NSLog(@"%@", action.title);
}]];

// add action
[alertVC addAction:[UIAlertAction actionWithTitle:@"cancel" style:UIAlertActionStyleDefault handler:^(UIAlertAction * _Nonnull action) {
    NSLog(@"%@", action.title);
}]];

// add UITextField. Since UIAlertView support maximum two textField, so if you add more than two UITextField, before iOS 8 it will only show first two, and iOS 8 or later will display all.
[alertVC addTextFieldWithConfigurationHandler:^(UITextField *textField) {
    textField.placeholder = @"huhu";
}];

// show
[self presentViewController:alertVC animated:YES completion:nil];
```

If you want to test GJAlertController but without iOS 7 device, you can directly use `GJAlertController`, `GJAlertAction` and other related methods. When display, use the following API methods.

```Objective-C
// show alert
[alert testShow];

// show action sheet
[actionSheet testShowActionSheet];
```
