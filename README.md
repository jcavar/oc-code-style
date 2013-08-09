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

###Variables
###Methods
