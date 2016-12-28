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


