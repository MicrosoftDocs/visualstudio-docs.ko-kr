---
title: 데이터 중단점을 설정할 수 없습니다 | Microsoft Docs
ms.date: 12/3/2019
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unable_to_set_data_breakpoint
dev_langs:
- CSharp
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, data breakpoint
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: wardengnaw
ms.author: waan
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: c9f06b72673ea73e68f6c224ec9734568d70e25a
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852259"
---
# <a name="troubleshooting-data-breakpoint-errors"></a>데이터 중단점 오류 문제 해결
이 페이지에서는 “값이 변경되면 중단”을 사용할 때 표시되는 일반적인 오류를 해결하는 과정을 안내합니다.

## <a name="diagnosing-unable-to-set-data-breakpoint-errors"></a>“데이터 중단점을 설정할 수 없습니다.” 오류 진단
> [!IMPORTANT]
> 관리되는 데이터 중단점은 .NET Core 3.0 이상에서 지원됩니다. 최신 버전은 [여기](https://dotnet.microsoft.com/download)에서 다운로드할 수 있습니다.

다음은 관리되는 데이터 중단점을 사용할 때 발생할 수 있는 오류 목록입니다. 여기에는 오류가 발생하는 이유에 대한 추가 설명과 오류를 해결하기 위한 해결 방법이 포함되어 있습니다.

- “대상 프로세스에서 사용하는 .NET 버전이 데이터 중단점을 지원하지 않습니다. 데이터 중단점을 사용하려면 x86 또는 x64에서 실행되는 .NET Core 3.0 이상이 필요합니다.”

  - 관리되는 데이터 중단점은 .NET Core 3.0부터 지원되며 .NET Framework 또는 .NET Core under 3.0 버전에서는 현재 지원되지 않습니다. 
    
  - **솔루션**: 이 문제에 대한 해결 방법은 프로젝트를 .NET Core 3.0으로 업그레이드하는 것입니다.

- “관리되는 힙에서 값을 찾을 수 없으며 추적할 수 없습니다.”
  - 스택에서 선언된 변수입니다.
    - 스택에서 만든 변수는 함수가 종료되면 유효하지 않으므로 이 변수에 대한 데이터 중단점 설정은 지원되지 않습니다.
    - **해결 방법**: 변수가 사용되는 줄에서 중단점을 설정합니다.

  - 드롭다운에서 확장되지 않은 변수에 대해 “값이 변경되면 중단”
    - 추적하려는 필드가 포함된 개체를 디버거에서 내부적으로 알고 있어야 합니다. 추적하려는 변수가 들어 있는 개체를 디버거에서 알 수 있도록 가비지 수집기는 힙에서 개체를 주위로 이동할 수 있습니다. 
    - **해결 방법**: 데이터 중단점을 설정하려는 개체 내의 메서드에 있는 경우 한 프레임 위로 이동한 후 `locals/autos/watch` 창을 사용하여 개체를 확장하고 원하는 필드에 데이터 중단점을 설정합니다.

- “정적 필드 또는 정적 속성에는 데이터 중단점이 지원되지 않습니다.”
    
  - 정적 필드 및 속성은 현재 지원되지 않습니다. 이 기능에 관심이 있는 경우 [피드백](#provide-feedback)을 제공하세요.

- “구조체의 필드 및 속성을 추적할 수 없습니다.”

  - 구조체의 필드 및 속성은 현재 지원되지 않습니다. 이 기능에 관심이 있는 경우 [피드백](#provide-feedback)을 제공하세요.

- “속성 값이 변경되었으며 더 이상 추적할 수 없습니다.”

  - 속성에 따라 런타임 중에 계산되는 방법이 변경될 수 있습니다. 이 경우 속성이 종속되는 변수 수가 증가하여 하드웨어 제한을 초과할 수 있습니다. 아래 `"The property is dependent on more memory than can be tracked by the hardware."` 참조

- “속성이 하드웨어에서 추적할 수 있는 것보다 많은 메모리에 종속되어 있습니다.”
    
  - 각 아키텍처에 지원할 수 있는 바이트 수와 하드웨어 데이터 중단점이 설정되어 있으며, 데이터 중단점을 설정하려는 속성이 해당 제한을 초과했습니다. 사용 중인 아키텍처에 대해 사용할 수 있는 하드웨어 지원 데이터 중단점 및 바이트 수는 [데이터 중단점 하드웨어 제한](#data-breakpoint-hardware-limitations) 표를 참조하세요. 
  - **해결 방법**: 속성 내에서 변경할 수 있는 값에 대한 데이터 중단점을 설정합니다.

- “레거시 C# 식 계산기를 사용할 때에는 데이터 중단점이 지원되지 않습니다.”

  - 데이터 중단점은 레거시가 아닌 C# 식 계산기에서만 지원됩니다. 
  - **솔루션**: `Debug -> Options`로 이동하여 레거시 C# 식 계산기를 사용하지 않도록 설정한 다음, `Debugging -> General`에서 `"Use the legacy C# and VB expression evaluators"`를 선택 취소합니다.

## <a name="data-breakpoint-hardware-limitations"></a>데이터 중단점 하드웨어 제한 사항

프로그램이 실행되는 아키텍처(플랫폼 구성)에는 사용할 수 있는 하드웨어 데이터 중단점 수가 제한되어 있습니다. 아래 표에서는 아키텍처에 따라 사용할 수 있는 레지스터 수를 나타냅니다.

| 아키텍처 | 하드웨어 지원 데이터 중단점 수 | 최대 바이트 크기|
| :-------------: |:-------------:| :-------------:|
| x86 | 4 | 4 |
| X64 | 4 | 8 |
| ARM | 1 | 4 |
| ARM64 | 2 | 8 |

## <a name="provide-feedback"></a>피드백 제공

이 기능에 대한 문제 또는 제안 사항은 IDE 또는 [Developer Community](https://developercommunity.visualstudio.com/)에서 도움말 > 피드백 보내기 > [문제 보고](../ide/how-to-report-a-problem-with-visual-studio.md)를 통해 알려주세요.

## <a name="see-also"></a>참조

- [.NET Core 3.0에서 “값이 변경되면 중단” 사용](using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus)
- [DevBlog: 값이 변경되면 중단: Visual Studio 2019의 .NET Core에 대한 데이터 중단점](https://devblogs.microsoft.com/visualstudio/break-when-value-changes-data-breakpoints-for-net-core-in-visual-studio-2019/)
