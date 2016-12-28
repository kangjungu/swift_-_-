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
- 이 문서는 앱이 iOS에서 잘 동작하는것에 핵심동작에 초점을 맞추고 있습니다..

You might not implement every feature described in this document but you should consider these features for every project you create.  
- 이 문서에서 묘사하는 모든 특성을 구현할 필요는 없을테지만 이 특성들을 매 프로젝트를 만들때 고려해야합니다.

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
- 아이디어를 앱으로 구현할 준비가 되면  앱과 시스템 사이 상호작용이 일어나는 부분을 이해해야 합니다.  

--  
###Apps Are Expected To Support Key Features  
-앱은 주요 기능을 지원할 것으로 예상됩니다.  

--



