#Objective-C code style

Objective-C code style conventions used in Planet 1107. 
Because of the nature of this topic, things that are
mentioned here are subjective, but we tried to find reasons why to use one code style instead of some other. Also, this
document is not definitive, and can be changed if we find arguments for other code style.
In [issues](https://github.com/jcavar/oc-code-style/issues) we are discussing about problems we encountered.

##Code structure

###If else

If you need to cover more than 2 cases in if else statment, write them in same intendation. 
That is not correct because they need to be nested, but that is not readable, and prefer this.

**For example:**

```objc
if (isTrue) {
    // code to do
} else if (isFalse) {
    //code to do
} else {
    //code to do
}
```

###for loop

```objc
for (int i = 0; i < length; i++) {
    //code to do
}
```

###do while loop

```objc
do {
        // code to do
} while (isTrue);
```

###Spacings
###Dot notation

If possible always use dot notation. It is simpler and more readable. Use dot notation even if you are 
accessing object sending message with brackets and after you need to access object property.

**For example:** 

```objc
UIApplicationDelegate *applicationDelegate = [UIApplication sharedApplication].delegate;
```

**Not:** 

```objc
[[UIApplication sharedApplication] delegate];
```

###Ternary operator
Don't use ternary operator because they are unreadable, better write if else statment.
###Xib files
Create xib files always if you don't have reason for not creating. 
Xib files are simple to edit and more readable than code you write.
####Tags
Don't use tags in xib files because when tags are used in code someone else can't know what that tag is used for.
Other problem is that someone can give same tag to other view as you do for your view.
##Naming

###Properties

```objc
@property (strong, nonatomic) IBOutlet UIButton *buttonMonth;
@property (strong, nonatomic) IBOutlet UIView *viewInputMonth;
@property (strong, nonatomic) IBOutlet UIPickerView *pickerViewMonth;
```

Because of order in which interface builder inserts property attributes, we decide to use the same style. 
So `strong`, `weak` or `assign`, `retain` are first in sequence, then `nonatomic` if property is `nonatomic`. 
If property is `atomic`, that also must be explicitly defined. After that `readonly` if needed, but `readwrite` 
is not needed to be explicitly defined. On last place `getter` of `setter` if needed.

When naming properites of UIKit, the name of property starts with the name of the class which is used and after name 
of class some description comes.

**For example:**  
```objc
@property (strong, nonatomic) IBOutlet UIButton *buttonMonth;
```
**Not:**  
```objc
@property (strong, nonatomic) IBOutlet UIButton *monthButton;
@property (strong, nonatomic) IBOutlet UIButton *month;
```

Also, this rules can be applied on classes from NSFoundation framework.

**For example:**  
```objc
@property (strong, nonatomic) NSArray *arrayOfMonths;
```
**Not:**  
```objc
@property (strong, nonatomic) NSArray *months;
@property (strong, nonatomic) NSArray *array;
```

This can be applied only to where property is describing complex types(classes, structs, enums, ...), not on primitive
data types for example:

**Not:**  
```objc
@property (assign, nonatomic) BOOL boolValid;
@property (assign, nonatomic) int intCount;
```

###Variables

####Class variables
####Local variables

###Methods

When naming methods which are IBActions method name is composed of {class_name}{control_name}{event}. Provide sender, with it's correct class, as parameter even if not required.

**For example:**
```objc
- (IBAction)buttonFilterTouchUpInside:(UIButton *)sender;
```
**Not:**
```objc
- (IBAction)buttonFilterClick:(id)sender;
- (IBAction)buttonClick:(id)sender;
- (IBAction)clickOnButton:(id)sender;
- (IBAction)filter:(id)sender;
- (IBAction)buttonFilterClick;
```
###Functions and Macros
### Files
####Classes
####Protocols
####Header files
####Images
##Structure

###Project structure

###File structure

#### .m file structure

Each .m file must be divided into one or multiple sections for simpler walking throuhgt file and finding each part.
For dividing code into sections we are using #pragma mark. For each classic section we have #pragma mark.

```objc
#pragma mark - Object lifecycle
#pragma mark - View lifecycle
#pragma mark - UITableViewDataSource methods
#pragma mark - UITableViewDelegate methods
```
##Specific classes

###Networking class
