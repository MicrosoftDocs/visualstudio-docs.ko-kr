---
title: '연습: c + +를 사용 하 여 SDK 만들기 | Microsoft Docs'
description: 네이티브 c + + 수학 라이브러리 sdk를 만들고, sdk를 Visual Studio 확장으로 패키지 하 고,이 연습을 사용 하 여 앱을 만드는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a52322e575dc201a6bf1648af93d813828e0b17
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113223009"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>연습: c + +를 사용 하 여 SDK 만들기
이 연습에서는 네이티브 c + + 수학 라이브러리 sdk를 만들고, sdk를 VSIX (Visual Studio Extension)로 패키지 한 다음,이를 사용 하 여 앱을 만드는 방법을 보여 줍니다. 이 연습은 다음 단계로 구분 됩니다.

- [네이티브 및 Windows 런타임 라이브러리를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [NativeMathVSIX 확장 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [클래스 라이브러리를 사용 하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>필수 조건
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>네이티브 및 Windows 런타임 라이브러리를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

2. 템플릿 목록에서 **Visual C++**  >  **Windows 유니버설** 를 확장 한 다음 **DLL (Windows 유니버설 앱)** 템플릿을 선택 합니다. **이름** 상자에서를 지정 하 `NativeMath` 고 **확인** 단추를 선택 합니다.

3. NativeMath을 다음 코드와 일치 하도록 업데이트 *합니다* .

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. NativeMath을 다음 코드와 일치 하도록 업데이트 *합니다* .

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. **솔루션 탐색기** 에서 **' NativeMath ' 솔루션** 에 대 한 바로 가기 메뉴를 열고   >  **새 Project** 추가를 선택 합니다.

6. 템플릿 목록에서 **Visual C++** 을 확장 한 다음 **Windows 런타임 구성 요소** 템플릿을 선택 합니다. **이름** 상자에서를 지정 하 `NativeMathWRT` 고 **확인** 단추를 선택 합니다.

7. 이 코드와 일치 하도록 *Class1 .h* 를 업데이트 합니다.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. 다음 코드와 일치 하도록 *Class1 .cpp* 를 업데이트 합니다.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> NativeMathVSIX 확장 프로젝트를 만들려면

1. **솔루션 탐색기** 에서 **' NativeMath ' 솔루션** 에 대 한 바로 가기 메뉴를 열고   >  **새 Project** 추가를 선택 합니다.

2. 템플릿 목록에서 **Visual c #**  >  **확장성** 을 확장 한 다음 **VSIX Project** 를 선택 합니다. **이름** 상자에서 **NativeMathVSIX** 를 지정 하 고 **확인** 단추를 선택 합니다.

3. **솔루션 탐색기** 에서 **source.extension.vsixmanifest** 의 바로 가기 메뉴를 열고 **코드 보기** 를 선택 합니다.

4. 다음 XML을 사용 하 여 기존 XML을 바꿉니다.

    ```xml
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="NativeMathVSIX..c6b3cae1-e7e2-4e71-90f6-21017ea0dff7" Version="1.0" Language="en-US" Publisher="MyName" />
        <DisplayName>Native Math SDK</DisplayName>
        <Description>Native Math Library w/ Windows Runtime Additions</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="NativeMathSDK" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

5. **솔루션 탐색기** 에서 **NativeMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고   >  **새 항목** 추가를 선택 합니다.

6. **Visual c # 항목** 목록에서 **데이터** 를 확장 한 다음 **XML 파일** 을 선택 합니다. **이름** 상자에서를 지정 하 `SDKManifest.xml` 고 **확인** 단추를 선택 합니다.

7. 이 XML을 사용 하 여 파일의 내용을 바꿉니다.

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. **솔루션 탐색기** **NativeMathVSIX** 프로젝트 아래에서 다음 폴더 구조를 만듭니다.

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

9. **솔루션 탐색기** 에서 **' NativeMath ' 솔루션** 에 대 한 바로 가기 메뉴를 연 다음 **파일 탐색기에서 폴더 열기** 를 선택 합니다.

10. **파일 탐색기** 에서 *$ \NativeMath\NativeMath.h를 $SolutionRoot* 복사한 다음, **솔루션 탐색기** 의 **NativeMathVSIX** 프로젝트 아래에서이 파일을 *\\ $SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include* 폴더에 붙여 넣습니다.

     *$ \Debug\NativeMath\NativeMath.lib $SolutionRoot* 복사한 후 *\\ $SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86* 폴더에 붙여넣습니다.

     *$\Debug\NativeMath\NativeMath.dll$SolutionRoot* 복사 하 고 *\\ $SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* 폴더에 붙여넣습니다.

     *$\Debug\NativeMathWRT\NativeMathWRT.dll$SolutionRoot* 복사 하 고 *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* 폴더에 붙여넣습니다.
     *$ \Debug\NativeMathWRT\NativeMathWRT.winmd $SolutionRoot* 복사 하 고 *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* 폴더에 붙여넣습니다.

     *$ \Debug\NativeMathWRT\NativeMathWRT.pri $SolutionRoot* 복사 하 고 *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* 폴더에 붙여넣습니다.

11. *$SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86 \\* 폴더에서 *NativeMathSDK* 라는 텍스트 파일을 만든 후 다음 내용을 붙여넣습니다.
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. 메뉴 모음에서   >  **기타 Windows**  >  **속성 창** 보기 (키보드: **F4** 키 선택)를 선택 합니다.

13. **솔루션 탐색기** 에서 **NativeMathWRT** 파일을 선택 합니다. **속성** 창에서 **빌드 작업** 속성을 **내용** 으로 변경한 다음 **VSIX에서 포함** 속성을 **True** 로 변경 합니다.

     **NativeMath** 파일에 대해이 프로세스를 반복 합니다.

     **NativeMathWRT** 파일에 대해이 프로세스를 반복 합니다.

     **NativeMath** 파일에 대해이 프로세스를 반복 합니다.

     **NativeMathSDK** 파일에 대해이 프로세스를 반복 합니다.

14. **솔루션 탐색기** 에서 **NativeMath** 파일을 선택 합니다. **속성** 창에서 **VSIX에 포함** 속성을 **True** 로 변경 합니다.

     **NativeMath.dll** 파일에 대해이 프로세스를 반복 합니다.

     **NativeMathWRT.dll** 파일에 대해이 프로세스를 반복 합니다.

     **SDKManifest.xml** 파일에 대해이 프로세스를 반복 합니다.

15. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다.

16. **솔루션 탐색기** 에서 **NativeMathVSIX** 프로젝트에 대 한 바로 가기 메뉴를 열고 **파일 탐색기에서 폴더 열기** 를 선택 합니다.

17. **파일 탐색기** 에서 *$SolutionRoot $ \NativeMathVSIX\bin\Debug* 폴더로 이동한 다음 *NativeMathVSIX* 를 실행 하 여 설치를 시작 합니다.

18. **설치** 단추를 선택 하 고 설치가 완료 될 때까지 기다린 후 Visual Studio를 엽니다.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> 클래스 라이브러리를 사용 하는 샘플 앱을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

2. 템플릿 목록에서 **Visual C++**  >  **Windows 유니버설** 을 확장 한 다음 **새 앱** 을 선택 합니다. **이름** 상자에서 **NativeMathSDKSample** 를 지정 하 고 **확인** 단추를 선택 합니다.

3. **솔루션 탐색기** 에서 **NativeMathSDKSample** 프로젝트에 대 한 바로 가기 메뉴를 열고 참조 **추가** 를 선택  >  합니다.

4. **참조 추가** 대화 상자의 참조 형식 목록에서 **Universal Windows** 를 확장 하 고 **확장** 을 선택 합니다. 마지막으로 **네이티브 수학 SDK** 확인란을 선택 하 고 **확인** 단추를 선택 합니다.

5. NativeMathSDKSample에 대 한 프로젝트 속성을 표시 합니다.

    참조를 추가할 때 *NativeMathSDK* 에서 정의한 속성이 적용 되었습니다. 프로젝트 **구성 속성** 의 **VC++ directory** 속성을 검사 하 여 속성이 적용 되었는지 확인할 수 있습니다.

6. **솔루션 탐색기** 에서 **mainpage** 을 열고 다음 xaml을 사용 하 여 내용을 바꿉니다.

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. 다음 코드와 일치 하도록 *mainpage* 을 업데이트 합니다.

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. 다음 코드와 일치 하도록 *mainpage* 을 업데이트 합니다.

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. **F5** 키를 선택 하 여 앱을 실행 합니다.

10. 앱에서 두 숫자를 입력 하 고 작업을 선택한 다음 단추를 선택 **=** 합니다.

     올바른 결과가 나타납니다.

    이 연습에서는 확장 SDK를 만들고 사용 하 여 [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] 라이브러리 및 이외의 라이브러리를 호출 하는 방법을 살펴보았습니다 [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] .

## <a name="next-steps"></a>다음 단계

## <a name="see-also"></a>참고 항목
- [연습: c # 또는 Visual Basic를 사용 하 여 SDK 만들기](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
