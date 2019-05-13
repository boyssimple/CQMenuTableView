# CQMenuTableView
一个支持多种形式的菜单,实用,扩展性强,使用简单


<img src="https://upload-images.jianshu.io/upload_images/3889208-afc1c2e553af1693.gif?imageMogr2/auto-orient/strip" alt="iOS ScreenShot 1" width="240px" style="width: 240px;" />

# Requirements
- iOS 7.0 or later
- ARC

# Install
## CocoaPods

```
pod 'CQMenuTableView'
```
## 手动导入
下载项目,将项目中的CQMenuTableView托人你的项目中即可

# Usage

## 只有标题

	#import "CQMenuTabView.h"
	
	CQMenuTabView *menTable = [[CQMenuTabView alloc] initWithFrame:CGRectMake(15, 100, UIScreen.mainScreen.bounds.size.width-30, 44)];
	menTable.titleFont = [UIFont systemFontOfSize:14];
	menTable.normaTitleColor = [UIColor blackColor];
    
    menTable.didSelctTitleColor = [UIColor redColor];
    menTable.showCursor = YES;
    menTable.cursorStyle = CQTabCursorWrap;
    menTable.layoutStyle = CQTabWrapContent;
    menTable.cursorHeight = 41;
    menTable.cursorView.backgroundColor = [UIColor colorWithRed:255/255.0 green:202/255.0 blue:204/255.0 alpha:1.0];
    menTable.backgroundColor = [UIColor whiteColor];
    
    //点击事件
    menTable.didTapItemAtIndexBlock = ^(UIView *view, NSInteger index) {
        NSLog(@"...%ld",(long)index);
    };
    [self.view addSubview:menTable];
    
    menTable.titles = @[@"分类一",@"分类一",@"分类一",@"分类一",@"分类一",@"分类一",@"分类一"];
    

## 其他样式,自定义

	buildTabViewWithItems 使用这个函数自定义
	
	//自定义
	  CQMenuTabView *menTable = [[CQMenuTabView alloc] initWithFrame:CGRectMake(15, 400, UIScreen.mainScreen.bounds.size.width-30, 44)];
  	 __block NSArray *titleArry =  @[@"分类一",@"分类一",@"分类一",@"分类一"];
    [menTable buildTabViewWithItems:^NSArray *{
        NSMutableArray *arry = [NSMutableArray array];
        for (int i = 0; i<titleArry.count; i++) {
            UIButton *button = [[UIButton alloc] initWithFrame:CGRectMake(0, 0, 50, 44)];
            [button setTitle:titleArry[i] forState:UIControlStateNormal];
            [arry addObject:button];
        }
        return arry;
    }];
    
    menTable.didTapItemAtIndexBlock = ^(UIView *view, NSInteger index) {
        NSLog(@"...%ld",(long)index);
    };
    
    menTable.normalizeTabItemBlock = ^(UIView *view, NSInteger index) {
        UIButton *button = (UIButton *)view;
        [button setTitleColor:[UIColor blackColor] forState:UIControlStateNormal];
    };
    
    menTable.hightlightTabItemBlock = ^(UIView *view, NSInteger index) {
        UIButton *button = (UIButton *)view;
        [button setTitleColor:[UIColor redColor] forState:UIControlStateNormal];
    };
    [self.view addSubview:menTable];
	
# License
[Apache]: http://www.apache.org/licenses/LICENSE-2.0
[MIT]: http://www.opensource.org/licenses/mit-license.php
[GPL]: http://www.gnu.org/licenses/gpl.html
[BSD]: http://opensource.org/licenses/bsd-license.php
[MIT license][MIT].
