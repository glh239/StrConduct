# StrConduct
字符串处理  去除指定字符串两边空格
有个朋友问的 帮他写的 顺带分享给大家

#import "ViewController.h"

#define YOURSTR @"str"

@interface ViewController ()


@end


@implementation ViewController

- (void)viewDidLoad {

    [super viewDidLoad];
    
    
    NSString *str = @"去 掉 空 格 str 看 看";
    
    NSLog(@"处理前:%@",str);
    
    NSLog(@"处理后:%@",[self stringConductWithStr:str]);
    
}

- (NSString *)stringConductWithStr:(NSString *)str{

    NSMutableString *mulStr = [[NSMutableString alloc] initWithString:str];
    
    if ([str containsString:YOURSTR]) {
       
       NSRange range = [mulStr rangeOfString:YOURSTR];
       
       if (range.location >= 1 && [[mulStr substringWithRange:NSMakeRange(range.location - 1, 1)] isEqualToString:@" "] && [[mulStr substringWithRange:NSMakeRange(range.location + range.length, 1)] isEqualToString:@" "]) {
       
            [mulStr replaceCharactersInRange:NSMakeRange(range.location - 1, range.length + 2) withString:YOURSTR];
            
        }
        
    }
    
    return [NSString stringWithFormat:@"%@",mulStr];
    
}

@end
