---
title: 프로젝트 디자이너, 컴파일 페이지(Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7a97068b70a76dfe343de5fa68db77d2ce9781
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111311"
---
# <a name="compile-page-project-designer-visual-basic"></a>프로젝트 디자이너, 컴파일 페이지(Visual Basic)

프로젝트 디자이너의 **컴파일** 페이지를 사용하여 컴파일 지침을 지정합니다. 또한 이 페이지에서 고급 컴파일러 옵션 및 빌드 전 또는 빌드 후 이벤트를 지정할 수 있습니다.

**컴파일** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다. 그런 다음 메뉴 모음에서 **프로젝트**, **속성**을 선택합니다. 프로젝트 디자이너가 나타나면 **컴파일** 탭을 클릭합니다.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>구성 및 플랫폼

다음 설정을 사용하면 표시하거나 수정할 구성 및 플랫폼을 선택할 수 있습니다.

> [!NOTE]
> 단순화된 빌드 구성을 사용하면 프로젝트 시스템에서 디버그 버전을 빌드할지 아니면 릴리스 버전을 빌드할지 결정합니다. 따라서 **구성** 및 **플랫폼** 목록이 표시되지 않습니다.

**Configuration**

표시하거나 수정할 구성 설정을 지정합니다. 설정은 **디버그**(기본값), **릴리스** 또는 **모든 구성**입니다. 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md) 및 [방법: 구성 만들기 및 편집](../../ide/how-to-create-and-edit-configurations.md)을 참조하세요.

**플랫폼**

표시하거나 수정할 플랫폼 설정을 지정합니다. **모든 CPU**(기본값), **x64** 또는 **x86**을 지정할 수 있습니다.

## <a name="compiler-configuration-options"></a>컴파일러 구성 옵션

다음 설정을 사용하면 컴파일러 구성 옵션을 설정할 수 있습니다.

**빌드 출력 경로**

프로젝트 구성에 사용할 출력 파일의 위치를 지정합니다. 이 상자에 빌드 출력의 경로를 입력하거나 **찾아보기** 단추를 클릭하여 경로를 선택합니다. 경로는 상대 경로입니다. 절대 경로를 입력하면 상대 경로로 저장됩니다. 기본 경로는 bin\Debug\ 또는 bin\Release\\입니다.

단순화된 빌드 구성을 사용하면 프로젝트 시스템에서 디버그 버전을 빌드할지 아니면 릴리스 버전을 빌드할지 결정합니다. **디버그** 메뉴(F5)의 **빌드** 명령은 지정한 **출력 경로**에 관계없이 빌드를 디버그 위치에 삽입합니다. 그러나 **빌드** 메뉴의 **빌드** 명령은 경로를 지정한 위치에 삽입합니다.

**Option Explicit**

암시적 변수 선언을 허용할지 여부를 지정합니다. 명시적 변수 선언이 필요하면 **On**을 선택합니다. 그러면 변수를 사용하기 전에 선언되지 않은 경우 컴파일러에서 오류를 보고합니다. 암시적 변수 선언을 허용하려면 **Off**를 선택합니다.

이 설정은 [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) 컴파일러 옵션에 해당합니다.

소스 코드 파일에 [Option Explicit 문](/dotnet/visual-basic/language-reference/statements/option-explicit-statement)이 포함되어 있는 경우 명령문의 `On` 또는 `Off` 값이 **컴파일 페이지**의 **Option Explicit** 설정을 재정의합니다.

새 프로젝트를 만들 때 **컴파일 페이지**의 **Option Explicit** 설정이 **옵션** 대화 상자의 **Option Explicit** 설정 값으로 지정됩니다. 이 대화 상자의 설정을 보거나 변경하려면 **도구** 메뉴에서 **옵션**을 클릭합니다. **옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장하고 **VB 기본값**을 클릭합니다. **VB 기본값**에서 **Option Explicit**의 초기 기본 설정은 **On**입니다.

**Option Explicit**를 `Off`로 설정하는 것은 일반적으로 좋은 사례가 아닙니다. 하나 이상의 위치에서 변수 이름을 잘못 입력할 수 있습니다. 그러면 프로그램이 실행될 때 예기치 않은 결과가 발생할 수 있습니다.

**Option Strict**

엄격한 형식 의미 체계를 적용할지 여부를 지정합니다. **Option Strict**가 **On**으로 지정되면 다음과 같은 조건에서 컴파일 시간 오류가 발생합니다.

- 암시적 축소 변환

- 런타임에 바인딩

- `Object` 유형으로 이어지는 암시적 형식 지정

