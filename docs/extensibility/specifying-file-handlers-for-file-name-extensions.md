---
title: 파일 이름 확장명에 대 한 파일 처리기 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af195aea09c91696843c6be42c20053bb8c095a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699748"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>파일 이름 확장명에 대한 파일 처리기 지정
특정 파일 확장명이 있는 파일을 처리 하는 응용 프로그램을 확인 하는 방법에는 여러 가지가 있습니다. OpenWithList 및 Openwithlist 동사는 파일 확장명에 대 한 레지스트리 항목에서 파일 처리기를 지정 하는 두 가지 방법입니다.

## <a name="openwithlist-verb"></a>OpenWithList 동사
 Windows 탐색기에서 파일을 마우스 오른쪽 단추로 클릭 하면 **열기** 명령이 표시 됩니다. 둘 이상의 제품이 확장과 연결 된 **경우 연결 프로그램 하위 메뉴가** 표시 됩니다.

 HKEY_CLASSES_ROOT에서 파일 확장명에 대 한 OpenWithList 키를 설정 하 여 다른 응용 프로그램을 등록 하 여 확장을 열 수 있습니다. 파일 확장명에 대 한이 키 아래에 나열 된 응용 프로그램은 **연결** 프로그램 대화 상자의 **권장 프로그램** 제목 아래에 나타납니다. 다음 예제에서는 .vcproj 파일 확장명을 열기 위해 등록 된 응용 프로그램을 보여 줍니다.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> 응용 프로그램을 지정 하는 키는 HKEY_CLASSES_ROOT \Applications>의 목록에 있습니다.

 OpenWithList 키를 추가 하 여 다른 응용 프로그램이 확장의 소유권을 갖는 경우에도 응용 프로그램에서 파일 확장명을 지원함을 선언 합니다. 이는 응용 프로그램 또는 다른 응용 프로그램의 이후 버전이 될 수 있습니다.

## <a name="openwithprogids"></a>OpenWithProgIDs
 Progid (프로그래밍 식별자)는 응용 프로그램 또는 COM 개체의 버전을 식별 하는 Classid의 친숙 한 버전입니다. 모든 공동 생성 가능 개체에는 자체 ProgID가 있어야 합니다. 예를 들어 VisualStudio는 VisualStudio를 시작 하는 동안 Visual Studio .NET 2003를 시작 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다. 프로젝트 형식 또는 프로젝트 항목 형식의 소유자는 파일 확장명에 대 한 버전별 ProgID를 만들어야 합니다. 둘 이상의 ProgID가 동일한 응용 프로그램을 시작할 수 있다는 것은 이러한 Progid가 중복 될 수 있습니다. 자세한 내용은 [파일 이름 확장명에 대 한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)을 참조 하세요.

 버전이 있는 파일 Progid에 대해 다음과 같은 명명 규칙을 사용 하 여 다른 공급 업체의 등록과 중복 되지 않도록 합니다.

|파일 확장명|버전이 지정 된 ProgID|
|--------------------|----------------------|
|. 확장명|제품. 확장명. versionMajor. Versionmajor|

 버전이 지정 된 Progid를 HKEY_CLASSES_ROOT \\ \Openwithprogids 키에 값으로 추가 하 여 특정 파일 확장명을 열 수 있는 다른 응용 프로그램을 등록할 수 있습니다 *\<extension>* . 이 레지스트리 키에는 파일 확장명과 연결 된 대체 Progid의 목록이 포함 됩니다. 나열 된 Progid와 연결 된 응용 프로그램이_제품 이름_ **으로 열기**하위 메뉴에 표시 됩니다. 동일한 응용 프로그램이 및 키 둘 다에서 지정 된 경우 `OpenWithList` `OpenWithProgids` 운영 체제에서 중복 항목을 병합 합니다.

> [!NOTE]
> `OpenWithProgids`키는 WINDOWS XP 에서만 지원 됩니다. 다른 운영 체제에서는이 키를 무시 하므로 파일 처리기의 유일한 등록으로 사용 하지 마십시오. 이 키를 사용 하 여 Windows XP에서 더 나은 사용자 환경을 제공 합니다.

 REG_NONE 형식의 값으로 원하는 Progid를 추가 합니다. 다음 코드에서는 파일 확장명에 Progid를 등록 하는 예를 제공 합니다.* ext*).

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 파일 확장명에 대 한 기본값으로 지정 된 ProgID가 기본 파일 처리기입니다. 이전 버전의와 함께 제공 되는 파일 확장명에 대 한 ProgID를 수정 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 하거나 다른 응용 프로그램에서 가져올 수 있는 경우 `OpenWithProgids` 파일 확장명에 대 한 키를 등록 하 고 지원 되는 이전 progid와 함께 목록에 새 ProgID를 지정 해야 합니다. 예를 들면 다음과 같습니다.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 이전 ProgID에 연결 된 동사가 있는 경우 바로 가기 메뉴에서 *제품 이름* **으로 열기** 에도 이러한 동사가 표시 됩니다.

## <a name="see-also"></a>추가 정보
- [파일 확장명 정보](../extensibility/about-file-name-extensions.md)
- [파일 이름 확장명에 대한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)
