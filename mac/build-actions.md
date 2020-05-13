---
title: 빌드 작업
description: 이 문서에서는 C# 프로젝트에 사용할 수 있는 여러 빌드 작업에 대해 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 5399BCB1-E317-4C7B-87B1-C531E985DE6E
ms.openlocfilehash: d089f38bd91eda2565f215e8d15a74cc119b8767
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714396"
---
# <a name="build-actions"></a>빌드 작업

Mac용 Visual Studio 프로젝트의 모든 파일에는 빌드 작업이 포함됩니다. 빌드 작업은 빌드 중 파일의 처리 방식을 제어합니다. 

>[!NOTE]
>이 토픽은 Mac용 Visual Studio에 적용됩니다. Windows용 Visual Studio의 경우 [빌드 작업](/visualstudio/ide/build-actions)을 참조하세요.

## <a name="set-a-build-action"></a>빌드 작업 설정

Mac용 Visual Studio에서 파일에 대해 빌드 작업을 설정하려면, 아래 그림과 같이 파일을 마우스 오른쪽 단추로 클릭하고 **빌드 작업**을 찾을 수 있습니다.

![솔루션 탐색기에서 컴파일 빌드 작업 선택](media/projects-and-solutions-image1.png)

이 파일에 대한 빌드 작업은 플라이아웃 메뉴에 표시됩니다. 

## <a name="build-action-values"></a>빌드 작업 값

Mac용 Visual Studio에서 빌드할 수 있는 프로젝트에 대한 몇 가지 일반적인 빌드 작업은 다음과 같습니다.

|빌드 동작 | 프로젝트 형식 | Description |
|--|--|--|
| **컴파일** | any | 파일이 소스 파일로 C# 컴파일러에 전달됩니다.|
| **콘텐츠** | .NET, Xamarin | ASP.NET 프로젝트의 경우 이러한 파일은 배포 시 사이트의 일부로 포함됩니다. Xamarin.iOS 및 Xamarin.Mac 프로젝트의 경우 앱 번들에 포함됩니다.|
| **포함 리소스** | .NET | 파일이 어셈블리에 포함될 리소스로 C# 컴파일러에 전달됩니다. 그런 다음, [ 네임스페이스의 ](/dotnet/api/system.reflection.assembly.getmanifestresourcestream)Assembly.GetManifestResourceStream`System.Reflection`을 사용하여 어셈블리에서 파일을 읽을 수 있습니다.|
| **없음** | any | 파일이 어떤 방식으로든 빌드에 속하지 않고, IDE에서 쉽게 액세스할 수 있도록 프로젝트에 포함됩니다. 이 값은 예를 들어 "ReadMe" 파일과 같은 문서 파일에 사용할 수 있습니다.|

> [!NOTE]
> 추가 빌드 작업은 특정 프로젝트 형식에 대해 정의할 수 있으므로 빌드 작업 목록은 프로젝트 형식에 따라 다르며, 이 목록에 없는 값이 표시될 수 있습니다.  

Xamarin.iOS 프로젝트에는 앱 번들의 일부로 파일을 추가하는 **BundleResource** 빌드 작업이 있습니다. Xamarin.Android 특정 빌드 작업에 대한 정보는 [빌드 프로세스](/xamarin/android/deploy-test/building-apps/build-process#Build_Actions) 가이드에서 확인할 수 있습니다.

솔루션 탐색기에서 둘 이상의 파일을 선택하여 한 번에 여러 파일에 빌드 작업을 설정할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- [빌드 작업(Windows의 Visual Studio)](/visualstudio/ide/build-actions)