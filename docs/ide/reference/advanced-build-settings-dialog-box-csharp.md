---
title: 고급 빌드 설정 대화 상자(C#)
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f25f9d96cd8de8dcb140c79c7dfb3a7a5981986c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595854"
---
# <a name="advanced-build-settings-dialog-box-c"></a>고급 빌드 설정 대화 상자(C#)

**프로젝트 디자이너**의 **고급 빌드 설정** 대화 상자를 사용하여 프로젝트의 고급 빌드 구성 속성을 지정합니다. 이 대화 상자는 C# 프로젝트에만 적용됩니다.

## <a name="general"></a>일반

다음 옵션을 사용하여 일반 고급 설정을 설정할 수 있습니다.

**언어 버전**

::: moniker range=">=vs-2019"

프로젝트의 대상 프레임워크에 따라 기본 언어 버전이 선택되는 방식에 대한 정보를 제공하는 [/langversion(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)에 대한 링크입니다.

::: moniker-end

::: moniker range="vs-2017"

사용할 언어의 버전을 지정합니다. 기능 집합은 버전에 따라 다르므로 이 옵션을 사용하여 컴파일러에서 구현된 기능의 하위 집합만 허용하도록 하거나 기존 표준과 호환되는 기능만 사용하도록 설정할 수 있습니다.

기본값은 C# 7.0입니다.

::: moniker-end

**내부 컴파일러 오류 보고**

Microsoft에 컴파일러 오류를 보고할지 여부를 지정합니다. **prompt**(기본값)로 설정되면 내부 컴파일러 오류가 발생할 경우 오류 보고서를 전자 방식으로 Microsoft에 보내는 옵션을 제공하는 프롬프트가 표시됩니다. **send**로 설정되면 오류 보고서가 자동으로 전송됩니다. **queue**로 설정되면 오류 보고서가 대기합니다. **none**으로 설정되면 오류가 컴파일러의 텍스트 출력으로만 보고됩니다. 자세한 내용은 [/errorreport(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)를 참조하세요.

**산술 연산 오버플로/언더플로 확인**

정수 산술 문이 [checked](/dotnet/csharp/language-reference/keywords/checked) 또는 [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) 키워드의 범위에 포함되지 않고 데이터 형식 범위를 벗어난 값을 생성할 경우 런타임 예외가 발생할지 여부를 지정합니다. 자세한 내용은 [/checked(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)를 참조하세요.

**mscorlib.dll을 참조하지 않음**

mscorlib.dll을 프로그램으로 가져와 전체 <xref:System> 네임스페이스를 정의할지 여부를 지정합니다. 고유한 <xref:System> 네임스페이스 및 개체를 정의하거나 만들려면 이 상자를 선택합니다. 자세한 내용은 [/nostdlib(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)를 참조하세요.

## <a name="output"></a>출력

다음 옵션을 사용하여 고급 출력 옵션을 지정할 수 있습니다.

**디버그 정보**

컴파일러에서 생성되는 디버깅 정보 형식을 지정합니다. 애플리케이션의 디버그 성능을 구성하는 방법에 대한 자세한 내용은 [쉽게 디버깅할 수 있도록 이미지 만들기](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug)를 참조하세요. 이 설정에는 다음과 같은 옵션이 있습니다.

- **없음**

   디버깅 정보가 생성되지 않도록 지정합니다.

- **full**

   디버거를 실행 중인 프로그램에 연결할 수 있습니다.

- **pdbonly**

   디버거에서 프로그램이 시작되는 경우 소스 코드 디버깅이 가능하지만, 실행 중인 프로그램이 디버거에 연결되는 경우 어셈블러만 표시됩니다.

- **portable**

   플랫폼과 관련되지 않은 이식 가능한 기호 파일인 .PDB 파일을 생성합니다. 이 파일은 기본 실행 파일의 콘텐츠 및 해당 콘텐츠 생성 방식에 대한 정보를 특히 디버거와 같은 다른 도구에 제공합니다. 자세한 내용은 [Portable PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md)(이식 가능한 PDB)를 참조하세요.

- **embedded**

   이식 가능한 기호 정보를 어셈블리에 포함합니다. 외부 .PDB 파일은 생성되지 않습니다.

자세한 내용은 [/debug(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)를 참조하세요.

**파일 맞춤**

출력 파일에 있는 섹션의 크기를 지정합니다. 유효한 값은 **512**, **1024**, **2048**, **4096** 및 **8192**입니다. 이러한 값은 바이트 단위로 측정됩니다. 각 섹션은 이 값의 배수인 경계에 맞춰지고 출력 파일 크기에 영향을 미칩니다. 자세한 내용은 [/filealign(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)을 참조하세요.

**라이브러리 기준 주소**

DLL을 로드할 기본 설정 기준 주소를 지정합니다. DLL에 대한 기본 기준 주소는 .NET Framework 공용 언어 런타임에 의해 설정됩니다. 자세한 내용은 [/baseaddress(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [C# 컴파일러 옵션](/dotnet/csharp/language-reference/compiler-options/index)
- [빌드 페이지, 프로젝트 디자이너(C#)](../../ide/reference/build-page-project-designer-csharp.md)
