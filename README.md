# Cordova Plugin For QQ SDK
[![version](https://img.shields.io/badge/version-0.4.0-blue.svg?style=flat)](https://github.com/borisavilov/cordova-plugin-QQ)
[![platform](https://img.shields.io/badge/platform-iOS%2FAndroid-lightgrey.svg?style=flat)](https://github.com/borisavilov/cordova-plugin-QQ)
[![GitHub license](https://img.shields.io/github/license/mashape/apistatus.svg?style=flat)](https://github.com/borisavilov/cordova-plugin-QQ/blob/master/LICENSE)

This is a Cordova Plugin for QQ SDK .
## Feature
1. QQ SSO Login
2. QQ Logout 
3. QQ Share 
4. QZone Share
5. QQ Favorites
6. checkClientInstalled		

## Requirements
- Cordova Version 3.5+ 
- Cordova-Android >=4.0
- Cordova-iOS >=4.0			

##Installation
1. ```cordova plugin add https://github.com/borisavilov/cordova-plugin-QQ.git --variable QQ_APP_ID=YOUR_QQ_APPID``` 
2. cordova build --device          			

##Notes			     		
1. This plugin is required cordova-android version >=4.0,so using cordova  5.0.0 or higher is recommended
2. This plugin should be used after the deviceready event has been fired!!!				
						

##Usage                								
					     
### QQ SSO Login
```Javascript
var checkClientIsInstalled = 1;//default is 0,only for iOS
YCQQ.ssoLogin(function(args){
      alert("token is " + args.access_token);
      alert("userid is " +args.userid);
      alert("expires_time is "+ new Date(parseInt(args.expires_time)) + " TimeStamp is " +args.expires_time);
      },function(failReason){
       console.log(failReason);
},checkClientIsInstalled);
```
### QQ Logout
```Javascript
YCQQ.logout(function(){
	console.log('logout success');
},function(failReason){
	console.log(failReason);
});
```
### QQ Share
```Javascript
var args = {};
args.url = "";
args.title = "";
args.description = "";
args.imageUrl = "";
args.appName = "";
YCQQ.shareToQQ(function(){
	console.log("share success");
},function(failReason){
	console.log(failReason);
},args);
```
### QZone Share
```Javascript
 var args = {};
 args.url = "http://www.baidu.com";
 args.title = "This is cordova QZone share ";
 args.description = "This is cordova QZone share ";
 var imgs =['https://www.baidu.com/img/bdlogo.png',
 'https://www.baidu.com/img/bdlogo.png',
 'https://www.baidu.com/img/bdlogo.png'];
  args.imageUrl = imgs;
  YCQQ.shareToQzone(function () {
      alert("share success");
  }, function (failReason) {
      alert(failReason);
  }, args);
```
###QQ Favorites
```Javascript
 var args = {};
 args.url = "http://www.baidu.com";
 args.title = "这个是cordova QQ 收藏测试";
 args.description = "这个是cordova QQ 收藏测试";
 args.imageUrl = "https://www.baidu.com/img/bdlogo.png";
 args.appName = "cordova—QQ";
 YCQQ.addToQQFavorites(function () {
   alert("share success");
 }, function (failReason) {
   alert(failReason);
 }, args);
```
### CheckClientInstalled
```Javascript
YCQQ.checkClientInstalled(function(){
	 console.log('client is installed');
},function(){
	// if installed QQ Client version is not supported sso,also will get this error
	console.log('client is not installed');
});
```
						
##ERROR_CODE					
When you use qq login,you may get an error code.If you get one, find detail error msg from [here](http://wiki.open.qq.com/wiki/mobile/API%E8%B0%83%E7%94%A8%E8%AF%B4%E6%98%8E#6._.E8.BF.94.E5.9B.9E.E7.A0.81.E8.AF.B4.E6.98.8E%E3%80%82) please.



