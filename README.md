# QLShowHUD
封装MBProgressHUD弹窗，可直接拖入项目使用

使用方法
导入头文件，在需要使用弹框的地方调用方法
```
[QLShowHUD showTextOnly:@"等小姐姐告诉我该干啥" configParameter:^(JKShowHUD *config) {
        config.cornerRadius = 20;
        config.backgroundColor  = [UIColor blackColor];
        config.labelColor = [UIColor whiteColor];
    } duration:1.0 inView:self.view];
```
    
 也可使用一句代码搞定，在此方法内部配置属性即可   
```
 [QLShowHUD showTextOnly:@"等小姐姐告诉我该干啥" configParameter:^(JKShowHUD *config) {
    } duration:1.0 inView:self.view];
```

 方法内部修改代码
```
 +(void)showTextOnly:(NSString *)text configParameter:(ConfigShowHUDBlock)config duration:(NSTimeInterval)sec inView:(UIView *)view
{
    QLShowHUD *hud = [[QLShowHUD alloc] initWithView:view];
    hud.text = text;
    hud.showTextOnly = YES;
    hud.margin = 10.f;
    // 配置额外的参数
    config(hud);
    //默认样式
    hud.labelColor = [UIColor whiteColor];
    hud.backgroundColor = [UIColor blackColor];
    hud.cornerRadius = 10;
    // 显示
    [hud show:YES];
    // 延迟sec后消失
    [hud hide:YES afterDelay:sec];
}
```
