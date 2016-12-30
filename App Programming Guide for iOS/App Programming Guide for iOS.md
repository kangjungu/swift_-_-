##Introduction  

###About  iOS App Architecture  
-iOS 아키텍쳐에 관하여

--
Apps need to work with the iOS to ensure that they deliver a great user experience.

-App은 좋은 사용자 경험을 제공하기 위해 iOS와 협력해야합니다.

Beyond just a good design for your app's design and user interface, a great user experience encompasses many other factors.  
-단순한 좋은 디자인을 넘어서는 앱 디자인과 유저 인터페이스에 대해, 뛰어난 사용자 경험은 많은 다른 요인들을 포함합니다.  

Users expect iOS apps to be fast and responsive while expecting the app to use little power as possible  
-유저들은 iOS앱에 가능한 적은 파워를 사용하고, 빠른 속도로 반응하길 기대합니다.

Apps need to support all of the latest iOS devices while still appearing as if the app was tailored for the current device.  
-App은 모든 최신 iOS 기기를 지원하는것을 필요로 하지만, 여전히 마치 앱이 현재 기기들에 딱 맞춘것 같이 만들어야합니다.

Implementing all of these behaviors can seem daunting at first but iOS provides the help you need to make it happen.  
-이 모든 동작들을 구현하는것은 힘든것 처럼 보일수 있지만 iOS는 이것들을 만들수 있게 도움을 제공합니다.

This document highlights the core behaviors that make your app work well on iOS.  
-이 문서는 앱이 iOS에서 잘 동작하는것에 핵심동작에 초점을 맞추고 있습니다..

You might not implement every feature described in this document but you should consider these features for every project you create.  
-이 문서에서 묘사하는 모든 특성을 구현할 필요는 없을테지만 이 특성들을 매 프로젝트를 만들때 고려해야합니다.

