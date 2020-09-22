---
title: 파일 연결 만들기 (ClickOnce 앱)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcca57415eae6480286f457755b996f22cb6507a
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809783"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>방법: ClickOnce 애플리케이션에 대한 파일 연결 만들기
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램은 하나 이상의 파일 이름 확장명에 연결 될 수 있으므로 사용자가 이러한 형식의 파일을 열 때 응용 프로그램이 자동으로 시작 됩니다. 응용 프로그램에 파일 이름 확장명 지원을 추가 하 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 는 것은 간단 합니다.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce 응용 프로그램에 대 한 파일 연결을 만들려면

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]응용 프로그램을 정상적으로 만들거나 기존 응용 프로그램을 사용 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다.

2. 메모장과 같은 텍스트 또는 XML 편집기를 사용 하 여 응용 프로그램 매니페스트를 엽니다.

3. `assembly` 요소를 찾습니다. 자세한 내용은 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)를 참조 하세요.

4. 요소의 자식으로 요소를 `assembly` 추가 `fileAssociation` 합니다. 요소에는 `fileAssociation` 다음 네 가지 특성이 있습니다.

   - `extension`: 응용 프로그램에 연결 하려는 파일 이름 확장명입니다.

   - `description`: Windows 셸에 표시 되는 파일 형식에 대 한 설명입니다.

   - `progid`: 레지스트리에 표시 하기 위해 파일 형식을 고유 하 게 식별 하는 문자열입니다.

   - `defaultIcon`:이 파일 형식에 사용할 아이콘입니다. 응용 프로그램 매니페스트에서 아이콘을 파일 리소스로 추가 해야 합니다. 자세한 내용은 [방법: ClickOnce 애플리케이션에 데이터 파일 포함](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)을 참조하세요.

     및 요소에 대 한 예제는 `file` `fileAssociation` [ \<fileAssociation> 요소](../deployment/fileassociation-element-clickonce-application.md)를 참조 하세요.

5. 응용 프로그램에 둘 이상의 파일 형식을 연결 하려면 요소를 더 추가 `fileAssociation` 합니다. 특성은 서로 `progid` 달라 야 합니다.

6. 응용 프로그램 매니페스트를 마치면 매니페스트에 다시 서명 합니다. *Mage.exe*를 사용 하 여 명령줄에서이 작업을 수행할 수 있습니다.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    자세한 내용은 [Mage.exe(매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)를 참조하세요.

## <a name="see-also"></a>추가 정보
- [\<fileAssociation> 요소인](../deployment/fileassociation-element-clickonce-application.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
- [Mage.exe(매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)