---
title: '연습: c + +를 사용 하 여 SDK 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202063"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>연습: C++를 사용하여 SDK 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 네이티브 c + + 수학 라이브러리 SDK를 만들고, SDK를 VSIX (Visual Studio Extension)로 패키지 한 다음,이를 사용 하 여 앱을 만드는 방법을 보여 줍니다. 이 연습은 다음 단계로 구분 됩니다.  
  
- [네이티브 및 Windows 런타임 라이브러리를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [NativeMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>사전 준비 사항  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> 네이티브 및 Windows 런타임 라이브러리를 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.  
  
2. 템플릿 목록에서 **Visual C++**, **windows 스토어**를 확장 한 다음 **DLL (windows 스토어 앱)** 템플릿을 선택 합니다. **이름** 상자에서를 지정 하 `NativeMath` 고 **확인** 단추를 선택 합니다.  
  
3. NativeMath을 다음 코드와 일치 하도록 업데이트 합니다.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. NativeMath을 다음 코드와 일치 하도록 업데이트 합니다.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. **솔루션 탐색기**에서 **' NativeMath ' 솔루션**에 대 한 바로 가기 메뉴를 열고 **추가**, **새 프로젝트**를 차례로 선택 합니다.  
  
6. 템플릿 목록에서 **Visual C++** 을 확장 한 다음 **Windows 런타임 구성 요소** 템플릿을 선택 합니다. **이름** 상자에서를 지정 하 `NativeMathWRT` 고 **확인** 단추를 선택 합니다.  
  
7. 이 코드와 일치 하도록 Class1 .h를 업데이트 합니다.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. 다음 코드와 일치 하도록 Class1 .cpp를 업데이트 합니다.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. 메뉴 모음에서 **빌드**, **솔루션 빌드**를 선택합니다.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> NativeMathVSIX 확장 프로젝트를 만들려면  
  
1. **솔루션 탐색기**에서 **' NativeMath ' 솔루션**에 대 한 바로 가기 메뉴를 열고 **추가**, **새 프로젝트**를 차례로 선택 합니다.  
  
2. 템플릿 목록에서 **Visual c #**, **확장성**을 차례로 확장 한 다음 **VSIX 패키지**를 선택 합니다. **이름** 상자에서 **NativeMathVSIX**를 지정 하 고 **확인** 단추를 선택 합니다.  
  
3. VSIX 매니페스트 디자이너가 나타나면 닫습니다.  
  
4. **솔루션 탐색기**에서 **source.extension.vsixmanifest**의 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.  
  
5. 다음 XML을 사용 하 여 기존 XML을 바꿉니다.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. **솔루션 탐색기**에서 **NativeMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**, **새 항목**을 차례로 선택 합니다.  
  
7. **Visual c # 항목**목록에서 **데이터**를 확장 한 다음 **XML 파일**을 선택 합니다. **이름** 상자에서를 지정 하 `SDKManifest.xml` 고 **확인** 단추를 선택 합니다.  
  
8. 이 XML을 사용 하 여 파일의 내용을 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. **솔루션 탐색기**의 **NativeMathVSIX** 프로젝트에서 다음 폴더 구조를 만듭니다.  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. **솔루션 탐색기**에서 **' NativeMath ' 솔루션**에 대 한 바로 가기 메뉴를 연 다음 **파일 탐색기에서 폴더 열기**를 선택 합니다.  
  
11. **파일 탐색기**에서 \NativeMath\NativeMath.h를 복사 하 고 **솔루션 탐색기** **NativeMathVSIX** 프로젝트의 \DesignTime\CommonConfiguration\Neutral\Include\ 폴더에 붙여 넣습니다.  
  
     \Debug\NativeMath\NativeMath.lib을 복사 하 여 \DesignTime\Debug\x86\ 폴더에 붙여넣습니다.  
  
     \Debug\NativeMath\NativeMath.dll을 복사 하 여 \Redist\Debug\x86\ 폴더에 붙여넣습니다.  
  
     DebugNativeMathWRTNativeMathWRT.dll을 복사 하 여 RedistDebugx86 폴더에 붙여넣습니다.  
  
     DebugNativeMathWRTNativeMathWRT을 복사 하 여 ReferencesCommonConfigurationNeutral 폴더에 붙여넣습니다.  
  
     DebugNativeMathWRTNativeMathWRT을 복사 하 여 ReferencesCommonConfigurationNeutral 폴더에 붙여넣습니다.  
  
12. \DesignTime\Debug\x86\ 폴더에서 NativeMathSDK 라는 텍스트 파일을 만들고 다음 콘텐츠를 붙여 넣습니다.  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. 메뉴 모음에서 **보기**, **다른 창**, **속성 창** 을 선택 합니다 (키보드: F4 키 선택).  
  
14. **솔루션 탐색기**에서 **NativeMathWRT** 파일을 선택 합니다. **속성** 창에서 **빌드 작업** 속성을 **내용**으로 변경한 다음 **VSIX에서 포함** 속성을 **True**로 변경 합니다.  
  
     **SimpleMath** 파일에 대해이 프로세스를 반복 합니다.  
  
     **NativeMath** 파일에 대해이 프로세스를 반복 합니다.  
  
     **NativeMathSDK** 파일에 대해이 프로세스를 반복 합니다.  
  
15. **솔루션 탐색기**에서 **NativeMath** 파일을 선택 합니다. **속성** 창에서 **VSIX에 포함** 속성을 **True**로 변경 합니다.  
  
     **NativeMath.dll** 파일에 대해이 프로세스를 반복 합니다.  
  
     **NativeMathWRT.dll** 파일에 대해이 프로세스를 반복 합니다.  
  
     **SDKManifest.xml** 파일에 대해이 프로세스를 반복 합니다.  
  
16. 메뉴 모음에서 **빌드**, **솔루션 빌드**를 선택합니다.  
  
17. **솔루션 탐색기**에서 **NativeMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기**를 선택 합니다.  
  
18. **파일 탐색기**에서 \bin\Debug\ 폴더로 이동한 다음 NativeMathVSIX를 실행 하 여 설치를 시작 합니다.  
  
19. **설치** 단추를 선택 하 고 설치가 완료 될 때까지 기다린 후 Visual Studio를 다시 시작 합니다.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> 클래스 라이브러리를 사용 하는 샘플 앱을 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트**를 차례로 선택합니다.  
  
2. 템플릿 목록에서 **Visual C++**, **Windows 스토어**를 확장 한 다음 **새 앱**을 선택 합니다. **이름** 상자에서 **NativeMathSDKSample**를 지정 하 고 **확인** 단추를 선택 합니다.  
  
3. **솔루션 탐색기**에서 **NativeMathSDKSample** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**, **참조**를 선택 합니다.  
  
4. **공용 속성**, **프레임 워크 및 참조** 속성 페이지의 참조 형식 목록에서 **Windows**를 확장 하 고 **확장**을 선택 합니다. 세부 정보 창에서 **네이티브 수학 SDK** 확장을 선택 하 고 **새 참조 추가** 단추를 선택 합니다.  
  
5. **참조 추가** 대화 상자에서 **네이티브 수학 SDK** 확인란을 선택 하 고 **확인** 단추를 선택 합니다.  
  
6. NativeMathSDKSample에 대 한 프로젝트 속성을 표시 합니다.  
  
    참조를 추가할 때 NativeMathSDK에서 정의한 속성이 적용 되었습니다. 프로젝트 **구성 속성**의 **VC + + 디렉터리** 속성을 검사 하 여이를 확인할 수 있습니다.  
  
7. **솔루션 탐색기**에서 mainpage을 열고 다음 xaml을 사용 하 여 내용을 바꿉니다.  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. 다음 코드와 일치 하도록 Mainpage을 업데이트 합니다.  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. 다음 코드와 일치 하도록 MainPage을 업데이트 합니다.  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. F5 키를 선택 하 여 앱을 실행 합니다.  
  
11. 앱에서 두 숫자를 입력 하 고 작업을 선택한 다음 단추를 선택 **=** 합니다.  
  
     올바른 결과가 나타납니다.  
  
    이 연습에서는 확장 SDK를 만들고 사용 하 여 [!INCLUDE[wrt](../includes/wrt-md.md)] 라이브러리 및 이외의 라이브러리를 호출 하는 방법을 살펴보았습니다 [!INCLUDE[wrt](../includes/wrt-md.md)] .  
  
## <a name="next-steps"></a>다음 단계  
  
## <a name="see-also"></a>관련 항목  
 [연습: c # 또는 Visual Basic를 사용 하 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
