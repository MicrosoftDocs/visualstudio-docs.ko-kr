---
title: CreateExpInstance 유틸리티 | Microsoft Docs
description: Visual Studio 실험적 인스턴스를 만들거나, 다시 설정하거나, 삭제할 수 있는 CreateExpInstance 유틸리티에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cce9bc25cb2ed820d3291ab65d94a868bb401ec9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898138"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 유틸리티
**CreateExpInstance** 유틸리티를 사용하여 Visual Studio 실험적 인스턴스를 만들거나, 다시 설정하거나, 삭제할 수 있습니다. 기본 제품을 변경하지 않고 실험적 인스턴스를 사용하여 Visual Studio 확장을 디버그하고 테스트할 수 있습니다.

## <a name="syntax"></a>구문

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>매개 변수
 **/Create** 실험적 인스턴스를 만듭니다.

 **/Reset** 실험적 인스턴스를 삭제한 다음 새 인스턴스를 만듭니다.

 **/Clean** 실험적 인스턴스를 삭제합니다.

 **/VSInstance** 복사할 기본 Visual Studio 인스턴스를 포함하는 디렉터리 이름입니다.

 **/RootSuffix** 실험적 인스턴스 디렉터리의 이름에 추가해야 하는 접미사입니다.

## <a name="remarks"></a>설명
 Visual Studio 확장에서 작업하는 경우 F5 키를 눌러 기본 실험적 인스턴스를 열고 현재 확장을 설치할 수 있습니다. 사용할 수 있는 실험적 인스턴스가 없는 경우 Visual Studio 기본 설정이 있는 인스턴스를 만듭니다.

 실험적 인스턴스의 기본 위치는 Visual Studio 버전 번호에 따라 달라집니다. 예를 들어 Visual Studio 2015의 경우 위치는 *%localappdata%\Microsoft\VisualStudio\14.0Exp \\* 입니다. 디렉터리 위치의 모든 파일은 해당 인스턴스의 일부로 간주됩니다. 디렉터리 이름이 기본 위치로 변경되지 않으면 추가 실험적 인스턴스는 Visual Studio 로드되지 않습니다.

 Visual Studio 실험적 인스턴스를 열 때 시스템 레지스트리에 액세스하지 않습니다. 이는 레지스트리 하이브의 실험적 버전을 사용한 이전 버전의 Visual Studio 다릅니다.

 **CreateExpInstance** 유틸리티는 **VsRegEx** 유틸리티를 대체합니다.

 다음 예제에서는 Visual Studio 기본 실험적 인스턴스를 다시 설정합니다.

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>참조
- [VSPackages](../../extensibility/internals/vspackages.md)
