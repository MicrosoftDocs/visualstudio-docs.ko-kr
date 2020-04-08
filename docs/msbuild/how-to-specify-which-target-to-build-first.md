---
title: '방법: 먼저 빌드할 대상 지정 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c679b2a43ec799035f9bafb6a03a546808498342
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543982"
---
# <a name="how-to-specify-which-target-to-build-first"></a>방법: 먼저 빌드할 대상 지정

프로젝트 파일에는 프로젝트 빌드 방식을 정의하는 하나 이상의 `Target` 요소가 포함됩니다. 프로젝트 파일에 `DefaultTargets` 특성, `InitialTargets` 특성이 포함되거나 대상이 명령줄에서 **-target** 스위치를 사용하여 지정된 경우가 아니면 MSBuild(Microsoft Build Engine) 엔진은 발견한 첫 번째 프로젝트 및 모든 종속성을 빌드합니다.
## <a name="use-the-initialtargets-attribute"></a>InitialTargets 특성 사용

대상이 명령줄 또는 `DefaultTargets` 특성에서 지정된 경우에도 `Project` 요소의 `InitialTargets` 특성은 먼저 실행할 대상을 지정합니다.

#### <a name="to-specify-one-initial-target"></a>하나의 초기 대상을 지정합니다.

- `Project` 요소의 `InitialTargets` 특성에서 기본 대상을 지정합니다. 예를 들어:

   `<Project InitialTargets="Clean">`

  대상을 순서대로 나열하고 각 대상으로 세미콜론으로 구분하여 `InitialTargets` 특성에서 두 개 이상의 초기 대상을 지정할 수 있습니다. 목록의 대상은 순차적으로 실행됩니다.

#### <a name="to-specify-more-than-one-initial-target"></a>두 개 이상의 초기 대상을 지정하려면

- `Project` 요소의 `InitialTargets` 특성에서 세미콜론으로 구분된 초기 대상을 나열합니다. 예를 들어 `Clean` 대상 및 `Compile` 대상을 차례로 실행하려면 다음을 실행합니다.

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>DefaultTargets 특성 사용

 `Project` 요소의 `DefaultTargets` 특성은 대상이 명령줄에서 명시적으로 지정되지 않은 경우 빌드되는 하나 이상의 대상을 지정합니다. 대상이 `InitialTargets` 특성과 `DefaultTargets` 특성에서 모두 지정되고 대상이 명령줄에서 지정되지 않은 경우 MSBuild는 `InitialTargets` 특성에 지정된 대상을 실행하고 나서 `DefaultTargets` 특성에 지정된 대상을 실행합니다.

#### <a name="to-specify-one-default-target"></a>하나의 기본 대상을 지정하려면

- `Project` 요소의 `DefaultTargets` 특성에서 기본 대상을 지정합니다. 예를 들어:

   `<Project DefaultTargets="Compile">`

  대상을 순서대로 나열하고 각 대상으로 세미콜론으로 구분하여 `DefaultTargets` 특성에서 두 개 이상의 기본 대상을 지정할 수 있습니다. 목록의 대상은 순차적으로 실행됩니다.

#### <a name="to-specify-more-than-one-default-target"></a>두 개 이상의 기본 대상을 지정하려면

- `Project` 요소의 `DefaultTargets` 특성에서 세미콜론으로 구분된 기본 대상을 나열합니다. 예를 들어 `Clean` 대상 및 `Compile` 대상을 차례로 실행하려면 다음을 실행합니다.

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>-target 스위치 사용

 기본 대상이 프로젝트 파일에 정의되어 있지 않거나 기본 대상을 사용하지 않으려는 경우 명령줄 스위치 **-target**을 사용하여 다른 대상을 지정할 수 있습니다. `DefaultTargets` 특성으로 지정된 대상 대신 **-target** 스위치를 사용하여 지정된 하나 이상의 대상이 실행됩니다. `InitialTargets` 특성에 지정된 대상이 항상 먼저 실행됩니다.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>기본 대상 이외의 대상을 먼저 사용하려면

- **-target** 명령줄 스위치를 사용하여 대상을 첫 번째 대상으로 지정합니다. 예를 들어:

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>기본 대상 이외의 여러 대상을 먼저 사용하려면

- **-target** 명령줄 스위치를 사용하여 세미콜론 또는 쉼표로 구분된 대상을 나열합니다. 예를 들어:

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>참조

- [MSBuild](../msbuild/msbuild.md)
- [대상](../msbuild/msbuild-targets.md)
- [방법: 빌드 정리](../msbuild/how-to-clean-a-build.md)
