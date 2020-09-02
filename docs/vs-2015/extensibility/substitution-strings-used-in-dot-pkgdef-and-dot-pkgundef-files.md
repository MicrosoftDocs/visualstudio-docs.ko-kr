---
title: 에서 사용 되는 대체 문자열입니다. .Pkgdef 및입니다. .Pkgundef 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgdef and .pkgundef files
ms.assetid: b1755d63-d794-4fd7-864b-70a9684881c2
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 47434d9d1dfcedeeaea330b1d65645d7a632c6e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160540"
---
# <a name="substitution-strings-used-in-pkgdef-and-pkgundef-files"></a>.Pkgdef 및 .Pkgundef 파일에 사용되는 대체 문자열
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 격리 셸 응용 프로그램에 대해 정의 하는 .pkgdef 및. .pkgundef 파일에 아래에 나열 된 대체 문자열을 사용할 수 있습니다.  
  
## <a name="substitution-strings"></a>대체 문자열  
  
|String|설명|  
|------------|-----------------|  
|$=*RegistryEntry*$|*RegistryEntry* 항목의 값입니다. 레지스트리 항목 문자열이 백슬래시 ()로 끝나는 경우 \\ 레지스트리 하위 키의 기본값이 사용 됩니다. 예를 들어 대체 문자열 $ = HKEY_CURRENT_USER \Environment\TEMP $는 현재 사용자의 임시 폴더로 확장 됩니다.|  
|$AppName $|AppEnv.dll 진입점에 전달 되는 응용 프로그램의 정규화 된 이름입니다. 정규화 된 이름은 응용 프로그램 이름, 밑줄 및 응용 프로그램 자동화 개체의 CLSID (클래스 식별자)로 구성 되며, .pkgdef 파일의 ThisVersionDTECLSID 설정 값으로도 기록 됩니다.|  
|$AppDataLocalFolder|이 응용 프로그램에 대 한% LOCALAPPDATA% 아래의 하위 폴더입니다.|  
|$BaseInstallDir $|Visual Studio가 설치 된 위치의 전체 경로입니다.|  
|$CommonFiles $|% CommonProgramFiles% 환경 변수의 값입니다.|  
|$MyDocuments $|현재 사용자의 내 문서 폴더에 대 한 전체 경로입니다.|  
|$PackageFolder $|응용 프로그램의 패키지 어셈블리 파일이 포함 된 디렉터리의 전체 경로입니다.|  
|$ProgramFiles $|% ProgramFiles% 환경 변수의 값입니다.|  
|$RootFolder $|응용 프로그램의 루트 디렉터리에 대 한 전체 경로입니다.|  
|$RootKey $|응용 프로그램의 루트 레지스트리 키입니다. 기본적으로 루트는 HKEY_CURRENT_USER \software \\ *CompanyName* \\ *ProjectName* \\ *VersionNumber* 에 있습니다 (응용 프로그램을 실행 하는 경우 _Config이 키에 추가 됨). *SolutionName*.pkgdef 파일의 RegistryRoot 값으로 설정 됩니다.<br /><br /> $RootKey $ 문자열은 application 하위 키 아래에 레지스트리 값을 검색 하는 데 사용할 수 있습니다. 예를 들어 "$ = $RootKey $ \AppIcon $" 문자열은 응용 프로그램 루트 하위 키 아래에 있는 AppIcon 항목의 값을 반환 합니다.<br /><br /> 파서는 .pkgdef 파일을 순차적으로 처리 하 고 항목이 이전에 정의 된 경우에만 application 하위 키 아래에 있는 레지스트리 항목에 액세스할 수 있습니다.|  
|$ShellFolder $|Visual Studio가 설치 된 위치의 전체 경로입니다.|  
|$System $|Windows\system32 폴더입니다.|  
|$WINDIR $|Windows 폴더입니다.|  
  
 파서가 대체 문자열을 인식 하지 못하거나 레지스트리 항목 또는 환경 변수의 값을 확인할 수 없는 경우 문자열의 해당 부분에서 대체를 수행 하지 않습니다.
