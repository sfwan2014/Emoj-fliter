# Emoj-fliter

# 判断输入文本是否包含emoj， 包含则不输入

//是否含有表情



    - (BOOL)stringContainsEmoji:(NSString *)string
    {
        NSError *err = nil;
        NSString *pattern = @"[\\ud83c\\udc00-\\ud83c\\udfff]|[\\ud83d\\udc00-\\ud83d\\udfff]|[\\ud83e\\udd00-\\ud83e\\udfff]|[\\u2600-\\u27ff]";
        NSRegularExpression *reg = [NSRegularExpression regularExpressionWithPattern:pattern options:NSRegularExpressionCaseInsensitive|NSRegularExpressionUseUnicodeWordBoundaries error:&err];
        if (err) {
            return NO;
        }
    
        NSArray <NSTextCheckingResult*>*result = [reg matchesInString:string options:NSMatchingReportProgress range:NSMakeRange(0, string.length)];
        return result.count > 0;
    }




