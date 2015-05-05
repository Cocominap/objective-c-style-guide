# NYTimes Objective-C Style Guide
# NYTimes Objective-C スタイルガイド	

This style guide outlines the coding conventions of the iOS teams at The New York Times. We welcome your feedback in [issues](https://github.com/NYTimes/objetive-c-style-guide/issues), [pull requests](https://github.com/NYTimes/objetive-c-style-guide/pulls) and [tweets](https://twitter.com/nytimesmobile). Also, [we’re hiring](http://jobs.nytco.com/job/New-York-iOS-Developer-Job-NY-10001/73366300/).

This style guide outlines the coding conventions of the iOS teams at The New York Times. We welcome your feedback in [issues](https://github.com/NYTimes/objetive-c-style-guide/issues), [pull requests](https://github.com/NYTimes/objetive-c-style-guide/pulls) and [tweets](https://twitter.com/nytimesmobile). Also, [we’re hiring](http://jobs.nytco.com/job/New-York-iOS-Developer-Job-NY-10001/73366300/).

このスタイルガイドは、ニューヨークタイムズの iOS チームにおけるコーディング慣例の概要です。フィードバックを歓迎します。 [issues](https://github.com/NYTimes/objetive-c-style-guide/issues), [pull requests](https://github.com/NYTimes/objetive-c-style-guide/pulls) そして [ツイッター](https://twitter.com/nytimesmobile) よりお願いします。また、[人材募集中です](http://jobs.nytco.com/job/New-York-iOS-Developer-Job-NY-10001/73366300/)。

Thanks to all of [our contributors](https://github.com/NYTimes/objective-c-style-guide/contributors).

すべての [貢献いただいた方々](https://github.com/NYTimes/objective-c-style-guide/contributors) に感謝いたします。

## Introduction

## イントロダクション

Here are some of the documents from Apple that informed the style guide. If something isn’t mentioned here, it’s probably covered in great detail in one of these:

ここでは、本スタイルガイドが情報源としている Apple のドキュメントをいくつか紹介します。本ガイドで述べられていないことも、以下ドキュメントでは詳細にカバーされていることでしょう。

* [The Objective-C Programming Language](http://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/ObjectiveC/Introduction/introObjectiveC.html)
* [Cocoa Fundamentals Guide](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CocoaFundamentals/Introduction/Introduction.html)
* [Coding Guidelines for Cocoa](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html)
* [iOS App Programming Guide](http://developer.apple.com/library/ios/#documentation/iphone/conceptual/iphoneosprogrammingguide/Introduction/Introduction.html)

* [Objective-C プログラミング言語](https://developer.apple.com/jp/documentation/ObjC.pdf)
* [Cocoa Fundamentals Guide](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CocoaFundamentals/Introduction/Introduction.html)
* [Cocoa向け コーディングガイドライン](https://developer.apple.com/jp/documentation/CodingGuidelines.pdf)
* [iOSアプリケーション プログラミングガイド](https://developer.apple.com/jp/documentation/iPhoneAppProgrammingGuide.pdf)

## Table of Contents

* [Dot Notation Syntax](#dot-notation-syntax)
* [ドット記法](#ドット記法)

* [Spacing](#spacing)
* [スペーシング](#スペーシング)

* [Conditionals](#conditionals)
* [Ternary Operator](#ternary-operator)
* [条件演算子](#条件演算子)
* [三項演算子](#三項演算子)

* [Error handling](#error-handling)
* [エラーハンドリング](#エラーハンドリング)

* [Methods](#methods)
* [メソッド](#メソッド)

* [Variables](#variables)
* [変数](#変数)

* [Naming](#naming)
	* [Categories](#categories)
* [名前付け](#名前付け)
	* [カテゴリ](#カテゴリ)

* [Comments](#comments)
* [コメント](#コメント)

* [Init & Dealloc](#init-and-dealloc)
* [Init と Dealloc](#Init と Dealloc)

* [Literals](#literals)
* [リテラル](#リテラル)

* [CGRect Functions](#cgrect-functions)
* [CGRect に関する関数](#CGRect に関する関数)

* [Constants](#constants)
* [定数](#定数)

* [Enumerated Types](#enumerated-types)
* [列挙型](#enumerated-types)

* [Bitmasks](#bitmasks)
* [ビットマスク](#ビットマスク)

* [Private Properties](#private-properties)
* [プライベートプロパティ](#プライベートプロパティ)

* [Image Naming](#image-naming)
* [画像の名前](#画像の名前)

* [Booleans](#booleans)
* [ブーリアン](#ブーリアン)

* [Singletons](#singletons)
* [シングルトン](#シングルトン)

* [Imports](#imports)
* [インポート](#インポート)

* [Xcode Project](#xcode-project)
* [Xcode プロジェクト](#Xcode プロジェクト)



## ドット記法

Dot notation should **always** be used for accessing and mutating properties. Bracket notation is preferred in all other instances.

ドット記法は **常に** プロパティへアクセスしたり、変更したりする目的で使いましょう。ブラケット記法は、その他すべてのインスタンスで使用することが望ましいです。


**For example:**
```objc
view.backgroundColor = [UIColor orangeColor];
[UIApplication sharedApplication].delegate;
```

**Not:**
```objc
[view setBackgroundColor:[UIColor orangeColor]];
UIApplication.sharedApplication.delegate;
```

## スペーシング

* Indent using 4 spaces. Never indent with tabs. Be sure to set this preference in Xcode.
* Method braces and other braces (`if`/`else`/`switch`/`while` etc.) always open on the same line as the statement but close on a new line.

* インデントは４文字のスペースで表記しましょう。決してタブは使わないこと。必ず Xcode でそのように設定しましょう。
* メソッドの開き括弧、および他 (`if`/`else`/`switch`/`while` etc.) の開き括弧は、定義や条件式と同じ行に、閉じ括弧は新しい行に書きましょう。

**For example:**
```objc
if (user.isHappy) {
// Do something
}
else {
// Do something else
}
```
* There should be exactly one blank line between methods to aid in visual clarity and organization.
* Whitespace within methods should be used to separate functionality (though often this can indicate an opportunity to split the method into several, smaller methods). In methods with long or verbose names, a single line of whitespace may be used to provide visual separation before the method’s body.
* `@synthesize` and `@dynamic` should each be declared on new lines in the implementation.

* メソッドとメソッドの間の空行はピッタリ１行にしましょう。見やすくなりますし、構造の助けになります。
* Whitespace within methods should be used to separate functionality (though often this can indicate an opportunity to split the method into several, smaller methods). In methods with long or verbose names, a single line of whitespace may be used to provide visual separation before the method’s body.
* `@synthesize` and `@dynamic` should each be declared on new lines in the implementation.


## 条件演算子

Conditional bodies should always use braces even when a conditional body could be written without braces (e.g., it is one line only) to prevent [errors](https://github.com/NYTimes/objective-c-style-guide/issues/26#issuecomment-22074256). These errors include adding a second line and expecting it to be part of the if-statement. Another, [even more dangerous defect](http://programmers.stackexchange.com/a/16530) may happen where the line “inside” the if-statement is commented out, and the next line unwittingly becomes part of the if-statement. In addition, this style is more consistent with all other conditionals, and therefore more easily scannable.

**For example:**
```objc
if (!error) {
return success;
}
```

**Not:**
```objc
if (!error)
return success;
```

or

```objc
if (!error) return success;
```

### 三項演算子

The ternary operator, `?` , should only be used when it increases clarity or code neatness. A single condition is usually all that should be evaluated. Evaluating multiple conditions is usually more understandable as an if statement, or refactored into named variables.

**For example:**
```objc
result = a > b ? x : y;
```

**Not:**
```objc
result = a > b ? x = c > d ? c : d : y;
```

## エラーハンドリング

When methods return an error parameter by reference, switch on the returned value, not the error variable.

**For example:**
```objc
NSError *error;
if (![self trySomethingWithError:&error]) {
// Handle Error
}
```

**Not:**
```objc
NSError *error;
[self trySomethingWithError:&error];
if (error) {
// Handle Error
}
```

Some of Apple’s APIs write garbage values to the error parameter (if non-NULL) in successful cases, so switching on the error can cause false negatives (and subsequently crash).

## メソッド

In method signatures, there should be a space after the scope (`-` or `+` symbol). There should be a space between the method segments.

**For Example**:
```objc
- (void)setExampleText:(NSString *)text image:(UIImage *)image;
```

## 変数

Variables should be named descriptively, with the variable’s name clearly communicating what the variable _is_ and pertinent information a programmer needs to use that value properly.

**For example:**

* `NSString *title`: It is reasonable to assume a “title” is a string.
* `NSString *titleHTML`: This indicates a title that may contain HTML which needs parsing for display. _“HTML” is needed for a programmer to use this variable effectively._
* `NSAttributedString *titleAttributedString`: A title, already formatted for display. _`AttributedString` hints that this value is not just a vanilla title, and adding it could be a reasonable choice depending on context._
* `NSDate *now`: _No further clarification is needed._
* `NSDate *lastModifiedDate`: Simply `lastModified` can be ambiguous; depending on context, one could reasonably assume it is one of a few different types.
* `NSURL *URL` vs. `NSString *URLString`: In situations when a value can reasonably be represented by different classes, it is often useful to disambiguate in the variable’s name.
* `NSString *releaseDateString`: Another example where a value could be represented by another class, and the name can help disambiguate.

Single letter variable names should be avoided except as simple counter variables in loops.

Asterisks indicating a type is a pointer should be “attached to” the variable name. **For example,** `NSString *text` **not** `NSString* text` or `NSString * text`, except in the case of constants (`NSString * const NYTConstantString`).

Property definitions should be used in place of naked instance variables whenever possible. Direct instance variable access should be avoided except in initializer methods (`init`, `initWithCoder:`, etc…), `dealloc` methods and within custom setters and getters. For more information, see [Apple’s docs on using accessor methods in initializer methods and `dealloc`](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/MemoryMgmt/Articles/mmPractical.html#//apple_ref/doc/uid/TP40004447-SW6).

**For example:**

```objc
@interface NYTSection: NSObject

@property (nonatomic) NSString *headline;

@end
```

**Not:**

```objc
@interface NYTSection : NSObject {
NSString *headline;
}
```

#### Variable Qualifiers

When it comes to the variable qualifiers [introduced with ARC](https://developer.apple.com/library/ios/releasenotes/objectivec/rn-transitioningtoarc/Introduction/Introduction.html#//apple_ref/doc/uid/TP40011226-CH1-SW4), the qualifier (`__strong`, `__weak`, `__unsafe_unretained`, `__autoreleasing`) should be placed between the asterisks and the variable name, e.g., `NSString * __weak text`. 

## 名前付け

Apple naming conventions should be adhered to wherever possible, especially those related to [memory management rules](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/MemoryMgmt/Articles/MemoryMgmt.html) ([NARC](http://stackoverflow.com/a/2865194/340508)).

Long, descriptive method and variable names are good.

**For example:**

```objc
UIButton *settingsButton;
```

**Not**

```objc
UIButton *setBut;
```

A three letter prefix (e.g., `NYT`) should always be used for class names and constants, however may be omitted for Core Data entity names. Constants should be camel-case with all words capitalized and prefixed by the related class name for clarity. A two letter prefix (e.g., `NS`) is [reserved for use by Apple](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/DefiningClasses/DefiningClasses.html#//apple_ref/doc/uid/TP40011210-CH3-SW12).

**For example:**

```objc
static const NSTimeInterval NYTArticleViewControllerNavigationFadeAnimationDuration = 0.3;
```

**Not:**

```objc
static const NSTimeInterval fadetime = 1.7;
```

Properties and local variables should be camel-case with the leading word being lowercase.

Instance variables should be camel-case with the leading word being lowercase, and should be prefixed with an underscore. This is consistent with instance variables synthesized automatically by LLVM. **If LLVM can synthesize the variable automatically, then let it.**

**For example:**

```objc
@synthesize descriptiveVariableName = _descriptiveVariableName;
```

**Not:**

```objc
id varnm;
```

### カテゴリ

Categories may be used to concisely segment functionality and should be named to describe that functionality.

**For example:**

```objc
@interface UIViewController (NYTMediaPlaying)
@interface NSString (NSStringEncodingDetection)
```

**Not:**

```objc
@interface NYTAdvertisement (private)
@interface NSString (NYTAdditions)
```

## コメント

When they are needed, comments should be used to explain **why** a particular piece of code does something. Any comments that are used must be kept up-to-date or deleted.

Block comments should generally be avoided, as code should be as self-documenting as possible, with only the need for intermittent, few-line explanations. This does not apply to those comments used to generate documentation.

## init and dealloc

`dealloc` methods should be placed at the top of the implementation, directly after the `@synthesize` and `@dynamic` statements. `init` should be placed directly below the `dealloc` methods of any class.

`init` methods should be structured like this:

```objc
- (instancetype)init {
self = [super init]; // or call the designated initializer
if (self) {
// Custom initialization
}

return self;
}
```

## リテラル

`NSString`, `NSDictionary`, `NSArray`, and `NSNumber` literals should be used whenever creating immutable instances of those objects. Pay special care that `nil` values not be passed into `NSArray` and `NSDictionary` literals, as this will cause a crash.

**For example:**

```objc
NSArray *names = @[@"Brian", @"Matt", @"Chris", @"Alex", @"Steve", @"Paul"];
NSDictionary *productManagers = @{@"iPhone" : @"Kate", @"iPad" : @"Kamal", @"Mobile Web" : @"Bill"};
NSNumber *shouldUseLiterals = @YES;
NSNumber *buildingZIPCode = @10018;
```

**Not:**

```objc
NSArray *names = [NSArray arrayWithObjects:@"Brian", @"Matt", @"Chris", @"Alex", @"Steve", @"Paul", nil];
NSDictionary *productManagers = [NSDictionary dictionaryWithObjectsAndKeys: @"Kate", @"iPhone", @"Kamal", @"iPad", @"Bill", @"Mobile Web", nil];
NSNumber *shouldUseLiterals = [NSNumber numberWithBool:YES];
NSNumber *buildingZIPCode = [NSNumber numberWithInteger:10018];
```

## `CGRect` に関する関数

When accessing the `x`, `y`, `width`, or `height` of a `CGRect`, always use the [`CGGeometry` functions](http://developer.apple.com/library/ios/#documentation/graphicsimaging/reference/CGGeometry/Reference/reference.html) instead of direct struct member access. From Apple's `CGGeometry` reference:

> All functions described in this reference that take CGRect data structures as inputs implicitly standardize those rectangles before calculating their results. For this reason, your applications should avoid directly reading and writing the data stored in the CGRect data structure. Instead, use the functions described here to manipulate rectangles and to retrieve their characteristics.

**For example:**

```objc
CGRect frame = self.view.frame;

CGFloat x = CGRectGetMinX(frame);
CGFloat y = CGRectGetMinY(frame);
CGFloat width = CGRectGetWidth(frame);
CGFloat height = CGRectGetHeight(frame);
```

**Not:**

```objc
CGRect frame = self.view.frame;

CGFloat x = frame.origin.x;
CGFloat y = frame.origin.y;
CGFloat width = frame.size.width;
CGFloat height = frame.size.height;
```

## 定数

Constants are preferred over in-line string literals or numbers, as they allow for easy reproduction of commonly used variables and can be quickly changed without the need for find and replace. Constants should be declared as `static` constants and not `#define`s unless explicitly being used as a macro.

**For example:**

```objc
static NSString * const NYTAboutViewControllerCompanyName = @"The New York Times Company";

static const CGFloat NYTImageThumbnailHeight = 50.0;
```

**Not:**

```objc
#define CompanyName @"The New York Times Company"

#define thumbnailHeight 2
```

## 列挙型

When using `enum`s, use the new fixed underlying type specification, which provides stronger type checking and code completion. The SDK includes a macro to facilitate and encourage use of fixed underlying types: `NS_ENUM()`.

**Example:**

```objc
typedef NS_ENUM(NSInteger, NYTAdRequestState) {
NYTAdRequestStateInactive,
NYTAdRequestStateLoading
};
```

## ビットマスク

When working with bitmasks, use the `NS_OPTIONS` macro.

**Example:**

```objc
typedef NS_OPTIONS(NSUInteger, NYTAdCategory) {
NYTAdCategoryAutos      = 1 << 0,
NYTAdCategoryJobs       = 1 << 1,
NYTAdCategoryRealState  = 1 << 2,
NYTAdCategoryTechnology = 1 << 3
};
```

## プライベートプロパティ

Private properties should be declared in class extensions (anonymous categories) in the implementation file of a class.

**For example:**

```objc
@interface NYTAdvertisement ()

@property (nonatomic, strong) GADBannerView *googleAdView;
@property (nonatomic, strong) ADBannerView *iAdView;
@property (nonatomic, strong) UIWebView *adXWebView;

@end
```

## 画像の名前

Image names should be named consistently to preserve organization and developer sanity. They should be named as one camel case string with a description of their purpose, followed by the un-prefixed name of the class or property they are customizing (if there is one), followed by a further description of color and/or placement, and finally their state.

**For example:**

* `RefreshBarButtonItem` / `RefreshBarButtonItem@2x` and `RefreshBarButtonItemSelected` / `RefreshBarButtonItemSelected@2x`
* `ArticleNavigationBarWhite` / `ArticleNavigationBarWhite@2x` and `ArticleNavigationBarBlackSelected` / `ArticleNavigationBarBlackSelected@2x`.

Images that are used for a similar purpose should be grouped in respective groups in an Images folder or Asset Catalog.

## ブーリアン

Never compare something directly to `YES`, because `YES` is defined as `1`, and a `BOOL` in Objective-C is a `CHAR` type that is 8 bits long (so a value of `11111110` will return `NO` if compared to `YES`).

**For an object pointer:**

```objc
if (!someObject) {
}

if (someObject == nil) {
}
```

**For a `BOOL` value:**

```objc
if (isAwesome)
if (!someNumber.boolValue)
if (someNumber.boolValue == NO)
```

**Not:**

```objc
if (isAwesome == YES) // Never do this.
```

If the name of a `BOOL` property is expressed as an adjective, the property’s name can omit the `is` prefix but should specify the conventional name for the getter.

**For example:**

```objc
@property (assign, getter=isEditable) BOOL editable;
```

_Text and example taken from the [Cocoa Naming Guidelines](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingIvarsAndTypes.html#//apple_ref/doc/uid/20001284-BAJGIIJE)._

## シングルトン

Singleton objects should use a thread-safe pattern for creating their shared instance.
```objc
+ (instancetype)sharedInstance {
static id sharedInstance = nil;

static dispatch_once_t onceToken;
dispatch_once(&onceToken, ^{
sharedInstance = [[[self class] alloc] init];
});

return sharedInstance;
}
```
This will prevent [possible and sometimes frequent crashes](http://cocoasamurai.blogspot.com/2011/04/singletons-your-doing-them-wrong.html).

## インポート

If there is more than one import statement, group the statements [together](http://ashfurrow.com/blog/structuring-modern-objective-c). Commenting each group is optional.

Note: For modules use the [@import](http://clang.llvm.org/docs/Modules.html#using-modules) syntax.

```objc
// Frameworks
@import QuartzCore;

// Models
#import "NYTUser.h"

// Views
#import "NYTButton.h"
#import "NYTUserView.h"
```

## Xcode プロジェクト

The physical files should be kept in sync with the Xcode project files in order to avoid file sprawl. Any Xcode groups created should be reflected by folders in the filesystem. Code should be grouped not only by type, but also by feature for greater clarity.

When possible, always turn on “Treat Warnings as Errors” in the target’s Build Settings and enable as many [additional warnings](http://boredzo.org/blog/archives/2009-11-07/warnings) as possible. If you need to ignore a specific warning, use [Clang’s pragma feature](http://clang.llvm.org/docs/UsersManual.html#controlling-diagnostics-via-pragmas).

# Other Objective-C Style Guides

If ours doesn’t fit your tastes, have a look at some other style guides:

* [Google](http://google-styleguide.googlecode.com/svn/trunk/objcguide.xml)
* [GitHub](https://github.com/github/objective-c-conventions)
* [Adium](https://trac.adium.im/wiki/CodingStyle)
* [Sam Soffes](https://gist.github.com/soffes/812796)
* [CocoaDevCentral](http://cocoadevcentral.com/articles/000082.php)
* [Luke Redpath](http://lukeredpath.co.uk/blog/2011/06/28/my-objective-c-style-guide/)
* [Marcus Zarra](http://www.cimgf.com/zds-code-style-guide/)
* [Wikimedia](https://www.mediawiki.org/wiki/Wikimedia_Apps/Team/iOS/ObjectiveCStyleGuide)
