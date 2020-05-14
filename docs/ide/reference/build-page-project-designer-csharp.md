---
title: 프로젝트 디자이너, 빌드 페이지(C#)
ms.date: 06/20/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuild
helpviewer_keywords:
- Build options [C#]
- Project Designer, Build page
ms.assetid: 77ff1bfc-d633-4634-ba29-9afdb6d7e362
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 85bf50c653d82a7de22d5a81fd81c38db0db1be8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76923261"
---
# <a name="build-page-project-designer-c"></a>프로젝트 디자이너, 빌드 페이지(C#)

**프로젝트 디자이너**의 **빌드** 페이지를 사용하여 프로젝트의 빌드 구성 속성을 지정합니다. 이 페이지는 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트에만 적용됩니다.

**빌드** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다. 그다음에 메뉴에서 **보기**, **속성 페이지**를 선택합니다. 프로젝트 디자이너가 나타나면 **빌드** 탭을 선택합니다.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>구성 및 플랫폼

다음 옵션을 사용하여 표시하거나 수정할 구성 및 플랫폼을 선택할 수 있습니다.

> [!NOTE]
> 단순화된 빌드 구성을 사용하면 프로젝트 시스템에서 디버그 버전을 빌드할지 아니면 릴리스 버전을 빌드할지 결정합니다. 따라서 이러한 옵션이 표시되지 않습니다. 자세한 내용은 [방법: 디버그 및 릴리스 구성 설정](../../debugger/how-to-set-debug-and-release-configurations.md)을 참조하세요.

**Configuration**

표시하거나 수정할 구성 설정을 지정합니다. **활성(디버그)** (기본값), **디버그**, **릴리스** 또는 **모든 구성** 중에서 설정을 선택할 수 있습니다.

**플랫폼**

표시하거나 수정할 플랫폼 설정을 지정합니다. 기본 설정은 **활성(모든 CPU)** 입니다. **구성 관리자**를 사용하여 활성 플랫폼을 변경할 수 있습니다. 자세한 내용은 [방법: 구성 만들기 및 편집](../../ide/how-to-create-and-edit-configurations.md)을 참조하세요.

## <a name="general"></a>일반

다음 옵션을 사용하여 여러 C# 컴파일러 설정을 구성할 수 있습니다.

**조건부 컴파일 기호**

조건부 컴파일을 수행할 기호를 지정합니다. 기호를 세미콜론(“;”)으로 구분합니다. 자세한 내용은 [/define(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option)을 참조하세요.

**DEBUG 상수 정의**

앱의 모든 소스 코드 파일에서 DEBUG를 기호로 정의합니다. 이 옵션을 선택하는 것은 `/define:DEBUG` 명령줄 옵션을 사용하는 것과 같습니다.

**TRACE 상수 정의**

앱의 모든 소스 코드 파일에서 TRACE를 기호로 정의합니다. 이 옵션을 선택하는 것은 `/define:TRACE` 명령줄 옵션을 사용하는 것과 같습니다.

**플랫폼 대상**

출력 파일의 대상으로 프로세서를 지정합니다. 32비트 Intel 호환 프로세서의 경우 **x86**을 선택하고, 64비트 Intel 호환 프로세서의 경우 **x64**를 선택하고, ARM 프로세서의 경우 **ARM**을 선택하고, 임의 프로세스를 허용하도록 지정하려면 **임의 CPU**를 선택합니다. **임의 CPU**는 프로젝트의 기본값입니다. 하드웨어의 가장 광범위한 범위에서 애플리케이션을 실행할 수 있기 때문입니다.

자세한 내용은 [/platform(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)을 참조하세요.

**Null 허용**

프로젝트 차원의 C# nullable 컨텍스트를 지정합니다. 이 UI 옵션은 Visual Studio 16.5에서 도입되었으며 C# 8.0 이상을 사용하는 프로젝트에서만 사용할 수 있습니다.

자세한 내용은 [Nullable 컨텍스트](/dotnet/csharp/nullable-references#nullable-contexts)를 참조하세요.

**32비트 선호**

**32비트 선호** 확인란을 선택하면 애플리케이션은 Windows 32비트 및 64비트 버전에서 모두 32비트 애플리케이션으로 실행됩니다. 이 확인란을 선택 취소하면 애플리케이션은 32비트 버전 Windows에서는 32비트 애플리케이션으로, 64비트 버전 Windows에서는 64비트 애플리케이션으로 실행됩니다.

애플리케이션을 64비트 애플리케이션으로 실행하면 포인터 크기가 두 배가 되고 32비트 전용인 다른 라이브러리에 대한 호환성 문제가 발생할 수 있습니다. 4GB 이상의 메모리가 필요하거나 64비트 명령으로 성능을 크게 향상할 수 있는 경우에만 64비트 애플리케이션을 실행하는 것이 좋습니다.

이 확인란은 다음 조건을 충족하는 경우에만 사용할 수 있습니다.

- **빌드 페이지**에서 **플랫폼 대상** 목록이 **임의 CPU**로 설정되어 있습니다.

- **애플리케이션 페이지**에서 **출력 형식** 목록의 프로젝트가 애플리케이션으로 지정됩니다.

- **애플리케이션 페이지**에서 **대상 프레임워크** 목록이 .NET Framework 4.5로 지정됩니다.

**안전하지 않은 코드 허용**

컴파일에 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) 키워드를 사용하는 코드를 허용합니다. 자세한 내용은 [/unsafe(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option)를 참조하세요.

**코드 최적화**

컴파일러에서 더 작지만 빠르고 효율적인 출력 파일을 만들기 위해 수행하는 최적화 기능을 사용하거나 사용하지 않도록 설정합니다. 자세한 내용은 [/optimize(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option)를 참조하세요.

## <a name="errors-and-warnings"></a>오류 및 경고

다음 설정은 빌드 프로세스에 대한 오류 및 경고 옵션을 구성하는 데 사용됩니다.

**경고 수준**

컴파일러 경고에 대한 표시 수준을 지정합니다. 자세한 내용은 [/warn(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option)을 참조하세요.

**경고 표시 안 함**

컴파일러에서 하나 이상의 경고를 생성하지 않도록 합니다. 여러 경고 번호를 쉼표 또는 세미콜론으로 구분합니다. 자세한 내용은 [/nowarn(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)을 참조하세요.

## <a name="treat-warnings-as-errors"></a>경고를 오류로 처리

다음 설정은 오류로 처리되는 경고를 지정하는 데 사용됩니다. 빌드에서 경고가 발생할 때 오류를 반환하는 조건을 지정하려면 다음 옵션 중 하나를 선택합니다. 자세한 내용은 [/warnaserror(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option)를 참조하세요.

**없음** - 경고를 오류로 처리하지 않습니다.

**모두** - 모든 경고를 오류로 처리합니다.

**특정 경고** - 지정된 경고를 오류로 처리합니다. 여러 경고 번호를 쉼표 또는 세미콜론으로 구분합니다.

> [!TIP]
> 코드 분석 경고를 오류로 취급하지 않으려면 [코드 분석 FAQ](../../code-quality/analyzers-faq.md#treat-warnings-as-errors)를 참조하세요.

## <a name="output"></a>출력

다음 설정은 빌드 프로세스에 대한 출력 옵션을 구성하는 데 사용됩니다.

**출력 경로**

프로젝트 구성에 사용할 출력 파일의 위치를 지정합니다. 이 상자에 빌드 출력의 경로를 입력하거나 **찾아보기** 단추를 선택하여 경로를 지정합니다. 경로는 상대 경로입니다. 절대 경로를 입력하면 상대 경로로 저장됩니다. 기본 경로는 bin\Debug 또는 bin\Release\\입니다.

단순화된 빌드 구성을 사용하면 프로젝트 시스템에서 디버그 버전을 빌드할지 아니면 릴리스 버전을 빌드할지 결정합니다. **디버그** 메뉴(F5)의 **빌드** 명령은 지정한 **출력 경로**에 관계없이 빌드를 디버그 위치에 삽입합니다. 그러나 **빌드** 메뉴의 **빌드** 명령은 경로를 지정한 위치에 삽입합니다. 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md)를 참조하세요.

**XML 문서 파일**

문서 주석을 처리할 대상 파일의 이름을 지정합니다. 자세한 내용은 [/doc(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)를 참조하세요.

**COM interop 등록**

관리되는 애플리케이션이 COM 개체가 관리되는 애플리케이션과 상호 작용할 수 있도록 하는 COM 개체(COM 호출 가능 래퍼)를 표시하도록 지정합니다. **COM interop 등록** 속성을 사용할 수 있으려면 이 애플리케이션에 대한 [프로젝트 디자이너](../../ide/reference/application-page-project-designer-visual-basic.md)의 **애플리케이션 페이지**에서 **출력 형식** 속성을 **클래스 라이브러리**로 설정해야 합니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 애플리케이션에 포함하고 COM 개체로 표시할 수 있는 클래스 예제는 [COM 클래스 예제](/dotnet/csharp/programming-guide/interop/example-com-class)를 참조하세요.

**serialization 어셈블리 생성**

XML serialization 어셈블리를 만드는 데 XML 직렬 변환기 생성기 도구(Sgen.exe)를 사용할지 여부를 지정합니다. 코드에서 형식을 직렬화하는 데 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용한 경우 serialization 어셈블리가 해당 클래스의 시작 성능을 향상할 수 있습니다. 기본적으로 이 옵션은 **자동**으로 설정됩니다. 이 설정은 코드에서 형식을 XML로 인코딩하는 데 <xref:System.Xml.Serialization.XmlSerializer>를 사용한 경우에만 serialization 어셈블리가 생성되도록 지정합니다. **끄기**는 코드에서 <xref:System.Xml.Serialization.XmlSerializer>를 사용하는지와 관계없이 serialization 어셈블리가 생성되지 않도록 지정합니다. **켜기**는 serialization 어셈블리가 항상 생성되도록 지정합니다. Serialization 어셈블리의 이름은 `TypeName`.XmlSerializers.dll로 지정됩니다. 자세한 내용은 [XML Serializer 생성기 도구(Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe)를 참조하세요.

**고급**

[고급 빌드 설정 대화 상자(C#)](../../ide/reference/advanced-build-settings-dialog-box-csharp.md) 대화 상자를 표시하려면 클릭합니다.

## <a name="see-also"></a>참고 항목

- [프로젝트 속성 참조](../../ide/reference/project-properties-reference.md)
- [C# 컴파일러 옵션](/dotnet/csharp/language-reference/compiler-options/index)
