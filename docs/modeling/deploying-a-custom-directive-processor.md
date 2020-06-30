---
title: 사용자 지정 지시문 처리기 배포
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4762ad21f117bebe22ecfce1c846f15d154b1bf5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536021"
---
# <a name="deploying-a-custom-directive-processor"></a>사용자 지정 지시문 처리기 배포

모든 컴퓨터에서 Visual Studio의 사용자 지정 지시문 프로세서를 사용 하려면이 항목에서 설명 하는 방법 중 하나를 사용 하 여 등록 해야 합니다.

이러한 방법은 다음과 같습니다.

- [Visual Studio 확장](../extensibility/shipping-visual-studio-extensions.md). 자신이 사용하는 컴퓨터와 다른 컴퓨터 둘 다에 지시문 프로세서를 설치하고 제거하는 방법을 제공합니다. 일반적으로 동일한 VSIX에 다른 기능을 패키지할 수도 있습니다.

- [VSPackage](../extensibility/internals/vspackages.md). 지시문 프로세서 외에 다른 기능이 포함된 VSPackage를 정의하는 경우 지시문 프로세서를 등록하는 간편한 방법이 있습니다.

- 레지스트리 키 설정. 이 방법에서는 지시문 프로세서에 대한 레지스트리 항목을 추가합니다.

Visual Studio 또는 MSBuild에서 텍스트 템플릿을 변환 하려는 경우에만 이러한 방법 중 하나를 사용 해야 합니다. 애플리케이션에서 사용자 지정 호스트를 사용하는 경우 사용자 지정 호스트는 각 지시문의 지시문 프로세서를 찾는 작업을 담당합니다.

## <a name="deploying-a-directive-processor-in-a-vsix"></a>VSIX로 지시문 프로세서 배포

[VSIX (Visual Studio Extension)](../extensibility/starting-to-develop-visual-studio-extensions.md)에 사용자 지정 지시문 프로세서를 추가할 수 있습니다.

 다음 두 항목이 .vsix 파일에 포함되어 있는지 확인해야 합니다.

- 사용자 지정 지시문 프로세서 클래스가 포함된 어셈블리(.dll)

- 지시문 프로세서를 등록하는 .pkgdef 파일. 이 파일의 루트 이름은 어셈블리와 동일해야 합니다. 예를 들어, 파일의 이름을 CDP.dll 및 CDP.pkgdef로 지정할 수 있습니다.

.vsix 파일의 내용을 검사하거나 변경하려면 파일 확장명을 .zip으로 변경한 다음 파일을 엽니다. 내용을 편집한 후 파일 이름을 다시 .vsix로 변경합니다.

여러 가지 방법으로 .vsix 파일을 만들 수 있습니다. 다음 절차에서는 한 가지 방법을 설명합니다.

#### <a name="to-develop-a-custom-directive-processor-in-a-vsix-project"></a>VSIX 프로젝트에서 사용자 지정 지시문 프로세서를 개발하려면

1. 새 **VSIX 프로젝트** 프로젝트를 만듭니다.

2. **Source.extension.vsixmanifest**에서 콘텐츠 형식 및 지원 되는 버전을 설정 합니다.

    1. VSIX 매니페스트 편집기의 **자산** 탭에서 **새로 만들기** 를 선택 하 고 새 항목의 속성을 설정 합니다.

         **콘텐츠 형식**  =  **VSPackage**

         **소스 프로젝트** = \<*the current project*>

    2. **선택한 버전** 을 클릭 하 고 지시문 프로세서를 사용할 설치 유형을 확인 합니다.

3. .pkgdef 파일을 추가하고 VSIX에 포함할 속성을 설정합니다.

    1. 텍스트 파일을 만들고 이름을 .pkgdef로 만듭니다. \<*assemblyName*>

         \<*assemblyName*>는 일반적으로 프로젝트의 이름과 동일 합니다.

    2. 솔루션 탐색기에서 이 파일을 선택하고 다음과 같이 속성을 설정합니다.

         **빌드 작업**  =  **콘텐츠**

         **출력 디렉터리**  =  에 복사 **항상 복사**

         **VSIX**  =  에 포함 **True**

    3. VSIX의 이름을 설정하고 ID가 고유한지 확인합니다.

