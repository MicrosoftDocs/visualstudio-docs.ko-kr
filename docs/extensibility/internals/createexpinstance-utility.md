---
title: 생성ExpInstance 유틸리티 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709235"
---
# <a name="createexpinstance-utility"></a>만들기ExpInstance 유틸리티
**CreateExpInstance** 유틸리티를 사용하여 Visual Studio의 실험 인스턴스를 생성, 재설정 또는 삭제합니다. 실험 인스턴스를 사용하여 기본 제품을 변경하지 않고 Visual Studio 확장을 디버깅하고 테스트할 수 있습니다.

## <a name="syntax"></a>구문

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>매개 변수
 **/만들기** 실험 인스턴스를 만듭니다.

 **/재설정** 실험 인스턴스를 삭제한 다음 새 인스턴스를 만듭니다.

 **/클린** 실험 인스턴스를 삭제합니다.

 **/VS인스턴스** 복사할 기본 Visual Studio 인스턴스를 포함하는 디렉터리 이름입니다.

 **/RootSuffix** 실험 인스턴스 디렉터리 이름을 더할 접미사입니다.

## <a name="remarks"></a>설명
 Visual Studio 확장에서 작업하는 경우 F5를 눌러 기본 실험 인스턴스를 열고 현재 확장을 설치할 수 있습니다. 사용 가능한 실험 인스턴스가 없는 경우 Visual Studio는 기본 설정이 있는 인스턴스를 만듭니다.

 실험 인스턴스의 기본 위치는 Visual Studio 버전 번호에 따라 다릅니다. 예를 들어 Visual Studio 2015의 위치는 *\\%localappdata%\Microsoft\VisualStudio\14.0Exp입니다.* 디렉터리 위치의 모든 파일은 해당 인스턴스의 일부로 간주됩니다. 디렉터리 이름이 기본 위치로 변경되지 않는 한 추가 실험 인스턴스는 Visual Studio에서 로드되지 않습니다.

 Visual Studio는 실험 인스턴스를 열 때 시스템 레지스트리에 액세스하지 않습니다. 이는 레지스트리 하이브의 실험 버전을 사용한 이전 버전의 Visual Studio와 다릅니다.

 **CreateExpInstance** 유틸리티는 **VsRegEx** 유틸리티를 대체합니다.

 다음 예제에서는 Visual Studio의 기본 실험 인스턴스를 다시 설정합니다.

 **CreateExpInstance.exe /재설정/VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>참조
- [VSPackage](../../extensibility/internals/vspackages.md)
