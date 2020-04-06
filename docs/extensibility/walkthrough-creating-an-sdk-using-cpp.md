---
title: '연습: C++를 사용하여 SDK 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697629"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>연습: C++를 사용하여 SDK 만들기
이 연습에서는 네이티브 C++ 수학 라이브러리 SDK를 만들고, SDK를 시각적 스튜디오 확장(VSIX)으로 패키징한 다음 앱을 만드는 방법을 보여 주며, 이를 사용하여 앱을 만듭니다. 연습은 다음 단계로 나뉩니다.

- [네이티브 및 Windows 런타임 라이브러리를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [NativeMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [클래스 라이브러리를 사용하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>네이티브 및 Windows 런타임 라이브러리를 만들려면

1. 메뉴 모음에서**새** > **프로젝트** **파일** > 을 선택합니다.

2. 템플릿 목록에서 **Visual C++** > **Windows 유니버설을**확장한 다음 **DLL(Windows 유니버설 앱)** 템플릿을 선택합니다. **이름** 상자에서 을 `NativeMath`지정한 다음 **확인** 단추를 선택합니다.

3. 다음 코드와 일치하도록 *NativeMath.h를* 업데이트합니다.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. 이 코드와 일치하도록 *NativeMath.cpp를* 업데이트하십시오.

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. **솔루션 탐색기에서** **솔루션 'NativeMath'의**바로 가기 메뉴를 열고**새 프로젝트** **추가를** > 선택합니다.

6. 템플릿 목록에서 **Visual C++를**확장한 다음 **Windows 런타임 구성 요소** 템플릿을 선택합니다. **이름** 상자에서 을 `NativeMathWRT`지정한 다음 **확인** 단추를 선택합니다.

7. 이 코드와 일치하도록 *Class1.h를* 업데이트합니다.

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. 이 코드와 일치하도록 *Class1.cpp를* 업데이트하십시오.

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>NativeMathVSIX 확장 프로젝트를 만들려면

1. **솔루션 탐색기에서** **솔루션 'NativeMath'의**바로 가기 메뉴를 열고**새 프로젝트** **추가를** > 선택합니다.

2. 템플릿 목록에서 **Visual C#** > **확장성을**확장한 다음 **VSIX 프로젝트를**선택합니다. **이름** 상자에서 **NativeMathVSIX를**지정한 다음 **확인** 단추를 선택합니다.

3. **솔루션 탐색기에서** **source.extension.vsixmanifest의**바로 가기 메뉴를 연 다음 **코드 보기를**선택합니다.

4. 다음 XML을 사용하여 기존 XML을 대체합니다.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. **솔루션 탐색기에서** **NativeMathVSIX** 프로젝트의 바로 가기 메뉴를 연 다음**새 항목** **추가를** > 선택합니다.

6. **시각적 C# 항목**목록에서 **데이터를**확장한 다음 **XML 파일을**선택합니다. **이름** 상자에서 을 `SDKManifest.xml`지정한 다음 **확인** 단추를 선택합니다.

7. 이 XML을 사용하여 파일의 내용을 바꿉꿉을 바꿀 수 있습니다.

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. **솔루션 탐색기에서** **NativeMathVSIX** 프로젝트에서 다음 폴더 구조를 만듭니다.

    ```xml
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

9. **솔루션 탐색기에서** **솔루션 'NativeMath'의**바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기를**선택합니다.

10. **파일 탐색기에서** *$SolutionRoot$\NativeMath\NativeMath.h를*복사한 다음 **솔루션 탐색기에서** **NativeMathVSIX** 프로젝트에서 *$SolutionRoot$\NativeMathVSIX\DesignTime\일반 구성\중립\폴더에\\ * 붙여넣습니다.

     *$SolutionRoot$\Debug\NativeMath\NativeMath.lib를*복사한 다음 *\\ $SolutionRoot$\NativeMathVSIX\DesignTime\debug\x86* 폴더에 붙여넣습니다.

     *$SolutionRoot$\디버그\NativeMath\NativeMath.dll을* 복사하여 *\\ $SolutionRoot$\NativeMathVSIX\Redist\Debug\x86* 폴더에 붙여넣습니다.

     *$SolutionRoot$\디버그\NativeMathWRT\NativeMathWRT.dll을* 복사하여 *$SolutionRoot$\NativeMathVSIX\Redist\Debug\x86* 폴더에 붙여넣습니다.
     *$SolutionRoot$\디버그\네이티브매스WRT\NativeMathWRT.winmd를* 복사하여 *$SolutionRoot$\NativeMathVSIX\참조\일반 구성\중립* 폴더에 붙여넣습니다.

     *$SolutionRoot$\디버그\NativeMathWRT\NativeMathWRT.pri를* 복사하여 *$SolutionRoot$\NativeMathVSIX\참조\일반 구성\중립* 폴더에 붙여넣습니다.

11. *$SolutionRoot$\NativeMathVSIX\DesignTime\Debug\x86\\ * 폴더에서 *NativeMathSDK.props라는*텍스트 파일을 만든 다음 다음 내용을 붙여 넣습니다.

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. 메뉴 모음에서**다른 Windows** > **속성 보기 창** **보기를** > 선택합니다(키보드: **F4** 키 선택).

13. **솔루션 탐색기에서** **NativeMathWRT.winmd** 파일을 선택합니다. **속성** 창에서 빌드 **작업** 속성을 **콘텐츠로**변경한 다음 **VSIX에 포함** 속성을 **True로**변경합니다.

     **NativeMath.h** 파일에 대해 이 프로세스를 반복합니다.

     **NativeMathWRT.pri** 파일에 대해 이 프로세스를 반복합니다.

     **NativeMath.Lib** 파일에 대해 이 프로세스를 반복합니다.

     **NativeMathSDK.props** 파일에 대해 이 프로세스를 반복합니다.

14. **솔루션 탐색기에서** **NativeMath.h** 파일을 선택합니다. **속성** 창에서 **VSIX에 포함** 속성을 **True로**변경합니다.

     **NativeMath.dll** 파일에 대해 이 프로세스를 반복합니다.

     **NativeMathWRT.dll** 파일에 대해 이 프로세스를 반복합니다.

     **SDKManifest.xml** 파일에 대해 이 프로세스를 반복합니다.

15. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

16. **솔루션 탐색기에서** **NativeMathVSIX** 프로젝트의 바로 가기 메뉴를 연 다음 **파일 탐색기에서 폴더 열기를**선택합니다.

17. **파일 탐색기에서** *$SolutionRoot$\NativeMathVSIX\bin\디버그* 폴더로 이동한 다음 *NativeMathVSIX.v6를* 실행하여 설치를 시작합니다.

18. **설치** 단추를 선택하고 설치가 완료될 때까지 기다린 다음 Visual Studio를 엽니다.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>클래스 라이브러리를 사용하는 샘플 앱을 만들려면

1. 메뉴 모음에서**새** > **프로젝트** **파일** > 을 선택합니다.

2. 템플릿 목록에서 **Visual C++** > **Windows 유니버설을** 확장한 다음 **빈 앱을**선택합니다. **이름** 상자에서 **NativeMathSDKSample을**지정한 다음 **확인** 단추를 선택합니다.

3. **솔루션 탐색기에서** **NativeMathSDKSample** 프로젝트의 바로 가기 메뉴를 연 다음**참조** **추가를** > 선택합니다.

4. 참조 **추가** 대화 상자에서 참조 유형 목록에서 **유니버설 Windows를**확장한 다음 **확장을 선택합니다.** 마지막으로 네이티브 **수학 SDK** 확인란을 선택한 다음 **확인** 단추를 선택합니다.

5. NativeMathSDKSample에 대한 프로젝트 속성을 표시합니다.

    *NativeMathSDK.props에서* 정의한 속성은 참조를 추가할 때 적용되었습니다. 프로젝트의 **구성**속성의 **VC++ 디렉터리** 속성을 검사하여 속성이 적용되었는지 확인할 수 있습니다.

6. **솔루션 탐색기에서** **MainPage.xaml을**연 다음 다음 XAML을 사용하여 콘텐츠를 대체합니다.

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. 이 코드와 일치하도록 *Mainpage.xaml.h를* 업데이트합니다.

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. 이 코드와 일치하도록 *MainPage.xaml.cpp를* 업데이트합니다.

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. 앱을 실행하려면 **F5** 키를 선택합니다.

10. 앱에서 두 숫자를 입력하고 작업을 선택한 다음 단추를 **=** 선택합니다.

     올바른 결과가 나타납니다.

    이 연습에서는 확장 SDK를 만들고 라이브러리와 비 [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] 라이브러리로 호출하는 방법을 보여 주어 도큐마에 이렇게 했습니다.

## <a name="next-steps"></a>다음 단계

## <a name="see-also"></a>참조
- [연습: C# 또는 시각적 기본을 사용하여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
