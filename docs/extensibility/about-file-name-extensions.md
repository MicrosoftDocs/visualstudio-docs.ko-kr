---
title: 파일 이름 확장명 정보 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03e07ec233ef975441a1f10507f0db872051558f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740352"
---
# <a name="about-file-name-extensions"></a>파일 이름 확장명 정보
VSPackage의 파일 확장명을 등록 하는 경우이 파일을의 버전과 연결 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다. 이는 컴퓨터에 둘 이상의 버전이 설치 된 경우에 중요 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다.

 Vspackage에 대 한 파일 확장명은 연결 된 ProgID (프로그래밍 식별자)를 가리키는 기본값을 사용 하 여 **HKEY_CLASSES_ROOT** 키 아래에 등록 됩니다.

 다음 예제에서는 *.vcproj* 파일 확장명에 대 한 등록 정보를 보여 줍니다.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 와 연결 된 파일에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 는와 같은 버전이 지정 된 ProgID가 있어야 합니다 `VisualStudio.vcproj.8.0` . 버전 관리 ProgID를 사용 하면 제품의 병렬 설치를 통해 제품 버전 간에 파일 확장명 연결을 유지할 수 있습니다. 버전 관련 ProgID를 사용 하면 다른 응용 프로그램이 나 버전의에서 덮어쓰거나 덮어쓸 염려 없이 열기, 편집 등의 표준 동사를 사용할 수도 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 경우에 따라 파일 확장명에 연결 된 ProgID는 변경 하면 안 됩니다. 예를 들어 *.htm* 파일 확장명 (progid = htmlfile)에 대 한 ProgID는 운영 체제의 여러 위치에서 하드 코딩 되며 *.htm* 및 *.html* 파일과의 연결에서 널리 사용 되 고 사용 됩니다.

## <a name="see-also"></a>추가 정보
- [Side-by-side 배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [파일 이름 확장명에 대 한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
