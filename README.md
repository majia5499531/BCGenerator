# BCGenerator
BCGenerator 一个比特币生成私钥 公钥 地址的库

### 使用方法：
可以直接使用pod集成，也可以将代码拖入项目中；
pod 集成方法：
```
pod 'BCGenerator'
```

### 依赖类库：
```
  s.dependency "CBSecp256k1"
  s.dependency "CBBase58"
```
CBSecp256k1 是从 iOS比特币项目CoreBitcoin 摘出来的椭圆双曲线算法部分。
CBBase58 是从 iOS比特币项目CoreBitcoin 摘出来的base58算法部分，并且集成了RIPEMD算法的 RIPEMD-160。

### 目录
库文件目录如下：
```
BCGenerator.h	EncryptUtil.h	NSData+UTF8.h	NSString+SHA.h
BCGenerator.m	EncryptUtil.m	NSData+UTF8.m	NSString+SHA.m
```
### BCGenerator使用
其中BCGenerator 就是生成公钥私钥地址的对象，使用方法如下：
```
 #import "BCGenerator.h"
 
 -(void)test{
 BCGenerator * generator = [[BCGenerator alloc]initWithWith:@"pseudorandom sequence"];
 NSLog(@"\n generator.rootPrivatekey = %@\n generator.mainProcessingKey = %@\n generator.rootPublickey = %@\n generator.address = %@",generator.rootPrivatekey,generator.mainProcessingKey,generator.rootPublickey,generator.address);
 }
```
### BCGenerator的头文件
```
@property(strong,nonatomic)NSData * rootPrivatekey;
//主私钥

@property(strong,nonatomic)NSData * mainProcessingKey;
//主链编码

@property(strong,nonatomic)NSData * rootPublickey;
//主公钥

@property(strong,nonatomic)NSString * address;
//由主公钥生成的比特币地址

/**
 根据伪随机数生成种子
 
 @param seedStr seedStr 根据伪随机数
 @return return instancetype 生成的对象
 */
-(instancetype)initWithWith:(NSString *)seedStr;

```

