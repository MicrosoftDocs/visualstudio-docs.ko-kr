---
title: '연습: 또는 Visual Basic를 사용 C# 하 여 SDK 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558214"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>연습: C# 또는 Visual Basic을 사용하여 SDK 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 시각적 개체 C# 를 사용 하 여 간단한 수학 라이브러리 sdk를 만든 다음 SDK를 VSIX (Visual Studio Extension)로 패키징하는 방법에 대해 알아봅니다. 다음 절차를 완료 합니다.  
  
- [SimpleMath Windows 런타임 구성 요소를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [SimpleMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>사전 요구 사항  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="createClassLibrary"></a>SimpleMath Windows 런타임 구성 요소를 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**, **새 프로젝트**를 차례로 선택 합니다.  
  
2. 템플릿 목록에서 **비주얼 C#**  또는 **Visual Basic**을 확장 하 고 **Windows 스토어** 노드를 선택한 다음 **Windows 런타임 구성 요소** 템플릿을 선택 합니다.  
  
3. **이름** 상자에서 **SimpleMath**를 지정 하 고 **확인** 단추를 선택 합니다.  
  
4. **솔루션 탐색기**에서 **SimpleMath** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.  
  
5. **Class1.cs** 를 **Arithmetic.cs** 로 바꾸고 다음 코드와 일치 하도록 업데이트 합니다.  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. **솔루션 탐색기**에서 **솔루션 ' SimpleMath '** 노드에 대 한 바로 가기 메뉴를 열고 **Configuration Manager**를 선택 합니다.  
  
     **Configuration Manager** 대화 상자가 열립니다.  
  
7. **활성 솔루션 구성** 목록에서 **릴리스**를 선택 합니다.  
  
8. **구성** 열에서 **SimpleMath** row가 **Release**로 설정 되었는지 확인 한 다음 **닫기** 단추를 선택 하 여 변경 내용을 적용 합니다.  
  
    > [!IMPORTANT]
    > SimpleMath 구성 요소용 SDK에는 하나의 구성만 포함 됩니다. 이 구성은 릴리스 빌드 여야 하며, 구성 요소를 사용 하는 앱이[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]에 대 한 인증을 통과 하지 않습니다.  
  
9. **솔루션 탐색기**에서 **SimpleMath** 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **빌드**를 선택 합니다.  
  
## <a name="createVSIX"></a>SimpleMathVSIX 확장 프로젝트를 만들려면  
  
1. **솔루션 ' SimpleMath '** 노드에 대 한 바로 가기 메뉴에서 **추가**, **새 프로젝트**를 차례로 선택 합니다.  
  
2. 템플릿 목록에서 **비주얼 C#**  또는 **Visual Basic**을 확장 하 고 **확장성** 노드를 선택한 다음 **VSIX 프로젝트** 템플릿을 선택 합니다.  
  
3. **이름** 상자에서 **SimpleMathVSIX**를 지정 하 고 **확인** 단추를 선택 합니다.  
  
4. **솔루션 탐색기**에서 **source.extension.vsixmanifest** 항목을 선택 합니다.  
  
5. 메뉴 모음에서 **보기**, **코드**를 차례로 선택합니다.  
  
6. 기존 XML을 다음 XML로 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트를 선택 합니다.  
  
8. 메뉴 모음에서 **프로젝트**, **새 항목 추가**를 선택 합니다.  
  
9. **공통 항목**목록에서 **데이터**를 확장 한 다음 **XML 파일**을 선택 합니다.  
  
10. **이름** 상자에 `SDKManifest.xml`를 지정한 다음 **추가** 단추를 선택 합니다.  
  
11. **솔루션 탐색기**에서 `SDKManifest.xml`에 대 한 바로 가기 메뉴를 열고 **속성**을 선택한 다음 **VSIX에 포함** 속성의 값을 **True**로 변경 합니다.  
  
12. 파일의 내용을 다음 XML로 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 폴더**를 선택 합니다.  
  
14. 폴더 이름을 `references`로 바꿉니다.  
  
15. **참조** 폴더의 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **새 폴더**를 선택 합니다.  
  
16. 하위 폴더의 이름을 `commonconfiguration`로 바꾸고 그 안에 하위 폴더를 만든 다음 `neutral`하위 폴더의 이름을로 바꿉니다.  
  
17. 앞의 네 단계를 반복 하 여 이번에는 `redist`첫 번째 폴더의 이름을 바꿉니다.  
  
     이제 프로젝트에 다음과 같은 폴더 구조가 포함 됩니다.  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. **솔루션 탐색기**에서 **SimpleMath** 프로젝트에 대 한 바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기**를 선택 합니다.  
  
19. **파일 탐색기**에서 bin\Release 폴더로 이동 하 고 SimpleMath 파일에 대 한 바로 가기 메뉴를 연 다음 **복사**를 선택 합니다.  
  
20. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트의 references\commonconfiguration\neutral 폴더에 파일을 붙여넣습니다.  
  
21. SimpleMath 파일을 **SimpleMathVSIX** 프로젝트의 redist\commonconfiguration\neutral 폴더에 붙여넣어 이전 단계를 반복 합니다.  
  
22. **솔루션 탐색기**에서 **SimpleMath**을 선택 합니다.  
  
23. 메뉴 모음에서 **보기**, **속성** (키보드: F4 키 선택)을 선택 합니다.  
  
24. **속성** 창에서 **빌드 작업** 속성을 **내용**으로 변경한 다음 **VSIX에서 포함** 속성을 **True**로 변경 합니다.  
  
25. **솔루션 탐색기**에서 **SimpleMath**에 대해이 프로세스를 반복 합니다.  
  
26. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트를 선택 합니다.  
  
27. 메뉴 모음에서 **빌드**, **빌드 SimpleMathVSIX**를 선택 합니다.  
  
28. **솔루션 탐색기**에서 **SimpleMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기**를 선택 합니다.  
  
29. **파일 탐색기**에서 \bin\Release 폴더로 이동한 다음 SimpleMathVSIX를 실행 하 여 설치 합니다.  
  
30. **설치** 단추를 선택 하 고 설치가 완료 될 때까지 기다린 후 Visual Studio를 다시 시작 합니다.  
  
## <a name="createSample"></a>클래스 라이브러리를 사용 하는 샘플 앱을 만들려면  
  
1. 메뉴 모음에서 **파일**, **새로 만들기**, **새 프로젝트**를 차례로 선택 합니다.  
  
2. 템플릿 목록에서 **Visual C#**  또는 **Visual Basic**을 확장 한 다음 **Windows 스토어** 노드를 선택 합니다.  
  
3. 비어 있는 **앱** 템플릿을 선택 하 고 프로젝트 이름을 **ArithmeticUI**로 지정한 다음 **확인** 단추를 선택 합니다.  
  
4. **솔루션 탐색기**에서 **ArithmeticUI** 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**, **참조**를 선택 합니다.  
  
5. 참조 형식 목록에서 **Windows**를 확장 하 고 **확장**을 선택 합니다.  
  
6. 세부 정보 창에서 **간단한 수학 SDK** 확장을 선택 합니다.  
  
    SDK에 대 한 추가 정보가 표시 됩니다. 이 연습 앞부분의 Sdkmanifest.xml 파일에서 지정한 대로 **추가 정보** 링크를 선택 하 여 https://docs.microsoft.com를 열 수 있습니다.  
  
7. **참조 관리자** 대화 상자에서 **간단한 수학 SDK** 확인란을 선택 하 고 **확인** 단추를 선택 합니다.  
  
8. 메뉴 모음에서 **보기**, **개체 브라우저**를 선택 합니다.  
  
9. **찾아보기** 목록에서 **Simple Math**를 선택 합니다.  
  
     이제 SDK의 기능을 탐색할 수 있습니다.  
  
10. **솔루션 탐색기**에서 mainpage을 열고 내용을 다음 xaml로 바꿉니다.  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. MainPage.xaml.cs을 다음 코드와 일치 하도록 업데이트 합니다.  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. F5 키를 선택 하 여 앱을 실행 합니다.  
  
13. 앱에서 두 숫자를 입력 하 고 작업을 선택한 다음 **=** 단추를 선택 합니다.  
  
     올바른 결과가 나타납니다.  
  
    확장 SDK를 성공적으로 만들고 사용 했습니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 을 사용 하 C++ 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)  
 [연습: JavaScript 를 사용 하 여 SDK 만들기](walkthrough-creating-an-sdk-using-javascript.md)  
 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