````
Note : Development of iOS apps requires an Intel-based Macintosh computer with the iOS SDK installed. 
-iOS 앱을 개발하려면 인텔 베이스 매킨토시 컴퓨터와 iOS SDK 설치가 필요합니다. 
For information about how to get the iOS SDK, go th the iOS Dev Center
-어떻게 iOS SDK를 설치하는지에 대해 설명이 필요하면 iOS Dev Center (https://developer.apple.com/devcenter/ios/)로 가보세요. 
````
--

###At a Glance  
-요약

--
When you are ready to take your ideas and turn them into an app, you need to understand the interactions that occur between the system and your app.  
-아이디어를 앱으로 구현할 준비가 되면  앱과 시스템 사이 상호작용이 일어나는 부분을 이해해야 합니다.  

--  
###Apps Are Expected To Support Key Features  
-앱이 지원하기를 기대하는 기능 

--
The system expects every app to have some specific resources and configuration data, such as an app icon and information about the capabilities of the app.    
-시스템은 명확한 리소스와앱 아이콘과 앱의 기능 같은 환경 설정 데이터를 모든 앱이 가지길 원합니다.  
Xcode provides some information with every new project but you must supply resource files and you must make sure the information in your project is correct before submitting your app.  
-Xcode는 모든 새로운 프로젝트에 약간의 정보를 제공합지만 리소스 파일을 제공해야하며 프로젝트 정보가 맞는지 앱을 제출하기전에 확인해야 합니다.

--  
###Apps Follow Well-Defined Execution Paths  
-앱은 명확한 실행 흐름을 따릅니다.

--
From the time the user launches an app to the time it quits, apps follow a well-defined execution path.  
-유저가 앱을 실행하고 종료할때 까지 앱은 명확한 실행 흐름을 따릅니다.  
During the life of an app, it can transition between foreground and background execution, it can be terminated an relaunched, and it can go to sleep temporarily.  
-앱이 살아있는 동안 앱은 포그라운드와 백그라운드에서 실행될수 있고 또한 앱은 다시 시작될수 있으며 일시적으로 슬립 상태에 있을수도 있습니다.  
Each time it transitions to a new state, the expectations for the app change.  
-새로운 상태로 변화할 때마다 앱에 대한 기대치가 바뀝니다.
A foreground app can do almost anything but background apps must do as little as possible.    
-포그라운드 앱은 거의 모든것을 할수 있습니다. 하지만 백그라운드 앱은 가능한 한 적은 것을 해야합니다.  
You use the state transitions to adjust your app's behaviors accordingly.  
-상태전환을 사용하여 앱의 동작을 적절하게 조정해야합니다.

--
###Apps Must Run Efficiently in a Multitasking Environment  
-앱은 멀티태스킹 환경에서 효율적으로 실행되어야합니다.  

--  
Battery life is important for users, as is performance, responsiveness, and a great user experience.  
-배터리 라이프는 퍼포먼스와 반응성과 뛰어난 사용자 경험 만큼 사용자 에게 중요합니다.  
Minimizing your app's usage of the battery ensures that user can your app all day without having to recharge the device, but launching and being ready to run quickly are also important.  
-유저가 앱을 하루종일 디바이스 충전없이 사용할수 있게 앱의 배터리 사용량의 최소화를 보장해야합니다. 그러나 실행은 빠르게 하는것 또한 중요합니다.  
The iOS multitasking implementation offers good battery life without sacrificing the responsiveness and user experience that users expect, but the implementation requires apps to adopt system-provided behaviors.  
-iOS 멀티 테스팅 구현은 사용자가 기대하는 사용자 경험과 반응성의 희생없이 좋은 배터리 라이프를 제공합니다. 그러나 구현은 앱은 시스템이 제공하는 동작으로 해야합니다.

--
###Communication Between Apps Follows Specific Pathways  
-어플리케이션간의 통신을 특별한 경로를 따릅니다.

--
For security, iOS apps run in a sandbox and have limited interactions with other apps.  
-보안을 위해서 iOS 어플리케이션은 샌드박스 안에서 실행이 되고 다른 어플리케이션과의 상호작용은 제한됩니다.
When you want to communicate with other apps on the system, there are specific ways to do so.   
-시스템 위의 다른 어플리케이션과 상호작용을 하기 윈한다면, 특정한 방법이 있습니다.

--
###Performance Tuning is Important for Apps  
-퍼보먼스 조율은 앱에서 중요합니다.

--
Every task perfomed by an app has a power cost associated with it.  
-앱이 수행되는 모든 일은 이것과 연관된 전력 비용이 있습니다.  
Apps that drain the user's battery create a negative user experience and are more likely to be deleted than those that to run for days on a single charge.  
-유저 배터리를 소모하는 앱은 부정적인 유저 경험을 만들고 한번 충전후 여러 날동안 실행되는 어플리케이션보다  삭제 가능성이 큽니다.  
So be aware of the cost of different operation and take advantage of power-saving measures offered by the system.  
-따라서 다른 작업의 비용을 인식하고 시스템에서 제공하는 절전 방법을 이용하십시오.

--
###How to Use This Document  
-문서 사용 방법

--
This document is not beginner's guide to creating iOS apps.  
-이 문서는 iOS 앱을 만들기 위한 초보자 가이드가 아닙니다.  
It is for developers who are ready to polish their app before putting it in the App Store.  
-이것은 앱스토어에 앱을 올리기 전에 앱을 다룰 준비가 된 개발자들을 위한것입니다.  
Use this document as a guide to understanding how your app interacts with the system and what is must do to make those interactions happen smoothly.  
-어떻게 어플리케이션과 시스템이 상호작용하는지 이해하기 위해서 또는 상호작용이 원활하게 이루어지도록 하기 위해 꼭 해야할 작업을 알고 싶을때는 이 문서를 사용하세요.

--
###Prerequisites  
-전제조건 

--
This document provides detailed information about iOS app architecture and shows you how to implement many app-level features.  
-이 문서는 iOS app 아키텍쳐에 대해서 자세한 정보를 제공하고 다양한 어플리케이션-레벨 기능을 구현할수 있는지 보여줍니다.  
This book assumes that you have already installed the iOS SDK, configured your development environment, and understand the basics of creating and implementing an app in Xcode.  
-이 책은 당신이 이미 iOS SDK를 설치했고 어플리케이션 개발 환경을 설정하였고 Xcode에서 어플리케이션 기본 생성 및 구현을 이해하고있다고 가정합니다. 
  
If you are new iOS app development, read [Start Developing iOS Apps (swift)](https://developer.apple.com/library/content/referencelibrary/GettingStarted/DevelopiOSAppsSwift/index.html#//apple_ref/doc/uid/TP40015214 "swift").  
-만약 당신이 새로운 iOS 앱 개발자라면 [Start Developing iOS Apps (swift)](https://developer.apple.com/library/content/referencelibrary/GettingStarted/DevelopiOSAppsSwift/index.html#//apple_ref/doc/uid/TP40015214 "swift") 이 링크를 읽어보세요.  
That document offers a step-by-step introduction to the development process to help you get up to speed quickly.  
-이 문서는 당신이 빠르게 처리할 수 있게 개발 과정을 단계별로 소개를  제공합니다.  
It also includes a hands-on tutorial that walks you through the app-creation process from start to finish, showing you how to create a simple app and get it running quickly.  
-또한 어플리케이션의 시작부터 끝까지의 프로세스를 안내하는 실습 자습서가 포함되어 간단한 앱을 빠르게 실행 하는 방법을 보여줍니다.

--
###See Also  
-또한 볼 것 
 
--
If you are learning about iOS, read [iOS Technology OverView](https://developer.apple.com/library/content/documentation/Miscellaneous/Conceptual/iPhoneOSTechOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007898 "Technology OverView") to learn about the technologies and feautres you can incorporate into your iOS apps.  
-만약 당신이 iOS에 대하여 배우고 있다면 [Technology OverView](https://developer.apple.com/library/content/documentation/Miscellaneous/Conceptual/iPhoneOSTechOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40007898 "Technology OverView")을 읽어 iOS 앱에 대해 통합 할 수 있는 기술과 기능에 대해서 배워보세요.


