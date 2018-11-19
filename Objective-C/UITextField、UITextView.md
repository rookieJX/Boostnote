### UITextField、UITextView

##### 限制输入长度

```objc

#define kRecordingTitleLength 16

- (void)actionForTitleTextFieldChaged:(UITextField *)textField {
    NSString *toBeString = textField.text;
    NSString * lang       = [[[UIApplication sharedApplication] textInputMode] primaryLanguage];
    if ([lang isEqualToString:@"zh-Hans"]) { // 如果输入的是简体中文
        UITextRange * selectRange = [textField markedTextRange];
        // 获取高亮部分
        UITextPosition * position = [textField positionFromPosition:selectRange.start offset:0];
        // 没有高亮选择的字，则对已输入的文字进行字数统计和限制
        if (!position) {
            if (toBeString.length > kRecordingTitleLength) {
                self.titleTextField.text = [toBeString substringToIndex:kRecordingTitleLength];
            } else {
                [self feedbackStringWithMessage:toBeString];
            }
        }
    } else { // 中文输入法以外的直接对其进行统计限制即可，不考虑其他情况
        if (toBeString.length > kRecordingTitleLength) {
            // 提醒最长字符
            self.titleTextField.text = [toBeString substringToIndex:kRecordingTitleLength];
        }else {
            [self feedbackStringWithMessage:toBeString];
            
        }
    }
}


- (void)feedbackStringWithMessage:(NSString *)message {
    
   // Do something
    
}
```