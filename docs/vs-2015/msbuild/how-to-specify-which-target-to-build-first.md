---
title: '방법: 먼저 빌드할 대상 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d7d47746aed2e663eb1fa25e3bb9ca2c6bed2c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178333"
---
# <a name="how-to-specify-which-target-to-build-first"></a>방법: 먼저 빌드할 대상 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 파일에는 프로젝트 빌드 방식을 정의하는 하나 이상의 `Target` 요소가 포함됩니다. [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)]( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ) 엔진은 프로젝트 파일에 특성, 특성 또는 대상이 포함 된 경우를 제외 하 고, `DefaultTargets` `InitialTargets` **/target** 스위치를 사용 하 여 명령줄에 지정 되는 첫 번째 프로젝트와 모든 종속성을 빌드합니다.  
  
## <a name="using-the-initialtargets-attribute"></a>InitialTargets 특성 사용  
 대상이 명령줄 또는 `DefaultTargets` 특성에서 지정된 경우에도 `Project` 요소의 `InitialTargets` 특성은 먼저 실행할 대상을 지정합니다.  
  
#### <a name="to-specify-one-initial-target"></a>하나의 초기 대상을 지정합니다.  
  
- `Project` 요소의 `InitialTargets` 특성에서 기본 대상을 지정합니다. 예를 들어:  
  
   `<Project InitialTargets="Clean">`  
  
  대상을 순서대로 나열하고 각 대상으로 세미콜론으로 구분하여 `InitialTargets` 특성에서 두 개 이상의 초기 대상을 지정할 수 있습니다. 목록의 대상은 순차적으로 실행됩니다.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>두 개 이상의 초기 대상을 지정하려면  
  
- `Project` 요소의 `InitialTargets` 특성에서 세미콜론으로 구분된 초기 대상을 나열합니다. 예를 들어 `Clean` 대상 및 `Compile` 대상을 차례로 실행하려면 다음을 실행합니다.  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>DefaultTargets 특성 사용  
 `Project` 요소의 `DefaultTargets` 특성은 대상이 명령줄에서 명시적으로 지정되지 않은 경우 빌드되는 하나 이상의 대상을 지정합니다. 대상이 `InitialTargets` 및 `DefaultTargets` 특성에서 둘 다 지정되고 대상이 명령줄에서 지정되지 않은 경우 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 `InitialTargets` 특성에 지정된 대상을 실행하고 나서 `DefaultTargets` 특성에 지정된 대상을 실행합니다.  
  
#### <a name="to-specify-one-default-target"></a>하나의 기본 대상을 지정하려면  
  
- `Project` 요소의 `DefaultTargets` 특성에서 기본 대상을 지정합니다. 예를 들어:  
  
   `<Project DefaultTargets="Compile">`  
  
  대상을 순서대로 나열하고 각 대상으로 세미콜론으로 구분하여 `DefaultTargets` 특성에서 두 개 이상의 기본 대상을 지정할 수 있습니다. 목록의 대상은 순차적으로 실행됩니다.  
  
#### <a name="to-specify-more-than-one-default-target"></a>두 개 이상의 기본 대상을 지정하려면  
  
- `Project` 요소의 `DefaultTargets` 특성에서 세미콜론으로 구분된 기본 대상을 나열합니다. 예를 들어 `Clean` 대상 및 `Compile` 대상을 차례로 실행하려면 다음을 실행합니다.  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>/target 스위치 사용  
 기본 대상이 프로젝트 파일에 정의 되어 있지 않거나 해당 기본 대상을 사용 하지 않으려는 경우 명령줄 스위치 **/target** 을 사용 하 여 다른 대상을 지정할 수 있습니다. **/Target** 스위치를 사용 하 여 지정 된 대상이 특성으로 지정 된 대상 대신 실행 됩니다 `DefaultTargets` . `InitialTargets` 특성에 지정된 대상이 항상 먼저 실행됩니다.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>기본 대상 이외의 대상을 먼저 사용하려면  
  
- **/Target** 명령줄 스위치를 사용 하 여 대상을 첫 번째 대상으로 지정 합니다. 예를 들어:  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>기본 대상 이외의 여러 대상을 먼저 사용하려면  
  
- **/Target** 명령줄 스위치를 사용 하 여 세미콜론 또는 쉼표로 구분 된 대상을 나열 합니다. 예를 들어:  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>참고 항목
  [MSBuild](msbuild.md)  
 [대상](../msbuild/msbuild-targets.md)   
 [방법: 빌드 정리](../msbuild/how-to-clean-a-build.md)
