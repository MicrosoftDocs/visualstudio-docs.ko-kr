---
title: 지원되는 코드 변경(C# 및 Visual Basic) | Microsoft Docs
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44881035da14483c3ddf1f4c48cb3957a1ce8b50
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729084"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>지원되는 코드 변경(C# 및 Visual Basic)
편집하며 계속하기에서는 메서드 본문 내의 코드 변경 유형을 대부분 처리합니다. 그러나 메서드 본문 외부의 변경 내용 대부분과 메서드 본문 내의 몇 가지 변경 내용은 디버깅 중에 적용할 수 없습니다. 이러한 지원되지 않는 변경 내용을 적용하려면 디버깅을 중지하고 새로운 버전의 코드로 다시 시작해야 합니다.

## <a name="supported-changes-to-code"></a>지원되는 코드 변경

다음 표에서는 세션을 다시 시작하지 않고 디버깅 세션 중에 C# 및 Visual Basic 코드에 적용할 수 있는 변경 내용을 보여 줍니다.

|언어 요소/기능|지원되는 편집 작업|제한 사항|
|-|-|-|
|유형|메서드, 필드, 생성자 등 추가|[예](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|반복기|추가 또는 수정|아니요|
|async/await 식|추가 또는 수정|[예](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|동적 개체|추가 또는 수정|아니요|
|람다 식|추가 또는 수정|[예](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|LINQ 식|추가 또는 수정|[람다 식과 동일](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> 문자열 보간 및 null 조건부 연산자와 같은 최신 언어 기능은 일반적으로 편집하며 계속하기에서 지원됩니다. 최신 정보는 [Enc 지원 편집](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) 페이지를 참조하세요.

## <a name="unsupported-changes-to-code"></a>지원되지 않는 코드 변경
 디버깅 세션 중에 C# 및 Visual Basic 코드에 적용할 수 없는 변경 내용은 다음과 같습니다.

- 현재 문 또는 다른 모든 활성 문에 대한 변경

     활성 문에는 호출 스택의 함수에서 현재 문을 실행하기 위해 호출된 모든 문이 포함됩니다.

     현재 문은 소스 창에서 노란색 배경으로 표시됩니다. 다른 활성 문은 배경이 회색으로 표시되고 읽기 전용입니다. 이러한 기본 색상은 **옵션** 대화 상자에서 변경할 수 있습니다.

- 다음 표에서는 언어 요소에서 지원되지 않는 코드 변경을 보여 줍니다.

|언어 요소/기능|지원되지 않는 편집 작업|
|-|-|
|모든 코드 요소|이름 바꾸기|
|네임스페이스|추가|
|네임스페이스, 형식, 멤버|삭제|
|제네릭|추가 또는 수정|
|인터페이스|수정|
|유형|추상 또는 가상 멤버 추가, 재정의 추가([세부 정보](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) 참조)|
|유형|소멸자 추가|
|멤버|포함된 interop 형식을 참조하는 멤버 수정|
|멤버|코드를 실행하여 이미 액세스한 후 정적 멤버 수정|
|멤버(Visual Basic)|On Error 또는 Resume 문을 사용하여 멤버 수정|
|멤버(Visual Basic)|Aggregate, Group By, Simple Join 또는 Group Join LINQ 쿼리 절이 포함된 멤버 수정|
|메서드|시그니처 수정|
|메서드|메서드 본문을 추가하여 추상 메서드가 비추상 메서드가 되도록 설정|
|메서드|Delete 메서드 본문|
|특성|추가 또는 수정|
|이벤트 또는 속성|형식 매개 변수, 기본 형식, 대리자 형식 또는 반환 형식 수정 |
|연산자 또는 인덱서|형식 매개 변수, 기본 형식, 대리자 형식 또는 반환 형식 수정 |
|catch 블록|활성 문이 포함된 경우 수정|
|try-catch-finally 블록|활성 문이 포함된 경우 수정|
|using 문|추가|
|비동기 메서드/람다|.NET Framework 4 이하를 대상으로 하는 프로젝트에서 비동기 메서드/람다 수정([세부 정보](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) 참조).|
|반복기|.NET Framework 4 이하를 대상으로 하는 프로젝트에서 반복기 수정([세부 정보](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) 참조)|

## <a name="unsafe-code"></a>안전하지 않은 코드
 안전하지 않은 코드의 변경에는 안전한 코드의 변경과 동일한 제한 사항이 적용되고 한 가지 제한 사항이 추가로 적용됩니다. `stackalloc` 연산자가 포함된 메서드 안에 있는 안전하지 않은 코드의 변경은 편집하며 계속하기에서 지원하지 않습니다.

## <a name="unsupported-app-scenarios"></a>지원되지 않는 앱 시나리오

지원되지 않는 앱 및 플랫폼으로는 ASP.NET 5, Silverlight 5 및 Windows 8.1이 있습니다.

> [!NOTE]
> 지원되는 앱에는 Windows 10의 UWP와 .NET Framework 4.6 데스크톱 이상 버전을 대상으로 하는 x86 및 x64 앱이 포함됩니다(.NET Framework는 데스크톱 버전에만 해당함).

## <a name="unsupported-scenarios"></a>지원되지 않는 시나리오
 다음과 같은 디버깅 시나리오에서는 편집하며 계속하기를 사용할 수 없습니다.

- 혼합 모드(네이티브/관리) 디버깅

- SQL 디버깅

- Dr. Watson 덤프 디버깅

- 포함된 런타임 애플리케이션 디버깅

- **디버그** 메뉴에서 **시작**을 선택하여 애플리케이션을 실행하는 대신 프로세스에 연결을 사용하여 애플리케이션 디버그(**디버그 > 프로세스에 연결**)

- 최적화된 코드 디버깅

- 빌드 오류가 발생하여 새 버전을 빌드하는 데 실패한 후 이전 버전의 코드 디버깅

## <a name="see-also"></a>참조
- [편집하며 계속하기(Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [방법: 편집하며 계속하기 사용(C#)](../debugger/how-to-use-edit-and-continue-csharp.md)