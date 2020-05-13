---
title: 레거시 언어 서비스 마이그레이션 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707103"
---
# <a name="migrating-a-legacy-language-service"></a>레거시 언어 서비스 마이그레이션
프로젝트를 업데이트하고 프로젝트에 source.extension.vsixmanifest 파일을 추가하여 레거시 언어 서비스를 이후 버전의 Visual Studio로 마이그레이션할 수 있습니다. Visual Studio 편집기는 언어 서비스 편집기를 적용하기 때문에 언어 서비스 자체는 이전과 같이 계속 작동합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 언어 서비스를 구현하는 새로운 방법에 대한 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/editor-and-language-service-extensions.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Visual Studio 2008 언어 서비스 솔루션을 이후 버전으로 마이그레이션
 다음 단계에서는 RegExLanguageService라는 Visual Studio 2008 샘플을 적용하는 방법을 보여 준다. 이 샘플은 Visual Studio SDK 설치 경로 \VisualStudioIntegration\샘플\IDE\CSharp\Example.RegExLanguageService\ 폴더의 Visual Studio 2008 *SDK 설치에서*찾을 수 있습니다.

> [!IMPORTANT]
> 언어 서비스가 색상을 정의하지 않는 경우 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> VSPackage에서 `true` 명시적으로 설정해야 합니다.

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Visual Studio 2008 언어 서비스를 이후 버전으로 마이그레이션하려면

1. 최신 버전의 Visual Studio 및 Visual Studio SDK를 설치합니다. SDK를 설치하는 방법에 대한 자세한 내용은 [Visual Studio SDK 설치를](../../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

2. RegExLangServ.csproj 파일을 편집합니다(비주얼 스튜디오에서 로드하지 않고)

     Microsoft.VsSDK.targets 파일을 참조하는 `Import` 노드에서 값을 다음 텍스트로 바꿉습니다.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. 파일을 저장한 다음 닫습니다.

4. RegExLangServ.sln 솔루션을 엽니다.

5. **단방향 업그레이드** 창이 나타납니다. **확인**을 클릭합니다.

6. 프로젝트 속성을 업데이트합니다. **솔루션 탐색기에서**프로젝트 노드를 선택하고 오른쪽 단추를 클릭하고 **속성을**선택하여 **프로젝트 속성** 창을 엽니다.

    - 응용 **프로그램** 탭에서 **대상 프레임워크를** **4.6.1로**변경합니다.

    - **디버그** 탭에서 외부 **프로그램 시작** 상자에서 ** \<Visual Studio 설치 경로를>\Common7\IDE\devenv.exe를 입력합니다.**

         **명령줄 인수** 상자에서 입력 /**rootsuffix Exp**.

7. 다음 참조를 업데이트합니다.

    - Microsoft.VisualStudio.Shell.9.0.dll에 대한 참조를 제거한 다음 Microsoft.VisualStudio.Shell.14.0.dll 및 Microsoft.VisualStudio.Shell.11.0.dll에 대한 참조를 추가합니다.

    - Microsoft.VisualStudio.Package.Language.9.0.dll에 대한 참조를 제거한 다음 Microsoft.VisualStudio.Package.Language.14.0.dll에 대한 참조를 추가합니다.

    - Microsoft.VisualStudio.Shell.Interop.10.0.dll에 대한 참조를 추가합니다.

8. VsPkg.cs 파일을 열고 `DefaultRegistryRoot` 속성값을

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. 원래 샘플은 언어 서비스를 등록하지 않으므로 VsPkg.cs 다음 특성을 추가해야 합니다.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. source.extension.vsixmanifest 파일을 추가해야 합니다.

    - 기존 확장자에서 프로젝트 디렉터리로 이 파일을 복사합니다. 이 파일을 얻는 한 가지 방법은 VSIX 프로젝트를 만드는 **것입니다(파일**아래에서 **새**를 클릭한 다음 **프로젝트를**클릭합니다. 시각적 기본 또는 C# **확장성에서** **VSIX 프로젝트를**선택합니다.)

    - 파일을 사용자의 프로젝트에 추가합니다.

    - 파일의 **속성에서**빌드 **작업을** **없음으로**설정합니다.

    - **VSIX 매니페스트 편집기로 파일을 엽니다.**

    - 다음 필드를 변경합니다.

    - **ID**: 레그익랭서서비스

    - **제품 이름**: 레그익랭서트

    - **설명**: 정규표현식 언어 서비스입니다.

    - **자산에서** **새**를 클릭하고 **Source** **A project in current solution** **Project** **[[]을** 클릭하여 **RegExLangServ** **[[][1] [1] [1] [1] [1] [1] [1] [1] [1] [1] [1] [1] [1] [1] [1] [] []**[] [] [] [] []

    - 파일을 저장하고 닫습니다.

11. 솔루션을 빌드합니다. 빌드된 파일은 **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\확장자\MSIT\\\RegExLangServ 에 배포됩니다.**

12. 디버깅을 시작합니다. 비주얼 스튜디오의 두 번째 인스턴스가 열렸습니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)
