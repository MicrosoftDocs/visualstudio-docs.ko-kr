---
title: '방법: 도메인별 언어 솔루션 만들기'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 844f3eb97ed9e07aa8125688d2bfe8944249b008
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541793"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>방법: 도메인별 언어 솔루션 만들기
DSL (도메인 특정 언어)은 특수화 된 Visual Studio 솔루션을 사용 하 여 만듭니다.

## <a name="prerequisites"></a>필수 구성 요소

이 절차를 시작 하기 전에 다음 구성 요소를 설치 합니다.

- Visual Studio
- Visual Studio SDK ( **Visual studio 확장 개발** 워크 로드의 일부로 설치 됨)
- 모델링 SDK (Visual Studio 구성 요소로 설치 됨)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>도메인별 언어 솔루션 만들기

1. 새 **도메인 특정 언어 디자이너** 프로젝트를 만들어 DSL 마법사를 시작 합니다.

   > [!NOTE]
   > 프로젝트에 대해 선택한 이름은 코드를 생성 하는 데 사용 될 수 있으므로 유효한 Visual c # 식별자 여야 합니다.

   ::: moniker range="vs-2017"

   ![DSL 만들기 대화 상자](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. DSL 템플릿을 선택 합니다.

    **도메인 특정 언어 옵션 선택** 페이지에서 **최소 언어**와 같은 솔루션 템플릿 중 하나를 선택 합니다. 만들려는 DSL과 비슷한 템플릿을 선택 합니다.

    솔루션 템플릿에 대 한 자세한 내용은 [도메인별 언어 솔루션 템플릿 선택](../modeling/choosing-a-domain-specific-language-solution-template.md)을 참조 하세요.

3. **파일 확장명** 페이지에 파일 이름 확장명을 입력 합니다. 컴퓨터에서 고유 해야 하며 DSL을 설치 하려는 모든 컴퓨터에서 고유 해야 합니다. **이 확장을 사용 하는 응용 프로그램 또는 Visual Studio 편집기가 없다는**메시지가 표시 됩니다.

   - 완전히 설치 되지 않은 이전 실험적 Dsl에서 파일 이름 확장명을 사용한 경우에는 Visual Studio SDK 메뉴에서 찾을 수 있는 **실험적 인스턴스 다시 설정** 도구를 사용 하 여 지울 수 있습니다.

   - 이 파일 확장명을 사용 하는 다른 Visual Studio 확장이 컴퓨터에 완전히 설치 된 경우 제거 하는 것이 좋습니다. **도구** 메뉴에서 **확장 관리자**를 클릭 합니다.

4. 마법사의 나머지 페이지에서 필드를 검사 하 고 필요한 경우 조정 합니다. 설정에 만족 하면 **마침**을 클릭 합니다. 설정에 대 한 자세한 내용은 [DSL 디자이너 Wizard Pages](#settings)를 참조 하세요.

    마법사는 **Dsl** 및 **dslpackage**라는 두 개의 프로젝트를 포함 하는 솔루션을 만듭니다.

   > [!NOTE]
   > 신뢰할 수 없는 소스에서 텍스트 템플릿을 실행 하지 않도록 경고 하는 메시지가 표시 되 면 **확인**을 클릭 합니다. 이 메시지를 다시 표시 하지 않도록 설정할 수 있습니다.

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a>DSL 디자이너 마법사 페이지
 여러 필드를 기본값으로 그대로 둘 수 있습니다. 그러나 파일 확장명 필드를 설정 했는지 확인 합니다.

### <a name="solution-settings-page"></a>솔루션 설정 페이지
 **도메인 특정 언어의 기반으로 사용할 템플릿을 선택 하십시오.**
만들려는 DSL과 비슷한 템플릿을 선택 합니다. 다른 템플릿은 편리한 시작점을 제공 합니다. 솔루션 템플릿을 선택 하면 마법사에서 설명이 표시 됩니다. 솔루션 템플릿에 대 한 자세한 내용은 [도메인별 언어 솔루션 템플릿 선택](../modeling/choosing-a-domain-specific-language-solution-template.md)을 참조 하세요.

 **도메인 특정 언어의 이름을 선택 하십시오.**
기본값은 솔루션 이름입니다. 이 값에서 코드가 생성 됩니다. 이 클래스는 c # 클래스 이름으로 유효 해야 합니다.

### <a name="file-extension-page"></a>파일 확장명 페이지
 **모델 파일이 사용 해야 하는 확장명은 무엇 인가요?**
새 파일 확장명을 입력 합니다.

 이 파일 확장명이 다음과 같이이 컴퓨터에서 사용 하도록 아직 등록 되지 않았는지 확인 합니다.

 **이 확장을 처리 하려면 등록 된 다른 도구 및 응용 프로그램을**확인 하세요. **이 확장명을 사용 하는 응용 프로그램 또는 Visual Studio 편집기가 없다는**메시지가 표시 되 면이 파일 확장명을 사용할 수 있습니다.

 도구 또는 패키지 목록이 표시 되 면 다음 중 하나를 수행 해야 합니다.

- 다른 파일 확장명을 입력 합니다.

     \- 또는 -

- Visual Studio 실험적 인스턴스를 다시 설정 합니다. 이렇게 하면 이전에 빌드한 모든 Dsl의 등록이 취소 됩니다. **시작** 메뉴에서 **모든 프로그램**, **Microsoft Visual Studio 2010 SDK**, **도구**를 차례로 클릭 한 다음 **Microsoft Visual Studio 2010 실험적 인스턴스를 다시 설정**합니다. 다시 사용 하려는 다른 모든 Dsl을 다시 작성할 수 있습니다.

     \- 또는 -

- 이 파일 확장명을 사용 하는 Visual Studio 확장이 컴퓨터에 완전히 설치 된 경우 제거 합니다. **도구** 메뉴에서 **확장 관리자**를 클릭 합니다.

### <a name="product-settings-page"></a>제품 설정 페이지
 **새 도메인별 언어가 속한 제품의 이름은 무엇 인가요?**
기본값은 DSL 이름입니다.

 이 값은 Windows 탐색기 (또는 파일 탐색기)에서이 파일 확장명을 가진 파일을 설명 하는 데 사용 됩니다.

 **제품이 속한 회사의 이름은 무엇 인가요?**
회사 이름입니다.

 이 값은 DSL 패키지의 AssemblyInfo 속성에 통합 됩니다.

 **이 솔루션의 프로젝트에 대 한 루트 네임 스페이스는 무엇 인가요?**
이 기본값은 회사 및 제품 이름에서 구성 된 이름입니다.

### <a name="signing-page"></a>서명 페이지
 **강력한 이름 키 파일 만들기** 기본 옵션은 DSL 어셈블리에 서명할 새 키를 만드는 것입니다.

 **기존 강력한 이름 키 사용** DSL을 다른 어셈블리와 통합 하려는 경우이 옵션을 사용 합니다.

 강력한 이름 지정에 대 한 자세한 내용은 [강력한 이름의 어셈블리 만들기 및 사용](/dotnet/standard/assembly/create-use-strong-named)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [도메인별 언어 정의 방법](../modeling/how-to-define-a-domain-specific-language.md)
- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
