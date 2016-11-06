# Passingvaluefromoneviewcontrollertoanthorviewcontroller
Passing value from one view controller to another view controller 
Adding program :
ViewController.h
@interface ViewController : UIViewController{
    IBOutlet UIButton *firstbutton;
    
    NSUserDefaults *userDef;
    
    AppDelegate *appDelegate;
    
}
-(IBAction)firstclick:(id)sender;
@property(nonatomic,retain)NSString *five;
@end
ViewController.m
#import "ViewController.h"
#import "SecondViewController.h"
#import "ThirdViewController.h"
@interface ViewController ()

@end

@implementation ViewController
@synthesize five;
- (void)viewDidLoad {
    
    
    
    appDelegate = (AppDelegate*)[[UIApplication sharedApplication]delegate];
    appDelegate.globalString= @"tesss";
    
    userDef= [NSUserDefaults standardUserDefaults];
    [userDef setObject:@"Ram" forKey:@"username"];
    [userDef synchronize];
    
    
    [super viewDidLoad];
    // Do any additional setup after loading the view, typically from a nib.
}
-(IBAction)firstclick:(id)sender{
    SecondViewController *second=[self.storyboard instantiateViewControllerWithIdentifier:@"second"];
    second.secstring=@"first viewcontroller to second value is passed";
    [[self navigationController]pushViewController:second animated:YES];

    
}


- (void)didReceiveMemoryWarning {
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}



@end

