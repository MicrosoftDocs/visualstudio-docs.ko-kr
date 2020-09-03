---
title: CreateExpInstance 유틸리티 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d778f0f31a7651412915a898bff9e4bdfe6c55f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196985"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance 유틸리티
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

CreateExpInstance 유틸리티를 사용 하 여 Visual Studio의 실험적 인스턴스를 만들거나, 다시 설정 하거나, 삭제할 수 있습니다. 실험적 인스턴스를 사용 하 여 기본 제품을 변경 하지 않고 Visual Studio 확장을 디버그 하 고 테스트할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>매개 변수  
 /Create  
 실험적 인스턴스를 만듭니다.  
  
 /Reset  
 실험적 인스턴스를 삭제 한 다음 새 인스턴스를 만듭니다.  
  
 /Clean  
 실험적 인스턴스를 삭제 합니다.  
  
 /VSInstance  
 복사할 기본 Visual Studio 인스턴스를 포함 하는 디렉터리의 이름입니다.  
  
 /RootSuffix  
 실험적 인스턴스 디렉터리의 이름에 추가할 접미사입니다.  
  
## <a name="remarks"></a>설명  
 Visual Studio 확장에서 작업 하는 경우 F5 키를 눌러 기본 실험적 인스턴스를 열고 현재 확장을 설치할 수 있습니다. 실험적 인스턴스를 사용할 수 없는 경우 Visual Studio에서 기본 설정을 포함 하는 인스턴스를 만듭니다.  
  
 실험적 인스턴스의 기본 위치는 Visual Studio 버전 번호에 따라 다릅니다. 예를 들어 Visual Studio 2015의 경우 디렉터리 위치의 모든 파일이 해당 인스턴스의 일부로 간주 되 는%localappdata%\Microsoft\VisualStudio\14.0Exp\ 위치입니다. 디렉터리 이름이 기본 위치로 변경 되지 않는 한 모든 추가 실험적 인스턴스는 Visual Studio에서 로드 되지 않습니다.  
  
 Visual Studio는 실험적 인스턴스를 열 때 시스템 레지스트리에 액세스 하지 않습니다. 이는 실험적 버전의 레지스트리 hive를 사용 하는 이전 버전의 Visual Studio와는 다릅니다.  
  
 CreateExpInstance 유틸리티는 VsRegEx 유틸리티를 대체 합니다.  
  
 다음 예에서는 Visual Studio의 기본 실험적 인스턴스를 다시 설정 합니다.  
  
 **CreateExpInstance.exe/Reset/VSInstance = 14.0/Vsinstance = Exp**  
  
## <a name="see-also"></a>관련 항목  
 [제품 릴리스](../../misc/releasing-a-visual-studio-integration-product.md)
