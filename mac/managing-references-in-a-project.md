---
title: 프로젝트에서 참조 관리
description: 이 문서에서는 Mac용 Visual Studio의 프로젝트에서 참조를 관리하는 방법에 대해 설명합니다.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.topic: overview
ms.openlocfilehash: 28ea53826a19a9ec97349060702cf13c68342ad2
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939001"
---
# <a name="managing-references-in-a-project"></a>프로젝트에서 참조 관리

Mac용 Visual Studio에서는 프로젝트에 참조를 추가하기 위한 두 가지 방법을 제공합니다.

![프로젝트 참조](media/projects-and-solutions-image10.png)

이러한 방법은 다음과 같습니다.

* 참조 항목
* NuGets(패키지 폴더를 통해 추가)

또한 모든 프로젝트에 웹 참조 및 네이티브 참조를 추가할 수 있습니다.

## <a name="assembly-references"></a>어셈블리 참조

Xamarin 내의 각 프레임워크는 여러 어셈블리와 함께 제공됩니다. 이러한 어셈블리 패키지 중 일부만 프로젝트에서 기본적으로 참조됩니다.

프로젝트에서 참조한 패키지를 편집하려면 **참조 편집** 대화 상자를 사용하세요. 이 대화 상자는 [참조] 폴더를 두 번 클릭하거나 상황에 맞는 메뉴 작업에서 **참조 편집**을 선택하면 표시됩니다.

![어셈블리 참조 대화 상자](media/projects-and-solutions-image11.png)

각 Xamarin 프레임워크에 사용할 수 있는 어셈블리에 대한 자세한 내용은 [Available Assemblies](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/)(사용할 수 있는 어셈블리) 가이드를 참조하세요.

## <a name="nuget"></a>NuGet

NuGet은 가장 인기 있는 .NET 개발용 패키지 관리자입니다. Mac용 Visual Studio의 NuGet 지원을 사용하면 패키지를 검색하여 프로젝트에 추가할 수 있습니다.

이렇게 하려면 Solution Pad의 **패키지** 폴더를 마우스 오른쪽 단추로 클릭한 다음 [패키지 추가]를 선택하세요.

NuGet 패키지를 사용하는 방법에 대한 자세한 내용은 [프로젝트에 NuGet 패키지 포함하기](nuget-walkthrough.md) 연습에서 제공합니다.

## <a name="see-also"></a>참조

- [참조 관리(Windows의 Visual Studio)](/visualstudio/ide/managing-references-in-a-project)
- [NuGet을 사용한 참조 추가 및 확장 SDK를 사용한 참조 추가(Windows의 Visual Studio)](/visualstudio/ide/adding-references-using-nuget-versus-an-extension-sdk)