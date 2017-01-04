###Expected App Behaviors
예상되는 어플리케이션 동작

--
Every new Xcode project comes configured to run right away in iOS Simulator or on a device.  
모든 새로운 Xcode 프로젝트는 iOS 시뮬레이터 또는 디바이스에서 즉각 실행되도록 구성됩니다.  
But simply being able to run on a device does not mean that your app is ready to ship on the App Store.  
그러나 디바이스에서 구동된다는 것이 어플리케이션이 앱스토어에 올라갈 준비가 되었다는 것을 의미하는것은 아닙니다.  
Every app requires some amount of customization to ensure a good experience for user.  
모든 어플리케이션은 좋은 유저 경험을 보장하기 위해서 약간의 맞춤 설정을 요청합니다.  
Customizations can range from providing an icon for your app to making architectural-level decisions about how your app presents and uses information.  
맞춤 설정은 어플리케이션 아이콘 제공 부터 어플리케이션의 정보 표시 및 사용 방법에 대한 아키텍쳐 레벨의 결정에 이르기까지 다양합니다.  
This chapter describes the behaviors that all apps are expected to handle and that you should consider early in the planning process.  
이 장에서는 모든 어플리케이션에서 처리해야하는 동작과 프로세스 계획 초기에 고려해야할 동작에 대해서 설명합니다.

--
###Providing the Required Resources  
필요한 자원 제공

--
Every app you create must have the following set of resources and meta data so that it can be displayed properly on iOS devices  
생성하는 모든 앱에는 iOS 기기에서 적절히 표시 될수 있도록 다음과 같은 리소스 및 메타 데이터 집합이 있어야 합니다.  

- An information property-list file. The **Info.plist** file contains metadata about your app, which the system uses to interact with your app. Xcode creates this file for you automatically based on your project's configuration and settings. If you want to view or modify the contents of this file directly, you can do so from the info tab of your project. For information about editing this file and for recommendations about what keys you should include, see [The Information Property List file. ](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW5 "The Information Property List file.")  
정보 속성리스트 파일 Info.plist 파일은 시스템이 어플리케이션과 상호작용하는데 사용하는 어플리케이션 메타데이터를 포함하고 있습니다. Xcode는 이 파일을 자동으로 프로젝트의 속성과 셋팅에 맞춰서 생성해줍니다. 만약 이 파일의 내용을 즉시 보거나 수정하기를 원한다면 프로젝트의 info 탭에서 할수 있습니다. 이파일을 수정하기를 위한 정보와 어떤 키들을 포함해야하는지 알고 싶으면 [The Information Property List file. ](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW5 "The Information Property List file.") 이 파일을 보십시오.  

- **A declaration of the app's required capabilities.** Every must declare the hardware capabilities or features that it requires to run. The App Store uses this information to determine whether or not a user can run your app on a specific device. You can edit your app's list of requirements using the Required device capabilities entry in the Info tab of your project. For information on how to configure this key, see [Declaring the Required Device Capabilities.](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW4)  
**어플리케이션 필수 기능을 선언합니다.** 실행에 필요한 모든 하드웨어 능력또는 특성을 정의해야합니다. 앱 스토어는 유저의 디바이스에서 실행될수 있는지 아닌지를 이 정보를 통해서 결정합니다. 어플리케이션의 요구 사항 목록을 프로젝트 맨 앞 Info 탭에서 필수 장치 기능 항목을 사용하여 수정할수 있습니다. 어떻게 키를 설정할수 있는지에 대한 정보를 보려면 [필요한 장치 기능 선언](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW4)을 보십시오.

- **One or more icons.** The system displays your app icon on the home screen of a user's device. The system many also use other versions of your icon in the Settings app or when displaying the results of a search. For information about how to specify app icons, see [App icons](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW1).   
**하나 이상의 아이콘들.** 시스템은 어플리케이션 아이콘을 유저의 디바이스 홈스크린에 표시합니다. 또한 시스템은 다른 버전의 아이콘을 셋팅 앱이나 검색 결과를 표시할때 사용합니다. 어떻게 앱 아이콘을 명시하는지 정보를 얻으려면 [App icons](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW1) 를 보십시오.

- **One or more launch images.** When an app is launched, the system displays a temporary image until the app is able to present its user interface. This temporary image is your app's launch image and it provides the user with immediate feedback that your app is launching and it provides the user with immediate feedback that your app is launching and will be ready soon. You must provide at least one luach image for your app and you may provide additional launch images to address specific scenarios. For information about creating your launch images, see [App Launch (Default) Images](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW3).    
**하나 이상의 실행 이미지.** 어플리케이션이 실행될때 시스템은 어플리케이션이 유저 인터페이스를 표시할때까지 임시의 이미지를 보여줍니다. 이 임시의 이미지는 어플리케이션의 시작이미지이며 유저에게 어플리케이션이 곧 실행된다는 피드백을 제공합니다. 당신은 어플리케이션을 위해서 최소한 하나의 시작 이미지를 제공해야하고 특정 시나리오를 위하여 추가로 이미지를 제공해야 할수도 있습니다. 시작 이미지 제작에 대한 정보를 얻으려면 [App Launch (Default) Images](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW3)를 보십시오.

