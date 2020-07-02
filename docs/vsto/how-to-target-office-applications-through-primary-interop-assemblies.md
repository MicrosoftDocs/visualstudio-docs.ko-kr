---
title: 주 interop 어셈블리를 통해 Office 앱을 대상으로 합니다.
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60e351a15af4994d2bf64a800e3019501cf0571d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545771"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상
  새 Office 프로젝트를 만들 때 Visual Studio는 프로젝트를 빌드하는 데 필요한 Microsoft Office PIA(주 interop 어셈블리)에 대한 참조를 자동으로 추가합니다. 다음과 같은 시나리오에서는 다른 PIA에 대한 참조를 추가해야 합니다.

- 프로젝트에서 다른 Microsoft Office 애플리케이션의 기능을 사용하려고 합니다. 예를 들어 Microsoft Office Word용 프로젝트에서 Microsoft Office Excel의 기능을 사용할 수 있습니다.

- Microsoft Office Access와 같이 Visual Studio에 전용 프로젝트가 없는 Microsoft Office 애플리케이션을 자동화하려고 합니다.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>주 interop 어셈블리에 대한 참조를 추가하려면

1. Office 프로젝트를 열고 **솔루션 탐색기**에서 프로젝트 이름을 선택 합니다.

2. **프로젝트** 메뉴에서 **참조 추가**를 클릭합니다.

3. **프레임 워크** 탭의 **구성 요소 이름** 목록에서 원하는 PIA를 선택 합니다. 사용 가능한 Microsoft Office 주 interop 어셈블리에 대 한 자세한 내용은 [Office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)를 참조 하세요.

     프로젝트에서 이상을 대상으로 하는 경우 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 어셈블리 참조에 대 한 **Interop 형식 포함** 속성은 기본적으로 **True** 로 설정 됩니다. 이 설정을 사용하면 최종 사용자 컴퓨터에서 솔루션에 PIA가 필요하지 않습니다. 자세한 내용은 [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)를 참조 하세요.

    > [!NOTE]
    > Office 프로젝트에서 **COM** 탭 대신 **참조 추가** 대화 상자의 **.net** 탭을 사용 하 여 항상 office pia에 대 한 참조를 추가 합니다. 자세한 내용은 [Office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)를 참조 하세요.

4. **확인**을 클릭합니다.

     어셈블리 이름은 **솔루션 탐색기**의 **참조** 폴더에 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [Office 주 interop 어셈블리](../vsto/office-primary-interop-assemblies.md)
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [방법: Office 주 interop 어셈블리 설치](../vsto/how-to-install-office-primary-interop-assemblies.md)
