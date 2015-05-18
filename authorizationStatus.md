#1.判断用户是否有权限访问相册

- import \<AssetsLibrary/AssetsLibrary.h\>
- ALAuthorizationStatus author = [ALAssetsLibrary authorizationStatus];
- if (author == ALAuthorizationStatusRestricted || author == ALAuthorizationStatusDenied)
        {
           //无权限
        }

- typedef enum {
  -   ALAuthorizationStatusNotDetermined = 0, // 用户尚未做出选择这个应用程序的问候
    - ALAuthorizationStatusRestricted,        // 此应用程序没有被授权访问的照片数据。可能是家长控制权限
    - ALAuthorizationStatusDenied,            // 用户已经明确否认了这一照片数据的应用程序访问
   -  ALAuthorizationStatusAuthorized         // 用户已经授权应用访问照片数据
- } ALAuthorizationStatus;

#2.判断用户是否有权限访问相机

- iOS7之前都可以访问相机，iOS7之后访问相机有权限设置

- import \<AVFoundation/AVCaptureDevice.h\>
- import \<AVFoundation/AVMediaFormat.h\>
- AVAuthorizationStatus authStatus = [AVCaptureDevice authorizationStatusForMediaType:AVMediaTypeVideo];
- if (authStatus == AVAuthorizationStatusRestricted || authStatus == AVAuthorizationStatusDenied)
        {
            //无权限
        }

#3.判断是否开启定位服务

- [CLLocationManager locationServicesEnabled] //检测的是整个的iOS系统的定位服务是否开启
- 检测当前应用的定位服务是否开启需要通过一下方法来检测
- (void)locationManager:(CLLocationManager *)manager
       didFailWithError:(NSError *)error
       
#4.判断用户是否有访问通讯录的权限
- 首先,加入框架AddressBook.framework/ AddressBookUI.framework

   - if (ABAddressBookGetAuthorizationStatus() !=kABAuthorizationStatusAuthorized)
    {
        //没有授权
    }
    else
    {   
      //已经授权
    }