---
title: CreatePkgDef 유틸리티 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841407"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 유틸리티
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 확장에 대 한 .dll 파일을 매개 변수로 사용 하 고 .dll과 함께 .pkgdef 파일을 만듭니다. .Pkgdef 파일은 확장이 설치 될 때 시스템 레지스트리에 기록 될 모든 정보를 포함 합니다.  
  
> [!NOTE]
> Visual Studio SDK에 포함 된 대부분의 프로젝트 템플릿은 빌드 프로세스의 일부로 .pkgdef 파일을 자동으로 만듭니다. 이 문서는 수동으로 패키지를 만들거나 기존 패키지를 .pkgdef 배포를 사용 하도록 변환 하려는 사용자를 위한 것입니다.  
  
## <a name="syntax"></a>구문  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>인수  
 /out =`FileName`  
 필수 요소. .Pkgdef 출력 파일의 `FileName` 이름을로 설정 합니다.  
  
 /codebase  
 선택 사항입니다. 코드 베이스 유틸리티를 사용 하 여 등록을 강제 합니다.  
  
 /assembly  
 어셈블리 유틸리티를 사용 하 여 등록을 강제 합니다.  
  
 `AssemblyPath`  
 .Pkgdef를 생성 하려는 .dll 파일의 경로입니다.  
  
## <a name="remarks"></a>설명  
 .Pkgdef 파일을 사용 하 여 확장 배포는 이전 버전의 Visual Studio에 대 한 레지스트리 요구 사항을 대체 합니다.  
  
 .Pkgdef 파일 은%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ 또는%vsinstalldir%\Common7\IDE\Extensions 위치 중 하나에 설치 해야 \\ 합니다. 설치 폴더가%localappdata%\Microsoft\Visual Studio\14.0\Extensions 이면 \\ Visual Studio에서 확장을 인식 하지만 기본적으로 사용 하지 않도록 설정 됩니다. 사용자는 확장 **및 업데이트**를 사용 하 여 확장을 사용 하도록 설정할 수 있습니다. 설치 폴더가%vsinstalldir%\Common7\IDE\Extensions 인 경우 \\ 확장은 기본적으로 사용 하도록 설정 됩니다.  
  
> [!NOTE]
> 확장 **및 업데이트** 도구는 VSIX 패키지의 일부로 설치 되지 않은 경우 확장에 액세스 하는 데 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [CreateExpInstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)
