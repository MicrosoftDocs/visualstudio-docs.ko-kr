---
title: 파일 이름 확장명 정보 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148028"
---
# <a name="about-file-name-extensions"></a>파일 확장명 정보
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage의 파일 확장명을 등록 하는 경우이 파일을의 버전과 연결 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다. 이는 컴퓨터에 둘 이상의 버전이 설치 된 경우에 중요 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다.  
  
 Vspackage에 대 한 파일 확장명은 연결 된 ProgID (프로그래밍 식별자)를 가리키는 기본값을 사용 하 여 HKEY_CLASSES_ROOT 키 아래에 등록 됩니다.  
  
 다음은 .vcproj 파일 확장명에 대 한 등록 정보의 예입니다.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 와 연결 된 파일에는 제품 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 병렬 설치를 `VisualStudio.vcproj.8.0` 통해 제품 버전 간에 파일 확장명 연결을 유지 관리할 수 있도록 버전 관리 ProgID (예:)가 있어야 합니다. 버전 관련 ProgID를 사용 하면 다른 응용 프로그램이 나 버전의에서 덮어쓰거나 덮어쓸 염려 없이 열기, 편집 등의 표준 동사를 사용할 수도 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 경우에 따라 파일 확장명에 연결 된 ProgID는 변경 하면 안 됩니다. 예를 들어 .htm 파일 확장명에 대 한 ProgID (progid = htmlfile)는 운영 체제의 여러 위치에서 하드 코드 되며 .htm 및 .html 파일과의 연결에서 널리 사용 되 고 사용 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [Side-by-side 배포를 위한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [파일 이름 확장명에 대한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
