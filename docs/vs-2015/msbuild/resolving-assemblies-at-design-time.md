---
title: 디자인 타임에 어셈블리 확인 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 920e7222b3b425cbb13c962ff8c2e1e2fc551bd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159236"
---
# <a name="resolving-assemblies-at-design-time"></a>디자인 타임에 어셈블리 확인
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참조 추가 대화 상자의 .NET 탭을 통해 어셈블리에 참조를 추가할 때, 참조는 중간 참조 어셈블리를 가리킵니다. 이 어셈블리는 모든 형식 및 시그니처 정보를 포함하지만 코드를 반드시 포함하지는 않습니다. .NET 탭에는 .NET Framework의 런타임 어셈블리에 해당하는 참조 어셈블리가 표시됩니다. 또한 타사에서 사용되는 등록된 AssemblyFoldersEx 폴더의 런타임 어셈블리에 해당하는 참조 어셈블리도 표시됩니다.  
  
## <a name="multi-targeting"></a>멀티 타기팅  
 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]를 사용하면 CLR(공용 언어 런타임) 버전 2.0 또는 버전 4에서 실행되는 .NET Framework의 버전을 대상으로 지정할 수 있습니다. 여기에는 .NET Framework 버전 2.0, 3.0, 3.5, 4, 4.5 및 4.5.1과 Silverlight 버전 1.0, 2.0 및 3.0이 포함됩니다. CLR 버전 2.0 또는 버전 4를 기준으로 하는 새 .NET Framework 버전이 릴리스되면 타기팅 팩을 사용하여 Framework를 설치할 수 있으며 설치된 후에는 자동으로 Visual Studio에서 대상으로 표시됩니다.  
  
## <a name="how-type-resolution-works"></a>형식 확인 작동 방식  
 런타임에 CLR은 GAC, bin 디렉터리 및 모든 검색 경로를 확인하여 어셈블리의 형식을 확인합니다. 이 작업은 Fusion 로더에 의해 처리됩니다. 그러나 Fusion 로더에서 어떤 항목을 찾고 있는지를 어떻게 알 수 있나요? 이것은 애플리케이션이 빌드되는 디자인 타임에 수행되는 확인에 따라 결정됩니다.  
  
 빌드 중에 컴파일러는 참조 어셈블리를 사용하여 애플리케이션 형식을 확인합니다. .NET Framework 버전 2.0, 3.0, 3.5, 4, 4.5 및 4.5.1에서 .NET Framework가 설치될 때 참조 어셈블리가 설치됩니다.  
  
 참조 어셈블리는 상응하는 버전의 .NET Framework SDK와 함께 제공되는 대상 지정 팩을 통해 제공됩니다. Framework는 자체적으로 런타임 어셈블리만 제공합니다. 애플리케이션을 빌드하기 위해서는 .NET Framework와 해당.NET Framework SDK를 모두 설치해야 합니다.  
  
 특정 .NET Framework를 대상으로 지정하면 빌드 시스템은 타기팅 팩의 참조 어셈블리를 사용하여 모든 형식을 확인합니다. 런타임에 Fusion 로더는 일반적으로 GAC에 있는 런타임 어셈블리에서도 이러한 동일한 형식을 확인합니다.  
  
 참조 어셈블리를 사용할 수 없으면 빌드 시스템은 런타임 어셈블리를 사용하여 어셈블리 형식을 확인합니다. GAC의 런타임 어셈블리는 부 버전 번호로 구분되지 않으므로 잘못된 어셈블리로 확인될 수 있습니다. 예를 들어 버전 3.0을 대상으로 지정했으나 .NET Framework 버전 3.5에 도입된 새 메서드가 참조되는 경우에 이러한 문제가 발생할 수 있습니다. 빌드가 성공하고 애플리케이션은 빌드 컴퓨터에서 실행되지만 버전 3.5가 설치되지 않은 컴퓨터로 배포하려고 하면 실패합니다.  
  
 이제 .NET Framework SDK가 포함된 타기팅 팩에는 해당 버전의 Framework에 있는 모든 런타임 어셈블리 목록(재배포 목록이라고도 함)이 포함됩니다. 따라서 빌드 시스템이 어셈블리의 잘못된 버전에 대해 형식을 확인할 가능성은 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [고급 개념](../msbuild/msbuild-advanced-concepts.md)