4. .pkgdef 파일에 다음 텍스트를 추가합니다.

    ```
    [$RootKey$\TextTemplating]
    [$RootKey$\TextTemplating\DirectiveProcessors]
    [$RootKey$\TextTemplating\DirectiveProcessors\ CustomDirectiveProcessorName]
    @="Custom Directive Processor description"
    "Class"="NamespaceName.ClassName"
    "CodeBase"="$PackageFolder$\AssemblyName.dll"
    ```

     `CustomDirectiveProcessorName`, `NamespaceName`, `ClassName`, `AssemblyName`을 사용자 고유의 이름으로 바꿉니다.

5. 프로젝트에 다음 참조를 추가합니다.

    - **VisualStudio \* 입니다. 0**

    - **VisualStudio \* . 인터페이스입니다. 0**

    - **VisualStudio \* . vshost.exe. 0**

6. 사용자 지정 지시문 프로세서 클래스를 프로젝트에 추가합니다.

     이 클래스는 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 또는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>를 구현해야 하는 공용 클래스입니다.

#### <a name="to-install-the-custom-directive-processor"></a>사용자 지정 지시문 프로세서를 설치하려면

1. Windows 탐색기에서 빌드 디렉터리 (일반적으로 bin\Debug 또는 bin\Release)를 엽니다.

2. 다른 컴퓨터에 지시문 프로세서를 설치하려면 .vsix 파일을 해당 컴퓨터에 복사합니다.

3. .vsix 파일을 두 번 클릭합니다. Visual Studio 확장 설치 관리자가 표시 됩니다.

4. Visual Studio를 다시 시작합니다. 이제 사용자 지정 지시문 프로세서를 참조하는 지시문이 포함된 텍스트 템플릿을 실행할 수 있습니다. 각 지시문의 형식은 다음과 같습니다.

     `<#@ CustomDirective Processor="CustomDirectiveProcessorName" parameter1="value1" ... #>`

#### <a name="to-uninstall-or-temporarily-disable-the-custom-directive-processor"></a>사용자 지정 지시문 프로세서를 제거하거나 임시로 사용하지 않도록 설정하려면

1. Visual Studio **도구** 메뉴에서 **확장 관리자**를 클릭 합니다.

2. 지시문 프로세서를 포함 하는 VSIX를 선택 하 고 **제거** 또는 **사용 안 함**을 클릭 합니다.

### <a name="troubleshooting-a-directive-processor-in-a-vsix"></a>VSIX에서 지시문 프로세서 문제 해결
 지시문 프로세서가 작동하지 않으면 다음 제안 사항이 도움이 될 수 있습니다.

- 사용자 지정 지시문에서 지정하는 프로세서 이름이 .pkgdef 파일에서 지정한 `CustomDirectiveProcessorName`과 일치해야 합니다.

- `IsDirectiveSupported` 메서드가 `true`의 이름이 전달될 때 `CustomDirective`를 반환해야 합니다.

- 확장 관리자에서 확장을 볼 수 없지만 시스템에서 확장을 설치할 수 없는 경우 **%localappdata%\Microsoft\VisualStudio \\ \* .0 \\ \**확장에서 확장을 삭제 합니다.

- .vsix 파일을 열고 파일 내용을 검사합니다. 이 파일을 열려면 파일 확장명을 .zip으로 변경합니다. 이 파일에 .dll, .pkgdef 및 extension.vsixmanifest 파일이 포함되어 있는지 확인합니다. extension.vsixmanifest 파일은 SupportedProducts 노드에 적절한 목록을 포함해야 하며 Content 노드 아래에 VsPackage 노드를 포함해야 합니다.

     `<Content>`

     `<VsPackage>CustomDirectiveProcessor.dll</VsPackage>`

     `</Content>`