The resources are required for all apps but are not the only ones you should include.  
리소스들은 모든 어플리케이션에 필요하지만 포함 시켜야하는 것은 아닙니다.  
There are many keys that Xcode does not include in your app's **Info.plist** file by default.  
Xcode가 기본으로 **Info.plist** 파일에 포함하지 않는 많은 키들이 있습니다.  
Most of the additional keys are important only if you incorporate specific features into your app.  
대부분의 추가적인 키들은 어플리케이션에 명확한 기능을 포함해야할 경우에만 중요합니다.  
For example, an app that uses the microphone should include the **NSMicrophoneUsageDescription** key and provide the user with information about how the app intends to use it.  
예를 들어 어플리케이션이 마이크를 사용해야한다면 **NSMicrophoneUsageDescription** 키를 포함시켜야하고 유저에게 어떤 의도로 이 기능을 사용하는지 정보를 제공해야 합니다.

--

###The App Bundle
어플리케이션 번들

When you build your iOS app, Xcode packages it as a bundle.  
iOS 어플리케이션을 빌드 할 때 Xcode는 그것을 번들로 묶습니다.  
A bundle is a directory in the file system that groups related resources together in one place.  
번들은 관련된 리소스를 한 곳에서 그룹화 하는 파일 시스템 디렉토리입니다.   
An iOS app bundle contains the app executable file and supporting resource files such as app icons, image file, and localized content.    
iOS 어플리케이션 번들은 어플리케이션 실행 파일과 어플리케이션 아이콘, 이미지 파일 그리고 현지화 된 콘텐츠 같은 서포트 리소스를 포함합니다.  
Table 1-1 lists the content of a typical iOS app bundle, which for demonstration purposes is called *MyApp*.  
*MyApp* 이라고 불리는 데모 버전으로 일반적인 iOS 어플리케이션 번들 내용을 표 1-1 리스트를 통해 보여줍니다.  
This example is for illustrative purposes only.  
이 예제는 설명을 위한 것입니다.  
Some of the files listed in this table may not appear in your own app bundles.  
테이블 리스트에 있는 일부의 파일들은 아마도 당신의 어플리케이션 번들에는 나타나지 않을것입니다.

**Table 1-1** A typical app bundle  
**테이블1-1** 일반적인 어플리케이션 번들

