---
title: 파일 이름 확장자 소개 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740352"
---
# <a name="about-file-name-extensions"></a>파일 이름 확장명 에 대해
VSPackage의 파일 확장자를 등록할 때 의 버전과 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]연결합니다. 이는 컴퓨터에 두 개 이상의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 버전이 설치된 경우 중요합니다.

 VSPackage용 파일 확장자는 연결된 프로그래밍 HKEY_CLASSES_ROOT 식별자(ProgID)를 가리키는 기본값을 가진 **HKEY_CLASSES_ROOT** 키 아래에 등록됩니다.

 다음 예제에서는 *.vcproj* 파일 확장자의 등록 정보를 보여 주며 있습니다.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)=" VisualStudio.vcproj.8.0"
```

 연결된 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 파일에는 와 같은 `VisualStudio.vcproj.8.0`버전이 있는 ProgID가 있어야 합니다. 버전이 지정된 ProgID를 사용하면 제품을 나란히 설치하여 제품 버전 간에 파일 확장자 연결을 유지할 수 있습니다. 버전별 ProgID를 사용하면 다른 응용 프로그램이나 버전에서 덮어쓰거나 덮어쓰는 등의 걱정 없이 열기, 편집 등과 같은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]표준 동사를 사용할 수 있습니다.

 경우에 따라 파일 확장과 연결된 ProgID를 변경하면 안 됩니다. 예를 들어 *.htm* 파일 확장자(progid = htmlfile)에 대한 ProgID는 운영 체제의 여러 위치에서 하드 코딩되며 *.htm* 및 *.html* 파일과 관련하여 널리 알려져 있으며 사용됩니다.

## <a name="see-also"></a>참조
- [나란히 배포할 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [파일 이름 확장명에 대한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
