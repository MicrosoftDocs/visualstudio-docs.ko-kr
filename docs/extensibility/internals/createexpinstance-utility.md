---
title: CreateExpInstance 유틸리티 | Microsoft Docs
description: Visual Studio의 실험적 인스턴스를 만들거나, 다시 설정 하거나, 삭제할 수 있는 CreateExpInstance 유틸리티에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: d0010c4a98d0ea50ec7feb2f7a379f3c84bc3d53
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056989"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 유틸리티
**Createexpinstance** 유틸리티를 사용 하 여 Visual Studio의 실험적 인스턴스를 만들거나, 다시 설정 하거나, 삭제할 수 있습니다. 실험적 인스턴스를 사용 하 여 기본 제품을 변경 하지 않고 Visual Studio 확장을 디버그 하 고 테스트할 수 있습니다.

## <a name="syntax"></a>구문

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>매개 변수
 **/Create** 실험적 인스턴스를 만듭니다.

 **/Reset** 실험적 인스턴스를 삭제 한 다음 새 인스턴스를 만듭니다.

 **/Clean** 실험적 인스턴스를 삭제 합니다.

 **/Vsinstance** 복사할 기본 Visual Studio 인스턴스를 포함 하는 디렉터리의 이름입니다.

 **/Rootsuffix** 실험적 인스턴스 디렉터리의 이름에 추가할 접미사입니다.

## <a name="remarks"></a>설명
 Visual Studio 확장에서 작업 하는 경우 F5 키를 눌러 기본 실험적 인스턴스를 열고 현재 확장을 설치할 수 있습니다. 실험적 인스턴스를 사용할 수 없는 경우 Visual Studio에서 기본 설정을 포함 하는 인스턴스를 만듭니다.

 실험적 인스턴스의 기본 위치는 Visual Studio 버전 번호에 따라 다릅니다. 예를 들어 Visual Studio 2015의 경우 위치는 *%localappdata%\Microsoft\VisualStudio\14.0Exp \\* 입니다. 디렉터리 위치의 모든 파일은 해당 인스턴스의 일부로 간주 됩니다. 디렉터리 이름이 기본 위치로 변경 되지 않는 한 모든 추가 실험적 인스턴스는 Visual Studio에서 로드 되지 않습니다.

 Visual Studio는 실험적 인스턴스를 열 때 시스템 레지스트리에 액세스 하지 않습니다. 이는 실험적 버전의 레지스트리 hive를 사용 하는 이전 버전의 Visual Studio와는 다릅니다.

 **Createexpinstance** 유틸리티는 **vsregex** 유틸리티를 대체 합니다.

 다음 예제에서는 Visual Studio의 기본 실험적 인스턴스를 다시 설정 합니다.

 **CreateExpInstance.exe/Reset/VSInstance = 14.0/Vsinstance = Exp**

## <a name="see-also"></a>참조
- [VSPackages](../../extensibility/internals/vspackages.md)
