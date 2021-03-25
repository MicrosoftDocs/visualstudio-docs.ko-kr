---
title: 파일 이름 확장명 정보 | Microsoft Docs
description: Vspackage에 대 한 파일 이름 확장명을 등록 하 고 특정 버전의 Visual Studio와 연결 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f38bee1b62340f7d557ac2e5190fc5c48d9268fe
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060148"
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

## <a name="see-also"></a>참조
- [Side-by-side 배포에 대 한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [파일 이름 확장명에 대 한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
