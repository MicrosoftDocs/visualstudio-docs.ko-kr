---
title: 레거시 언어 서비스 마이그레이션 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707103"
---
# <a name="migrating-a-legacy-language-service"></a>레거시 언어 서비스 마이그레이션
프로젝트를 업데이트 하 고 프로젝트에 source.extension.vsixmanifest 파일을 추가 하 여 레거시 언어 서비스를 최신 버전의 Visual Studio로 마이그레이션할 수 있습니다. Visual Studio 편집기가이를 조정 하기 때문에 언어 서비스 자체는 이전과 마찬가지로 계속 작동 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 언어 서비스를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)을 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Visual Studio 2008 언어 서비스 솔루션을 최신 버전으로 마이그레이션
 다음 단계에서는 RegExLanguageService 이라는 Visual Studio 2008 샘플을 조정 하는 방법을 보여 줍니다. Visual studio *sdk 설치 경로*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ 폴더의 visual STUDIO 2008 sdk 설치에서이 샘플을 찾을 수 있습니다.

> [!IMPORTANT]
> 언어 서비스에서 색을 정의 하지 않는 경우 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> VSPackage에서를로 명시적으로 설정 해야 합니다 `true` .

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Visual Studio 2008 언어 서비스를 이후 버전으로 마이그레이션하려면

1. 최신 버전의 Visual Studio 및 Visual Studio SDK를 설치 합니다. SDK를 설치 하는 방법에 대 한 자세한 내용은 [Visual STUDIO Sdk 설치](../../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

2. Visual Studio에서 로드 하지 않고 RegExLangServ 파일을 편집 합니다.

     `Import`Microsoft.. n e t. .targets 파일을 참조 하는 노드에서 값을 다음 텍스트로 바꿉니다.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. 파일을 저장 한 다음 닫습니다.

4. RegExLangServ 솔루션을 엽니다.

5. **단방향 업그레이드** 창이 표시 됩니다. **확인**을 클릭합니다.

6. 프로젝트 속성을 업데이트 합니다. **솔루션 탐색기**에서 프로젝트 노드를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **속성**을 선택 하 여 **프로젝트 속성** 창을 엽니다.

    - **응용 프로그램** 탭에서 **대상 프레임 워크** 를 **4.6.1**로 변경 합니다.

    - **디버그** 탭의 **시작 외부 프로그램** 상자에\Common7\IDE\devenv.exe을 입력 ** \<Visual Studio installation path> 합니다**.

         **명령줄 인수** 상자에/**rootsuffix Exp**를 입력 합니다.

7. 다음 참조를 업데이트 합니다.

    - Microsoft.VisualStudio.Shell.9.0.dll에 대 한 참조를 제거한 다음 Microsoft.VisualStudio.Shell.14.0.dll 및 Microsoft.VisualStudio.Shell.Immutable.11.0.dll에 대 한 참조를 추가 합니다.

    - Microsoft.VisualStudio.Package.LanguageService.9.0.dll에 대 한 참조를 제거한 다음 Microsoft.VisualStudio.Package.LanguageService.14.0.dll에 대 한 참조를 추가 합니다.

    - Microsoft.VisualStudio.Shell.Interop.10.0.dll에 대 한 참조를 추가 합니다.

8. VsPkg.cs 파일을 열고 특성의 값을로 변경 합니다. `DefaultRegistryRoot`

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. 원래 샘플은 해당 언어 서비스를 등록 하지 않으므로 VsPkg.cs에 다음 특성을 추가 해야 합니다.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Source.extension.vsixmanifest 파일을 추가 해야 합니다.

    - 기존 확장에서이 파일을 프로젝트 디렉터리에 복사 합니다. 이 파일을 가져오는 한 가지 방법은 VSIX 프로젝트를 만드는 것입니다. **파일**에서 **새로**만들기를 클릭 한 다음 **프로젝트**를 클릭 합니다. Visual Basic 또는 c #에서 **확장성**을 클릭 한 다음 **VSIX 프로젝트**를 선택 합니다.

    - 파일을 사용자의 프로젝트에 추가합니다.

    - 파일 **속성**에서 **빌드 작업** 을 **없음**으로 설정 합니다.

    - **VSIX 매니페스트 편집기**를 사용 하 여 파일을 엽니다.

    - 다음 필드를 변경 합니다.

    - **ID**: RegExLangServ

    - **제품 이름**: RegExLangServ

    - **설명**: 정규식 언어 서비스입니다.

    - **자산**에서 **새로 만들기**를 클릭 하 고, **VisualStudio**에 대 한 **유형을** 선택 하 고, **소스** 를 **현재 솔루션의 프로젝트로**설정한 다음, **프로젝트** 를 **RegExLangServ**로 설정 합니다.

    - 파일을 저장하고 닫습니다.

11. 솔루션을 빌드합니다. 빌드된 파일은 **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ \\ **에 배포 됩니다.

12. 디버깅을 시작합니다. Visual Studio의 두 번째 인스턴스가 열렸습니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)
