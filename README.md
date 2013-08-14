#Objective-C code style

Objective-C code style conventions used in Planet 1107. 
Because of the nature of this topic, things that are
mentioned here are subjective, but we tried to find reasons why to use one code style instead of some other. Also, this
document is not definitive, and can be changed if we find arguments for other code style.
In [issues](https://github.com/jcavar/oc-code-style/issues) we are discussing about problems we encountered.

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
###Variables
###Methods

When naming methods which are IBActions method name is composed of {class_name}{control_name}{event}. Provide sender 
as parameter even if not required.

**For example:**
```objc
- (IBAction)buttonFilterTouchUpInside:(id)sender;
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

