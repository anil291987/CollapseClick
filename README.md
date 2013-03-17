CollapseClick
=============

A collapsible list that functions like a UITableView, except you can collapse and open cells on a click. Feed it UIViews for what is shown when each cell is open. Works via delegation similar to UITableView. *This is a UIScrollView Subclass.*
![ScreenShot](https://raw.github.com/bennyguitar/CollapseClick/master/CCScreen.png)

## Installation ##

Drag the included **CollapseClick.m, CollapseClick.h, CollapseClickCell.m, CollapseClickCell.h, CollapseClickCell.xib, CollapseClickArrow.h, CollapseClickArrow.m** files into your project. They are located in the top-level directory **CollapseClick**. You can see a demo of how to use these with the included Xcode project as well.

Import CollapseClick.h into your ViewController.h file. Next, in InterfaceBuilder, drag a UIScrollView out into your ViewController. Click on the Identity Inspector (3rd icon from the left, in the Right Pane in XCode) and change the class to <code>CollapseClick</code>. Connect up your CollapseClick to your ViewController.h file. Now add the CollapseClickDelegate. Your interface should look like this now:

```shell
#import <UIKit/UIKit.h>
#import "CollapseClick.h"

@interface ViewController : UIViewController <CollapseClickDelegate> {
  __weak IBOutlet CollapseClick *myCollapseClick;
}

@end
```

You are now ready to roll.


## Using CollapseClick ##

CollapseClick works off of delegation, similar to how UITableView appropriates and displays its data. There are 6 delegate methods you can implement, 3 of which are required.

**Required Delegate Methods**
```shell
-(int)numberOfCellsForCollapseClick {
    return (int)newInt;
}
```
This method is fairly clear, it's just the number of CollapseClick Cells to display. Usually you would use this similar to a UITableView with your data array's count being the return here.

```shell
-(NSString *)titleForCollapseClickAtIndex:(int)index {
    return (NSString*)newTitle;
}
```
This method just sets the Title Label's text for each CollapseClick Cell. 

```shell
-(UIView *)viewForCollapseClickContentViewAtIndex:(int)index {
    return (UIView *)contentView;
}
```
This method sets the ContentView property of each CollapseClick Cell. This is the fun part. You can use programmatically created UIViews or use instance variables of UIViews you create in Interface Builder. As long as it's a UIView, this method will put it in the collapsible section of your CollapseClick Cell.
 
 
**Optional Delegate Methods**
```shell
-(UIColor *)colorForCollapseClickTitleViewAtIndex:(int)index {
    return (UIColor *)color;
}
```
This method sets the background color for your CollapseClick Cell's header or TitleView. It's the red area in the screenshot above. Default is <code>[UIColor colorWithWhite:0.4 alpha:1.0]</code>

```shell
-(UIColor *)colorForTitleLabelAtIndex:(int)index {
    return (UIColor *)color;
}
```
This method sets the Title Label's textColor property. Default is <code>[UIColor colorWithWhite]</code>

```shell
-(UIColor *)colorForTitleArrowAtIndex:(int)index {
    return (UIColor *)color;
}
```
This method sets the color of the arrow at the right of each CollapseClick Cell. Default is <code>[UIColor colorWithWhite:0.0 alpha:0.35]</code>
 
 
**CollapseClick Additional Methods**
```shell
-(void)reloadCollapseClick;
```
This method will redraw and lay out your CollapseClick View. Call this method after a change to your data that you are using in conjunction with CollapseClick.

```shell
-(CollapseClickCell *)collapseClickCellForIndex:(int)index;
```
This method will return the entire CollapseClickCell at specified index. There is also a method for returning just the ContentView further down.

```shell
-(UIView *)contentViewForCellAtIndex:(int)index;
```
This method will return the ContentView for the CollapseClickCell at specified index.

```shell
-(void)scrollToCollapseClickCellAtIndex:(int)index animated:(BOOL)animated;
```
This method scrolls your CollapseClick to the cell at your specified index. You can animate this process or not.
 
 
Reap What I Sow!
================

This project is distributed under the standard MIT License. Please use this and twist it in whatever fashion you wish - and recommend any cool changes to help the code.
