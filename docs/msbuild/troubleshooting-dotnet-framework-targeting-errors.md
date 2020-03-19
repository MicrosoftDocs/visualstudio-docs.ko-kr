---
title: .NET Framework 대상 지정 오류 문제 해결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1c496fd457e80220bb2ea4a2f032cef9508d9dcb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631603"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>.NET Framework 대상 지정 오류 문제 해결

이 항목에서는 참조 문제로 인해 발생할 수 있는 MSBuild 오류와 이러한 문제를 해결하는 방법을 설명합니다.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>다른 버전의.NET Framework를 대상으로 하는 프로젝트 또는 어셈블리를 참조한 경우

 다른 .NET Framework 버전을 대상으로 하는 프로젝트나 어셈블리를 참조하는 애플리케이션을 만들 수 있습니다. 예를 들어, .NET Framework 4용 클라이언트 프로파일을 대상으로 하지만 .NET Framework 2.0을 대상으로 하는 어셈블리를 참조하는 애플리케이션을 만들 수 있습니다. 그렇지만 이전 버전의 .NET Framework를 대상으로 하는 프로젝트를 만드는 경우 해당 프로젝트에서 .NET Framework 4용 클라이언트 프로필 또는 .NET Framework 4 자체를 대상으로 하는 프로젝트나 어셈블리에 대한 참조를 설정할 수 없습니다. 이 오류를 해결하려면 사용하는 애플리케이션이 애플리케이션에서 참조하는 프로젝트 또는 어셈블리의 대상으로 지정된 프로필에 호환되는 프로필을 대상으로 하는지 확인합니다.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>프로젝트의 대상을 다른 버전의 .NET Framework로 다시 지정한 경우

 애플리케이션에 대한 .NET Framework 대상 버전을 변경하는 경우 Visual Studio는 일부 참조를 변경하지만 사용자가 일부 참조를 수동으로 변경해야 할 수 있습니다. 예를 들어 애플리케이션 대상을 .NET Framework 3.5 서비스 팩 1로 변경하며, 해당 애플리케이션이 .NET Framework 4용 클라이언트 프로필에 의존하는 리소스 또는 설정을 갖는 경우 앞에서 언급한 오류 중 하나가 발생할 수 있습니다.

 애플리케이션 설정 문제를 해결하려면 **솔루션 탐색기**를 열고 **모든 파일 표시**를 선택한 후 Visual Studio XML 편집기에서 *app.config* 파일을 편집합니다. 설정의 버전을 .NET Framework의 적절한 버전과 일치하도록 변경합니다. 예를 들어 버전 설정을 4.0.0.0에서 2.0.0.0으로 변경할 수 있습니다. 마찬가지로 추가된 리소스가 있는 애플리케이션의 경우 **솔루션 탐색기**를 열고 **모든 파일 표시** 단추를 선택한 후 **내 프로젝트**(Visual Basic) 또는 **속성**(C#)을 확장하고 Visual Studio XML 편집기에서 *Resources.resx* 파일을 편집합니다. 버전 설정을 4.0.0.0에서 2.0.0.0으로 변경합니다.

 애플리케이션에 아이콘 또는 비트맵과 같은 리소스나 데이터 연결 문자열과 같은 설정이 있는 경우 **프로젝트 디자이너**의 **설정** 페이지에서 모든 항목을 제거한 후 필요한 설정을 다시 추가하여 오류를 해결할 수도 있습니다.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>프로젝트의 대상을 다른 버전의 .NET Framework로 다시 지정했으며 참조가 확인되지 않는 경우

 다른 버전의 .NET Framework로 프로젝트 대상을 다시 지정하는 경우 참조가 제대로 확인되지 않을 수 있습니다. 어셈블리에 대한 명시적 정규화 참조에서 종종 이 문제가 발생하지만, 확인되지 않는 참조를 제거한 다음 프로젝트에 다시 추가하여 이 문제를 해결할 수 있습니다. 대안으로, 프로젝트 파일을 편집하여 참조를 바꿀 수 있습니다. 먼저 다음 형식에 대한 참조를 제거합니다.

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 그런 후 다음과 같은 간단한 형식으로 바꿉니다.

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> 프로젝트를 닫았다가 다시 연 후에도 다시 빌드해야 모든 참조가 제대로 확인됩니다.

## <a name="see-also"></a>참조

- [방법: .NET Framework 버전 대상 지정](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework 클라이언트 프로필](/dotnet/framework/deployment/client-profile)
- [Framework 대상 지정 개요](../ide/visual-studio-multi-targeting-overview.md)
- [멀티 타기팅](../msbuild/msbuild-multitargeting-overview.md)