암시적 축소 변환 오류는 축소 변환인 암시적 데이터 형식 변환이 있을 경우 발생합니다. 자세한 내용은 [Option Strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [암시적 변환과 명시적 변환](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) 및 [확대 변환과 축소 변환](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)을 참조하세요.

개체에 `Object` 형식으로 선언된 변수의 속성 또는 메서드에 할당되면 런타임에 바인딩됩니다. 자세한 내용은 [Option Strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement) 및 [초기 바인딩 및 런타임에 바인딩](/dotnet/visual-basic/programming-guide/language-features/early-late-binding)을 참조하세요.

암시적 개체 형식 오류는 선언된 변수에 대해 적절한 형식이 유추될 수 없어 `Object`의 형식이 유추될 때 발생합니다. 주로 `Dim` 절을 사용하지 않고 `As` 문을 사용하여 변수를 선언하고, `Option Infer`가 꺼져 있는 경우 발생합니다. 자세한 내용은 [Option Strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer 문](/dotnet/visual-basic/language-reference/statements/option-infer-statement) 및 [Visual Basic 언어 사양](/dotnet/visual-basic/reference/language-specification)을 참조하세요.

**Option Strict** 설정은 [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) 컴파일러 옵션에 해당합니다.

소스 코드 파일에 [Option Strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement)이 포함되어 있는 경우 명령문의 `On` 또는 `Off` 값이 **컴파일 페이지**의 **Option Strict** 설정을 재정의합니다.

프로젝트를 만들 때 **컴파일 페이지**의 **Option Strict** 설정이 **옵션** 대화 상자의 **Option Strict** 설정 값으로 지정됩니다. 이 대화 상자의 설정을 보거나 변경하려면 **도구** 메뉴에서 **옵션**을 클릭합니다. **옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장하고 **VB 기본값**을 클릭합니다. **VB 기본값**에서 **Option Strict**의 초기 기본 설정은 **Off**입니다.

**Option Strict 개별 경고**

**컴파일 페이지**의 **경고 구성** 섹션에 `Option Strict`가 켜져 있을 때 컴파일 시간 오류가 발생하는 세 가지 조건에 해당하는 설정이 있습니다. 이러한 설정은 다음과 같습니다.

- **암시적 변환**

- **런타임에 바인딩; 호출이 실패할 수 있음**

- **암시적 형식; 개체로 간주**

**Option Strict**를 **On**으로 설정하는 경우 이러한 세 가지 경고 구성 설정은 모두 **Error**로 설정됩니다. **Option Strict**를 **Off**로 설정하는 경우 세 가지 설정은 모두 **None**으로 설정됩니다.

각 경고 구성 설정은 **None**, **Warning** 또는 **Error**로 개별적으로 변경할 수 있습니다. 세 가지 경고 구성 설정이 모두 **Error**로 설정된 경우 `On`이 `Option strict` 상자에 표시됩니다. 세 가지 모두 **None**으로 설정된 경우 `Off`가 이 상자에 표시됩니다. 이러한 설정의 다른 조합의 경우 **(사용자 지정)** 이 나타납니다.

**Option Compare**

사용할 문자열 비교 형식을 지정합니다. 이진, 대/소문자 구분 문자열 비교를 사용하도록 컴파일러에 지시하려면 **Binary**를 선택합니다. 로캘별 대/소문자 구분 문자열 비교를 사용하려면 **Text**를 선택합니다.

이 설정은 [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) 컴파일러 옵션에 해당합니다.

소스 코드 파일에 [Option Compare 문](/dotnet/visual-basic/language-reference/statements/option-compare-statement)이 포함되어 있는 경우 명령문의 `Binary` 또는 `Text` 값이 **컴파일 페이지**의 **Option Compare** 설정을 재정의합니다.

프로젝트를 만들 때 **컴파일 페이지**의 **Option Compare** 설정이 **옵션** 대화 상자의 **Option Compare** 설정 값으로 지정됩니다. 이 대화 상자의 설정을 보거나 변경하려면 **도구** 메뉴에서 **옵션**을 클릭합니다. **옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장하고 **VB 기본값**을 클릭합니다. **VB 기본값**에서 **Option Compare**의 초기 기본 설정은 **Binary**입니다.

**Option Infer**

변수 선언에서 지역 형식 유추를 허용할지 여부를 지정합니다. 지역 형식 유추를 사용하려면 **On**을 선택합니다. 지역 형식 유추를 차단하려면 **Off**를 선택합니다.

이 설정은 [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) 컴파일러 옵션에 해당합니다.

소스 코드 파일에 [Option Infer 문](/dotnet/visual-basic/language-reference/statements/option-infer-statement)이 포함되어 있는 경우 명령문의 `On` 또는 `Off` 값이 **컴파일 페이지**의 **Option Infer** 설정을 재정의합니다.

프로젝트를 만들 때 **컴파일 페이지**의 **Option Infer** 설정이 **옵션** 대화 상자의 **Option Infer** 설정 값으로 지정됩니다. 이 대화 상자의 설정을 보거나 변경하려면 **도구** 메뉴에서 **옵션**을 클릭합니다. **옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장하고 **VB 기본값**을 클릭합니다. **VB 기본값**에서 **Option Infer**의 초기 기본 설정은 **On**입니다.

**대상 CPU**

출력 파일의 대상으로 프로세서를 지정합니다. 32비트 Intel 호환 프로세서의 경우 **x86**, 64비트 Intel 호환 프로세서의 경우 **x64**, ARM 프로세서의 경우 **ARM**, 임의 프로세스를 허용하도록 지정하려면 **임의 CPU**를 선택합니다. **임의 CPU**는 새 프로젝트의 기본값입니다. 하드웨어 형식 중 가장 광범위한 범위에서 애플리케이션을 실행할 수 있기 때문입니다.

자세한 내용은 [/platform(Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform)을 참조하세요.

**32비트 선호**

**32비트 선호** 확인란을 선택하면 애플리케이션은 Windows 32비트 및 64비트 버전에서 모두 32비트 애플리케이션으로 실행됩니다. 그렇지 않은 경우 애플리케이션은 32비트 버전 Windows에서는 32비트 애플리케이션으로, 64비트 버전 Windows에서는 64비트 애플리케이션으로 실행됩니다.

64비트 애플리케이션으로 실행하면 포인터 크기가 두 배가 되어 단독으로 32비트인 라이브러리에서 호환성 문제가 발생할 수 있습니다. 매우 빠르게 실행하거나 4GB 이상의 메모리가 필요한 경우에만 애플리케이션을 64비트로 실행해야 합니다.

이 확인란은 다음 조건을 충족하는 경우에만 사용할 수 있습니다.

- **컴파일 페이지**에서 **대상 CPU** 목록이 **임의 CPU**로 설정됩니다.

- **애플리케이션 페이지**에서 **애플리케이션 형식** 목록이 프로젝트가 애플리케이션임을 지정합니다.

- **애플리케이션 페이지**에서 **대상 프레임워크** 목록이 .NET Framework 4.5로 지정됩니다.

**경고 구성**

이 표에는 빌드 조건과 각각의 **None**, **Warning** 또는 **Error**의 해당 알림 수준이 나열되어 있습니다.

기본적으로 모든 컴파일러 경고는 컴파일하는 동안 작업 목록에 추가됩니다. 경고 또는 오류를 발급하지 않도록 컴파일러에 지시하려면 **모든 경고 사용 안 함**을 선택합니다. 컴파일러가 경고를 수정해야 하는 오류로 처리하도록 하려면 **모든 경고를 오류로 처리**를 선택합니다.

**모든 경고 사용 안 함**

컴파일러가 이 문서의 앞부분에서 설명한 **조건 및 알림** 표에 지정된 대로 알림을 발급하도록 허용할지 여부를 지정합니다. 이 확인란은 기본적으로 선택되어 있지 않습니다. 컴파일러가 경고 또는 오류를 발급하지 않도록 지시하려면 이 확인란을 선택합니다.

이 설정은 [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) 컴파일러 옵션에 해당합니다.

**모든 경고를 오류로 처리**

경고를 처리하는 방법을 지정합니다. 기본적으로 이 확인란의 선택을 취소하면 모든 경고 알림이 **Warning**으로 설정된 상태로 유지됩니다. 모든 경고 알림을 **Error**로 변경하려면 이 확인란을 선택합니다.

이 옵션은 **모든 경고 사용 안 함**을 선택 취소한 경우에만 사용할 수 있습니다.

**XML 문서 파일 생성**

문서 정보를 생성할지 여부를 지정합니다. 기본적으로 이 확인란을 선택하면 컴파일러에 문서 정보를 생성하고 XML 파일에 포함하도록 지시합니다. 컴파일러에 문서를 만들지 않도록 지시하려면 이 확인란의 선택을 취소합니다.

이 설정은 [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) 컴파일러 옵션에 해당합니다.

**COM interop 등록**

관리 애플리케이션이 COM 개체가 애플리케이션과 상호 작용할 수 있도록 하는 COM 개체(COM 호출 가능 래퍼)를 표시할지 여부를 지정합니다.

기본적으로 이 확인란의 선택을 취소하면 애플리케이션은 COM interop를 허용하지 않도록 지정됩니다. COM interop를 허용하려면 이 확인란을 선택합니다.

이 옵션은 Windows 애플리케이션 또는 콘솔 애플리케이션 프로젝트에 사용할 수 없습니다.

**빌드 이벤트**

**빌드 이벤트** 대화 상자에 액세스하려면 이 단추를 클릭합니다. 이 대화 상자를 사용하여 프로젝트에 대한 빌드 전 및 빌드 후 구성 지침을 지정할 수 있습니다. 이 대화 상자는 Visual Basic 프로젝트에만 적용됩니다. 자세한 내용은 [빌드 이벤트 대화 상자(Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md)를 참조하세요.

**고급 컴파일 옵션**

**AdvancedCompiler 설정** 대화 상자에 액세스하려면 이 단추를 클릭합니다. **AdvancedCompiler 설정** 대화 상자를 사용하여 프로젝트의 고급 빌드 구성 속성을 지정합니다. 이 대화 상자는 Visual Basic 프로젝트에만 적용됩니다. 자세한 내용은 [고급 컴파일러 설정 대화 상자(Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [방법: 빌드 이벤트 지정(Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic 명령줄 컴파일러](/dotnet/visual-basic/reference/command-line-compiler/index)
- [방법: 구성 만들기 및 편집](../../ide/how-to-create-and-edit-configurations.md)
