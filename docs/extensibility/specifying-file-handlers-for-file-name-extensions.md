---
title: 파일 이름 확장명에 대한 파일 처리기 지정 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699748"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>파일 이름 확장명에 대한 파일 처리기 지정
특정 파일 확장이 있는 파일을 처리하는 응용 프로그램을 확인하는 방법에는 여러 가지가 있습니다. OpenWithList 및 OpenWithProgids 동사는 파일 확장명에 대한 레지스트리 항목 아래에 파일 처리기를 지정하는 두 가지 방법입니다.

## <a name="openwithlist-verb"></a>오픈위드리스트 동사
 Windows 탐색기에서 파일을 마우스 오른쪽 단추로 클릭하면 **열기** 명령이 표시됩니다. 둘 이상의 제품이 확장과 연결된 경우 하위 메뉴를 **가진 열기가** 표시됩니다.

 HKEY_CLASSES_ROOT 파일 확장에 대한 OpenWithList 키를 설정하여 확장을 열려면 다른 응용 프로그램을 등록할 수 있습니다. 파일 확장에 대해 이 키 아래에 나열된 응용 프로그램은 **대화** 상자 열기에서 **권장 프로그램** 제목 아래에 표시됩니다. 다음 예제에서는 .vcproj 파일 확장자 열기 위해 등록된 응용 프로그램을 보여 주습니다.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithList\
         devenv.exe
```

> [!NOTE]
> 응용 프로그램을 지정하는 키는 HKEY_CLASSES_ROOT\응용 프로그램 아래의 목록에서 작성되었습니다.

 OpenWithList 키를 추가 하 여 다른 응용 프로그램 확장자의 소유권을 차지 하는 경우에 응용 프로그램 파일 확장프로그램을 지원 하는 선언 합니다. 응용 프로그램 또는 다른 응용 프로그램의 이후 버전일 수 있습니다.

## <a name="openwithprogids"></a>오픈와프로그기드
 프로그래매틱 식별자(ProgID)는 응용 프로그램 또는 COM 개체의 버전을 식별하는 ClassID의 친숙한 버전입니다. 공동 가능한 모든 오브젝트에는 자체 ProgID가 있어야 합니다. 예를 들어 VisualStudio.DTE.7.1은 Visual Studio.NET 2003을 시작하고 VisualStudio.DTE.10.0은 시작됩니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트 유형 또는 프로젝트 항목 유형의 소유자로서 파일 확장명에 대한 버전별 ProgID를 만들어야 합니다. 이들 프로그ID는 하나 이상의 ProgID가 동일한 애플리케이션을 시작할 수 있다는 점에서 중복될 수 있다. 자세한 내용은 [파일 이름 확장명에 대한 동사 등록을](../extensibility/registering-verbs-for-file-name-extensions.md)참조하십시오.

 다른 공급업체의 등록으로 중복되지 않도록 버전이 지정된 파일 ProgID에 대해 다음 명명 규칙을 사용합니다.

|파일 확장명|버전이 있는 프로그ID|
|--------------------|----------------------|
|.확장|Productname. 확장.버전메이저.버전마이너|

 버전이 적용된 ProgID를 \OpenWithProgids 키에 HKEY_CLASSES_ROOT\\*\<확장>* 값으로 추가하여 특정 파일 확장자를 열 수 있는 다른 응용 프로그램을 등록할 수 있습니다. 이 레지스트리 키에는 파일 확장과 관련된 대체 ProgID 목록이 포함되어 있습니다. 나열된 ProgID와 연결된 응용 프로그램은 **Open With**_제품 이름_ 열기 하위 메뉴에 나타납니다. `OpenWithList` 동일한 응용 프로그램이 키와 `OpenWithProgids` 키 모두에 지정되면 운영 체제가 중복을 병합합니다.

> [!NOTE]
> 키는 `OpenWithProgids` Windows XP에서만 지원됩니다. 다른 운영 체제에서는 이 키를 무시하므로 파일 처리기에 대한 유일한 등록으로 사용하지 마십시오. 이 키를 사용하여 Windows XP에서 더 나은 사용자 환경을 제공합니다.

 원하는 ProgID를 REG_NONE 형식의 값으로 추가합니다. 다음 코드는 파일 확장자를 위한 ProgID를 등록하는 예제를 제공합니다(* 내설)을*참조하십시오.

```
HKEY_CLASSES_ROOT\
   .ext\
      (default)="MyProduct.ext.14.0"
      OpenWithProgids
         progid        REG_NONE (zero-length binary value)
         otherprogid   REG_NONE (zero-length binary value)
```

 파일 확장자의 기본값으로 지정된 ProgID가 기본 파일 처리기입니다. 이전 버전과 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 함께 제공되거나 다른 응용 프로그램에서 인계할 수 있는 파일 확장명에 대한 ProgID를 수정하는 경우 파일 확장명에 대한 `OpenWithProgids` 키를 등록하고 지원되는 이전 ProgID와 함께 목록에 새 ProgID를 지정해야 합니다. 다음은 그 예입니다.

```
HKEY_CLASSES_ROOT\
   .vcproj\
      (default)="VisualStudio.vcproj.14.0"
      OpenWithProgids
         vcprojfile              //old progid
         VisualStudio.vcproj.12.0 //old progid
         VisualStudio.vcproj.14.0 //new progid
```

 이전 ProgID에 연결된 동사가 있는 경우 이러한 동사는 바로 가기 메뉴의 *제품 이름* **열기** 아래에도 표시됩니다.

## <a name="see-also"></a>참조
- [파일 확장명 정보](../extensibility/about-file-name-extensions.md)
- [파일 이름 확장명에 대한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)