파일 | 예제 | 설명
-----| ------- | -------
App executable | MyApp | 실행 파일은 어플리케이션 컴파일 코드를 포함하고 있습니다. 어플리케이션 실행 파일의 이름은 어플리케이션 이름에서 *.app* 확장자를 뺀 것과 같습니다. 이 파일은 필수입니다.
The information property list file    | Info.plist | **Info.plist** 파일은 어플리케이션의 환경 설정 데이터를 포함하고 있습니다. 시스템은 이 데이터를 어떻게 어플리케이션과 상호작용 하는지를 결정하는데 사용합니다. 이 파일은 필수이며 **Info.plist** 라고 명명 되어야 합니다. 정보를 더 얻고 싶으면 [The Information Property List File](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW5)을 보십시오.
| App icons | Icon.png  Icon@2x.png  Icon-Small.png  Icon-Small@2x.png | 어플리케이션 아이콘은 디바이스 홈 스크린에 어플리케이션을 나타내는 데 사용됩니다. 다른 아이콘들은 시스템에 의해서 적절한 곳에 사용됩니다. 파일 이름에 **@2x** 붙은 아이콘들은 레티나 디스플레이 디바이스에 사용됩니다. 어플리케이션 아이콘은 필수 항목입니다. 아이콘 이미지 파일에 대한 자세한 정보를 얻고 싶으면 [App Icons](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW1)를 보십시오.
|Launch images | Default.png  Default-Portrait.png  Default-Landscape.png | 시스템은 이 파일을 어플리케이션이 실행 되는 도중 임시 배경화면으로 사용합니다. 이것은 어플리케이션이 유저 인터페이스를 보여줄 준비가 되면 곧 사라집니다. 최소한 하나의 실행 이미지가 필수적으로 있어야합니다. 실행 이미지에 대한 자세한 정보를 얻으려면 [App Launch(Default) Images](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW3) 를 보십시오.
|Storyboard files(or nib files) | MainBoard.storyboard | 스토리보드는 어플리케이션이 스크린에 보여주는 뷰와 뷰 컨트롤러를 포함하고 있습니다. 스토리보드 안에 있는 뷰는 뷰 컨트롤러에 따라서 조직화 되어있습니다. 스토리보드는 또한 다른 뷰로 사용자를 전환 시키는 세그라고 불리는 전환을 식별합니다.   메인 스토리보드 파일 이름은 프로젝트를 만들 때 Xcode가 설정합니다. *UIMainStoryboardFile* key에 다른 값을 할당하여 *Info.plist* 파일에서 메인 스토리보드 파일이름을 수정할수 있습니다. 스토리보드대신에 **nib files**를 사용하는 어플리케이션들은 *UIMainStoryboardFile* key를 *NSMainNibFile* key로 대체하여 메인 nib 파일의 키를 수정할 수 있습니다. 스토리보드 (또는 nib 파일)을 사용하는 것은 선택이지만 권장됩니다.
| Ad hoc distribution icon | iTunesArtwork | 만약 어플리케이션을 임시로 배포하려면 512 x 512 픽셀의 아이콘을 포함해야합니다. 이 아이콘은 일반적으로 iTunes Connect를 통해 App store에 제공하는 자료입니다. 그러나 만약 어플리케이션 임시 배포는 App store를 통하지 않기 때문에, 아이콘은 꼭 app bundle에 있어야 합니다. iTunes는 이 아이콘을 어플리케이션을 보여주는데 사용합니다.(만약 이 방법으로 어플리케이션을 배포하려면 이 파일은 App Store에 제출한 것과 같아야합니다.)  이 아이콘의 파일 이름은 반드시 *iTunesArtwork* 이여야 하고 반드시 확장자가 없어야합니다. 이 파일은 임시 배포에 필요하지만 임시 배포가 아니라면 필수는 아닙니다.
|Settings bundle | Settings.bundle | 만약 어플리케이션 속성을 설정 어플리케이션을 통하여 보여주고 싶은 경우에는 반드시 settings bundle 을 포함시켜야 합니다. 이 번들은 *property list* 데이터와 어플리케이션 속성을 정의하는 기타 리소스를 포함하고 있습니다. 설정 어플리케이션은 이 번들 안에 있는 정보를 사용하여 어플리케이션에 필요한 인터페이스 요소를 조합합니다.   이 번들은 선택적입니다. 설정과 settings bundle 지정에 대한 더 많은 정보를 얻으려면 *[Preferences and Settings Programming Guide](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/UserDefaults/Introduction/Introduction.html#//apple_ref/doc/uid/10000059i)* 를 보십시오.
| Nolocalized resource files | sun.png    mydata.plist | 현지화 되지 않는 리소스들은 이미지, 사운드 파일, 영상, 그리고 어플리케이션에서 사용하는 커스텀 데이터 파일을 포함합니다. 이 파일들 모두는 app bundle 의 최상위에 위치해야합니다.
| Subdirectories for localized resources | en.lproj  fr.lproj  es.lproj  | 현지화된 리소스 파일은 ISO 639-1 언어 약어와 *.lproj* 접미사가 붙어 구성 되어야 하고 언어별 프로젝트 폴더에 위치해야합니다. (예를들어 *en.lproj*, *fr.lproj*, 그리고 *es.lproj* 폴더들은 각각 영어, 프랑스어, 스페인어로 현지화된 리소스가 있어야합니다.)  iOS 어플리케이션은 국제화 되어야 하며 하며 각각의 *language.lproj* 디렉토리는 각각의 언어를 지원합니다. 어플리케이션의 현지화된 커스텀 리소스를 제공하는것 외에도 어플리케이션 아이콘, 시작 이미지, 셋팅 아이콘을 언어별 프로젝트 디렉토리에 같은 이름으로 위치하는 것으로 현지화해서 제공할수 있습니다. 더 많은 정보를 원하면 [Internationalizing Your App](https://developer.apple.com/library/content/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/ExpectedAppBehaviors/ExpectedAppBehaviors.html#//apple_ref/doc/uid/TP40007072-CH3-SW10) 을 보십시오.
  

For more information about the structure of an iOS app bundle, see [Bundle Programming Guide](https://developer.apple.com/library/content/documentation/CoreFoundation/Conceptual/CFBundles/Introduction/Introduction.html#//apple_ref/doc/uid/10000123i).
iOS app bundle 구조에 대해 더 많은 정보를 얻으려면 [Bundle Programming Guide](https://developer.apple.com/library/content/documentation/CoreFoundation/Conceptual/CFBundles/Introduction/Introduction.html#//apple_ref/doc/uid/10000123i) 를 보십시오. 어떻게 번들에 있는 리소스 파일들을 로드 하는지에 대한 정보를 얻으려면 [Resource Programming Guide](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/LoadingResources/Introduction/Introduction.html#//apple_ref/doc/uid/10000051i) 를 보십시오.

 














	
	