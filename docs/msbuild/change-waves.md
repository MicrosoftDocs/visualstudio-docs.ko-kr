---
title: 변경 웨이브
description: 중단을 유발할 수 있는 MSBuild 기능을 활성화하거나 비활성화하는 방법을 알아봅니다.
ms.date: 11/10/2020
ms.topic: conceptual
helpviewer_keywords:
- Change waves [MSBuild]
- MSBuildDisableFeaturesFromVersion environment variable
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>=vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 77f93b4741ee987bac871e619ccbe58e2d4d4000
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939528"
---
# <a name="change-waves"></a>변경 웨이브

변경 웨이브는 특정 플래그를 환경 변수로 지정하여 옵트아웃할 수 있는 MSBuild 내 동작 변경 모음입니다. 이 기능의 목적은 중단을 유발할 수 있는 변경 사항을 경고하여 이러한 변경 사항이 표준 기능이 되기 전에 거부할 수 있도록 하는 것입니다. 특정 변경 웨이브의 기능은 모두 활성화하거나 비활성화해야 하며, 개별적으로 설정할 수는 없습니다.

새 버전의 MSBuild로 업그레이드하는 경우 중단을 유발할 수 있는 변경 사항은 기본적으로 활성화되지만, 기능이 빌드에 부정적인 영향을 준다면 관련 변경 사항을 쉽게 비활성화할 수 있습니다. 각 변경 웨이브는 MSBuild 버전 번호(예: 16.8)로 식별하지만, 변경 웨이브 설정은 관련 MSBuild 버전의 모든 변경 사항이 아닌 빌드 프로세스에 영향을 줄 수 있는 특정 기능만 제어합니다. 각 변경 웨이브의 기능 모음은 [이 문서 후반부](#change-waves-and-associated-features)에 나와 있습니다. 변경 웨이브를 비활성화하면 상위 버전의 변경 웨이브도 비활성화됩니다.

## <a name="opt-out-of-change-wave-features"></a>변경 웨이브 기능 옵트아웃

변경 웨이브의 기능을 비활성화하려면 환경 변수 `MSBuildDisableFeaturesFromVersion`을 **비활성화하려는** 기능이 포함된 변경 웨이브(또는 MSBuild 버전)로 설정합니다. 기능의 개발 목적이었던 MSBuild 버전을 말합니다. 변경 웨이브를 기능에 매핑하는 아래 예시를 참조하세요.

### <a name="msbuilddisablefeaturesfromversion-values"></a>MSBuildDisableFeaturesFromVersion 값

`MSBuildDisableFeaturesFromVersion`을 유효한 변경 웨이브로 설정하지 않으면 경고 메시지가 표시되거나 기본값이 특정 웨이브로 설정됩니다. 다음 표에는 가능한 설정이 나와 있습니다.

| `MSBuildDisableFeaturesFromVersion` 값                         | 결과        | 경고를 받을까요? |
| :-------------                                                    | :----------   | :----------: |
| 설정 해제                                                             | 모든 변경 웨이브를 활성화합니다. 즉 각 변경 웨이브의 모든 기능이 활성화됩니다.               | 아니요   |
| 유효한 모든 최신 변경 웨이브(예: `16.8`)                      | 변경 웨이브 `16.8` **이상의** 모든 기능을 비활성화합니다.                                           | 아니요   |
| 잘못된 값(예: 유효한 웨이브가 `16.8` 및 `16.10`일 때 `16.9`)| 가장 가까운 유효한 값(오름차순)이 기본값이 됩니다. 예를 들어 `16.9`로 설정하면 `16.10`이 기본값이 됩니다.               | 아니요   |
| 로테이션에서 벗어남(예: 최고 웨이브가 `17.0`일 때 `17.1`)      | 가장 가까운 유효 값으로 고정됩니다. 예를 들어 `17.1`은 `17.0`으로 고정되고 `16.5`는 `16.8`로 고정됩니다.                    | 예  |
| 잘못된 형식(예: `16x8`, `17_0`, `garbage`)                    | 모든 변경 웨이브를 활성화합니다. 즉 각 변경 웨이브의 모든 기능이 활성화됩니다.               | 예  |

## <a name="change-waves-and-associated-features"></a>변경 웨이브 및 관련 기능

아래 목록에 있는 링크를 누르면 기능에 대한 GitHub PR로 이동합니다.

### <a name="168"></a>16.8

- [NoWarn 활성화](https://github.com/dotnet/msbuild/pull/5671)
- [대상/작업 건너뛴 로그 메시지를 1,024자로 자르기](https://github.com/dotnet/msbuild/pull/5553)
- [False 조건으로 전체 드라이브 glob 확장하지 않음](https://github.com/dotnet/msbuild/pull/5669)

### <a name="1610"></a>16.10

- [조건의 속성 확장에 공백이 있으면 오류 발생](https://github.com/dotnet/msbuild/pull/5672)

### <a name="170"></a>17.0

이 변경 웨이브에 아직 항목이 없습니다.

## <a name="change-waves-that-are-out-of-rotation"></a>로테이션을 벗어난 변경 웨이브

지금은 로케이션을 벗어난 변경 웨이브가 없습니다.

## <a name="faq"></a>FAQ

**다른 모든 릴리스에서 변경 웨이브 로테이션 이탈을 추진하는 이유는 무엇입니까?**

Microsoft는 영향을 받는 대상과 논의하고 변경 사항을 적용하도록 도와야 하는 때가 바로 지금이라고 생각합니다.

**프로젝트 속성이 아닌 환경 변수인 이유는 무엇입니까?**

MSBuild에서 프로젝트를 로드하기 전에 변경 웨이브에 기능을 추가해야 하는 상황이 있습니다. 그래서 변경 웨이브는 환경 변수를 사용해야 합니다.

**옵트인이 아닌 옵트아웃인 이유는 무엇입니까?**

옵트아웃이 더 나은 방법입니다. 옵트아웃을 이용하지 않으면 기능이 고객 빌드에 영향을 줄 때 받는 피드백이 제한되기 때문입니다.

## <a name="see-also"></a>참조

- [MSBuild](msbuild.md)
- [MSBuild 16의 새로운 기능](whats-new-msbuild-16-0.md)
