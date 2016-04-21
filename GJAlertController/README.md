# GJAlertController
##简介
UIAlertController是一个在iOS8才被加入的类，在低于iOS8版本的设备上无法使用，此库可让使用者在低版本中也可以使用UIAlertController。

也就是说，你在开发的时候尽管使用UIAlertController，就当它是iOS很早版本就有的类，不必去在代码中判断如果iOS版本小于8，而去用AlertView或者ActionSheet。

当app运行的iOS版本中没有UIAlertController的时候，GJAlertController这个类库会自动用UIAlertView、UIActionSheet去帮你实现你想要的功能。

### Import

#### Copy and import

Drag and drop the files in GJAlertController folder to the project.

#### CocoaPods

`pod 'GJAlertController`



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
