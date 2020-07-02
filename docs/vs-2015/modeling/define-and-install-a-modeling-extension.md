---
title: 모델링 확장 정의 및 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ef79d1be0b88ecdafa8691189bbc95291a6417ed
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544991"
---
# <a name="define-and-install-a-modeling-extension"></a>모델링 확장 정의 및 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 모델링 다이어그램에 대한 확장을 정의할 수 있습니다. 이러한 방식으로 사용자 고유의 요구에 따라 다이어그램 및 모델을 조정할 수 있습니다. 예를 들어 메뉴 명령, UML 프로필, 유효성 검사 제약 조건 및 도구 상자 항목을 정의할 수 있습니다. 단일 확장에서 여러 개의 구성 요소를 정의할 수 있습니다. [VSIX(Visual Studio Integration Extension)](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)(영문) 형식으로 이러한 확장을 다른 Visual Studio 사용자에게 배포할 수도 있습니다. Visual Studio에서 VSIX 프로젝트를 사용하여 VSIX를 만들 수 있습니다.

## <a name="requirements"></a>요구 사항
 [요구 사항](../modeling/extend-uml-models-and-diagrams.md#Requirements)을 참조 하세요.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="creating-a-modeling-extension-solution"></a>모델링 확장 솔루션 만들기
 모델링 확장을 정의하려면 다음 프로젝트를 포함하는 솔루션을 만들어야 합니다.

- VSIX( [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integration Extension) 프로젝트. 확장 구성 요소의 설치 관리자 역할을 하는 파일이 생성됩니다.

- 프로그램 코드를 포함하는 구성 요소에 필요한 클래스 라이브러리 프로젝트.

  여러 구성 요소가 포함된 확장을 만들려는 경우 단일 솔루션으로 개발할 수 있습니다. VSIX 프로젝트 하나만 필요합니다.

  사용자 지정 도구 상자 항목 및 사용자 지정 UML 프로필과 같이 코드가 필요 없는 구성 요소는 별도의 클래스 라이브러리 프로젝트를 사용하지 않고 VSIX 프로젝트에 직접 추가할 수 있습니다. 프로그램 코드가 필요한 구성 요소는 별도의 클래스 라이브러리 프로젝트에서 보다 쉽게 정의됩니다. 코드가 필요한 구성 요소에는 제스처 처리기, 메뉴 명령 및 유효성 검사 코드가 포함됩니다.

#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>메뉴 명령, 제스처 처리기 또는 유효성 검사에 대한 클래스 라이브러리 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 선택합니다.

2. **설치된 템플릿**에서 **Visual C#** 또는 **Visual Basic**을 선택한 다음 **클래스 라이브러리**를 선택합니다.

#### <a name="to-create-a-vsix-project"></a>VSIX 프로젝트를 만들려면

1. 코드가 포함된 구성 요소를 만드는 경우 먼저 클래스 라이브러리 프로젝트를 만드는 것이 가장 쉽습니다. 해당 프로젝트에 코드를 추가합니다.

2. VSIX 프로젝트를 만듭니다.

    1. **솔루션 탐색기**의 솔루션 바로 가기 메뉴에서 **추가**, **새 프로젝트**를 선택합니다.

    2. **설치된 템플릿**에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **확장성**을 선택합니다. 가운데 열에서 **VSIX 프로젝트**를 선택합니다.

3. VSIX 프로젝트를 솔루션의 시작 프로젝트로 설정합니다.

    - 솔루션 탐색기의 VSIX 프로젝트 바로 가기 메뉴에서 **시작 프로젝트로 설정**을 선택 합니다.

4. **source.extension.vsixmanifest**를 엽니다. 파일이 매니페스트 편집기에서 열립니다.

5. **메타데이터** 탭에서 VSIX의 이름 및 설명 필드를 설정합니다.

6. **설치 대상** 탭에서 **새로 만들기** 를 선택하고 Visual Studio 버전을 대상으로 설정합니다.

7. **자산** 탭에서 Visual Studio 확장에 구성 요소를 추가합니다.

    1. **새로 만들기**를 선택합니다.

    2. 코드가 포함된 구성 요소의 경우 **새 자산 추가** 대화 상자에서 다음 필드를 설정합니다.

        |필드|값|
        |-|-|
        |**입력할** =|**Microsoft.VisualStudio.MefComponent**|
        |**원본** =|**현재 솔루션의 프로젝트**|
        |**Project** =|*클래스 라이브러리 프로젝트*|
        |**이 폴더에 포함** =|*비우려면*|

         다른 구성 요소 형식의 경우 다음 섹션의 링크를 참조하세요.

## <a name="developing-the-component"></a>구성 요소 개발
 메뉴 명령 또는 제스처 처리기와 같은 각 구성 요소에 대해 별도의 처리기를 정의해야 합니다. 동일한 클래스 라이브러리 프로젝트에 여러 개의 처리기를 넣을 수 있습니다. 다음 표에서는 다양한 종류의 처리기를 요약해서 보여 줍니다.

|확장 형식|항목|각 구성 요소의 일반적인 선언 방법|
|--------------------|-----------|----------------------------------------------|
|메뉴 명령|[모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|
|끌어서 놓기 또는 두 번 클릭|[모델링 다이어그램의 제스처 처리기 정의](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|
|유효성 검사 제약 조건|[UML 모델에 대한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|
|작업 항목 링크 이벤트 처리기|[작업 항목 링크 처리기 정의](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|
|UML 프로필|[프로필을 정의하여 UML 확장](../modeling/define-a-profile-to-extend-uml.md)|(정의 예정)|
|도구 상자 항목|[사용자 지정 모델링 도구 상자 항목 정의](../modeling/define-a-custom-modeling-toolbox-item.md)|(정의 예정)|

## <a name="running-an-extension-during-its-development"></a>개발 중에 확장 실행

#### <a name="to-run-an-extension-during-its-development"></a>개발 중에 확장을 실행하려면

1. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **디버그** 메뉴에서 **Start 디버그ging**을 선택합니다.

     프로젝트가 빌드되고, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 의 새 인스턴스가 실험적 모드에서 시작됩니다.

    - 또는 **디버깅하지 않고 시작**을 선택할 수 있습니다. 이렇게 하면 프로그램을 시작하는 데 걸리는 시간이 줄어듭니다.

2. Visual Studio의 실험적 인스턴스에서 모델링 프로젝트를 만들거나 열고 다이어그램을 만들거나 엽니다.

     확장이 로드되어 실행됩니다.

3. **디버깅하지 않고 시작** 을 사용했지만 디버거를 사용하려는 경우 Visual Studio의 기본 인스턴스로 돌아갑니다. **디버그** 메뉴에서 **프로세스에 연결**을 클릭합니다. 대화 상자에서 프로그램 이름이 **devenv**인 Visual Studio의 실험적 인스턴스를 선택합니다.

## <a name="installing-and-uninstalling-an-extension"></a><a name="Installing"></a>확장 설치 및 제거
 자신의 컴퓨터나 다른 컴퓨터의 Visual Studio 기본 인스턴스에서 확장을 실행하려면 다음 단계를 수행합니다.

1. 사용 중인 컴퓨터에서 확장 프로젝트를 통해 빌드된 **.vsix** 파일을 찾습니다.

    1. **솔루션 탐색기**의 프로젝트 바로 가기 메뉴에서 **Windows 탐색기에서 폴더 열기**를 선택합니다.

    2. 파일 ** \\ \* bin \\ **_을 찾습니다_**. vsix**

2. 확장을 설치할 대상 컴퓨터에 **.vsix** 파일을 복사합니다. 이 컴퓨터는 사용 중인 컴퓨터이거나 다른 컴퓨터일 수 있습니다.

    - 대상 컴퓨터에 **source.extension.vsixmanifest** 의 **설치 대상**탭에서 지정한 Visual Studio 버전 중 하나가 있어야 합니다.

3. 대상 컴퓨터에서 **.vsix** 파일을 두 번 클릭하여 엽니다.

     **Visual Studio 확장 설치 관리자** 에서 확장을 열고 설치합니다.

4. Visual Studio를 시작하거나 다시 시작합니다.

#### <a name="to-uninstall-an-extension"></a>확장을 제거하려면

1. **도구** 메뉴에서 **확장 및 업데이트**를 클릭합니다.

2. **설치된 확장**을 확장합니다.

3. 확장을 선택하고 **제거**를 클릭합니다.

   드물게 결함이 있는 확장은 로드되지 않고 오류 창에 보고서를 생성하지만 확장 관리자에 나타나지 않습니다. 이 경우 다음 위치에서 파일을 삭제 하 여 확장을 제거할 수 있습니다. 여기서 *% LocalAppData%* 는 일반적으로 *DriveName*: \Users \\ *UserName*\AppData\Local입니다.

   *% LocalAppData%* **\Microsoft\VisualStudio \\ [version] \extensions**

## <a name="see-also"></a>참고 항목
 [프로필을 정의 하 여 uml 확장](../modeling/define-a-profile-to-extend-uml.md) [사용자 지정 모델링 도구 상자 정의](../modeling/define-a-custom-modeling-toolbox-item.md) [uml 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md) [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