## <a name="deploying-a-directive-processor-in-a-vspackage"></a>VSPackage에서 지시문 프로세서 배포
 지시문 프로세서가 GAC에서 설치될 VSPackage에 포함된 경우 시스템에서 .pkgdef 파일을 자동으로 생성할 수 있습니다.

 패키지 클래스에 다음 특성을 배치합니다.

```csharp
[ProvideDirectiveProcessor(typeof(DirectiveProcessorClass), "DirectiveProcessorName", "Directive processor description.")]
```

> [!NOTE]
> 이 특성은 지시문 프로세서 클래스가 아니라 패키지 클래스에 배치됩니다.

 .pkgdef 파일은 프로젝트를 빌드할 때 생성됩니다. VSPackage를 설치하면 .pkgdef 파일이 지시문 프로세서를 등록합니다.

 .pkgdef 파일이 빌드 폴더에 나타나는지 확인합니다. 빌드 폴더는 대개 bin\Debug 또는 bin\Release입니다. 이 파일이 나타나지 않으면 텍스트 편집기에서 .csproj 파일을 열고 `<GeneratePkgDefFile>false</GeneratePkgDefFile>` 노드를 제거합니다.

 자세한 내용은 [VSPackages](../extensibility/internals/vspackages.md)을 참조하세요.

## <a name="setting-a-registry-key"></a>레지스트리 키 설정
 사용자 지정 지시문 프로세서를 설치하는 이 방법은 가장 선호되지 않는 방법입니다. 이 방법으로는 간편하게 지시문 프로세서를 사용하거나 사용하지 않도록 설정할 수 없으며 지시문 프로세서를 다른 사용자에게 배포할 수 없습니다.

> [!CAUTION]
> 레지스트리를 올바르게 편집하지 않으면 시스템을 심각하게 손상시킬 수 있습니다. 따라서 레지스트리를 변경하기 전에 컴퓨터에 있는 중요한 데이터를 백업해야 합니다.

#### <a name="to-register-a-directive-processor-by-setting-a-registry-key"></a>레지스트리 키를 설정하여 지시문 프로세서를 등록하려면

1. `regedit`을 실행합니다.

2. regedit에서 다음 레지스트리 키로 이동합니다.

    **HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ \* \ .0\ texttemplating\directiveprocessors**

    실험 버전의 Visual Studio에 지시문 프로세서를 설치 하려는 경우 "11.0" 뒤에 "Exp"를 삽입 합니다.

3. 지시문 프로세서 클래스와 이름이 같은 레지스트리 키를 추가합니다.

   - 레지스트리 트리에서 **DirectiveProcessors** 노드를 마우스 오른쪽 단추로 클릭 하 고 **새로 만들기**를 가리킨 다음 **키**를 클릭 합니다.

4. 새 노드에서 다음 표에 따라 Class와 CodeBase 또는 Assembly의 문자열 값을 추가합니다.

   1. 만든 노드를 마우스 오른쪽 단추로 클릭 하 고 **새로 만들기**를 가리킨 다음 **문자열 값**을 클릭 합니다.

   2. 값의 이름을 편집합니다.

   3. 이름을 두 번 클릭하고 데이터를 편집합니다.

   사용자 지정 지시문 프로세서가 GAC에 없는 경우 레지스트리 하위 키는 다음 표와 같습니다.

|Name|Type|데이터|
|-|-|-|
|(기본값)|REG_SZ|(값 설정 안 됨)|
|클래스|REG_SZ|**\<Namespace Name>.\<Class Name>**|
|CodeBase|REG_SZ|**\<Your Path>\\어셈블리 이름<\>**|

 어셈블리가 GAC에 있는 경우 레지스트리 하위 키는 다음 표와 같습니다.

|Name|Type|데이터|
|-|-|-|
|(기본값)|REG_SZ|(값 설정 안 됨)|
|클래스|REG_SZ|\<**Your Fully Qualified Class Name**>|
|어셈블리|REG_SZ|\<**Your Assembly Name in the GAC**>|

## <a name="see-also"></a>참고 항목

- [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기](../modeling/creating-custom-t4-text-template-directive-processors.md)
