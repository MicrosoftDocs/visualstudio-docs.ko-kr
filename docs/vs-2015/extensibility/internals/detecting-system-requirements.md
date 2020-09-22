---
title: 시스템 요구 사항 검색 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841490"
---
# <a name="detecting-system-requirements"></a>시스템 요구 사항 검색
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio가 설치 되어 있지 않으면 VSPackage를 사용할 수 없습니다. Microsoft Windows Installer를 사용 하 여 VSPackage 설치를 관리 하는 경우 Visual Studio가 설치 되어 있는지 여부를 검색 하도록 설치 관리자를 구성할 수 있습니다. 또한 특정 버전의 Windows 또는 특정 RAM과 같은 다른 요구 사항이 있는지 시스템을 검사 하도록 구성할 수 있습니다.  
  
## <a name="detecting-visual-studio-editions"></a>Visual Studio 버전 검색  
 Visual Studio 버전이 설치 되어 있는지 확인 하려면 다음 표에 나열 된 것과 같이 해당 폴더에서 Install 레지스트리 키의 값이 (REG_DWORD) 1 인지 확인 합니다. Visual Studio 버전의 계층 구조는 다음과 같습니다.  
  
1. Enterprise  
  
2. Professional  
  
3. 커뮤니티  
  
   "상위" 버전이 설치 되어 있는 경우 해당 버전에 대 한 레지스트리 키와 "하위" 버전을 추가 합니다. 즉, Enterprise edition이 설치 되어 있는 경우에는 설치 키가 Enterprise의 경우 1로, Professional 및 Community 버전의 경우 1로 설정 됩니다. 따라서 필요한 "최고" 버전만 확인 하면 됩니다.  
  
> [!NOTE]
> 64 비트 버전의 레지스트리 편집기에서 32 비트 키는 HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node 아래에 표시 됩니다 \\ . Visual Studio 키는 HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing 아래에 \\ 있습니다.  
  
|제품|키|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (통합 및 격리)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Visual Studio가 실행 되는 경우 검색  
 VSPackage가 설치 될 때 Visual Studio가 실행 중인 경우 VSPackage를 올바르게 등록할 수 없습니다. 설치 관리자에서 Visual Studio가 실행 중일 때를 검색 한 다음 프로그램 설치를 거부 해야 합니다. Windows Installer 테이블 항목을 사용 하 여 이러한 검색을 사용 하도록 설정할 수 없습니다. 대신, 다음과 같이 사용자 지정 작업을 만들어야 합니다. 함수를 사용 `EnumProcesses` 하 여 devenv.exe 프로세스를 검색 한 다음 시작 조건에 사용 되는 설치 관리자 속성을 설정 하거나 사용자에 게 Visual Studio를 닫으라는 메시지를 표시 하는 대화 상자를 조건부로 표시 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Windows Installer를 사용하여 VSPackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
