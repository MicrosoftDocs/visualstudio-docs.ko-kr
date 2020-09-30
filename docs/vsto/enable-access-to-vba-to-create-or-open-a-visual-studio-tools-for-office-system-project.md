---
title: VSTO 시스템 프로젝트를 만들거나 열기 위한 VBA 액세스
titleSuffix: ''
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e30a89bdf8547eab9ed9c51b07c49e014b7302
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584861"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>VBA에 대 한 액세스를 사용 하 여 Microsoft Office 시스템 프로젝트에 대 한 Visual Studio Tools 만들기 또는 열기

Microsoft Office에서 Visual Basic for Applications (VBA) 프로젝트 시스템에 대 한 액세스를 명시적으로 사용 하도록 설정 해야 Microsoft Office 시스템 프로젝트에 대 한 Visual Studio Tools를 만들거나 열 수 있습니다.

 프로젝트에서 Visual Basic for Applications를 사용 하지 않더라도 Microsoft Office 개발 프로젝트를 사용 하려면 Microsoft Office Word에서 Visual Basic for Applications (VBA) 프로젝트 시스템에 액세스 하 고 Excel을 Microsoft Office 해야 합니다. Visual Basic 및 C# 프로젝트의 디자인 타임 컨트롤 지원은 Visual Basic for Applications 프로젝트 시스템에 따라 달라집니다.

 일부 Microsoft Office 매크로 바이러스는 자신을 전파하기 위한 수단으로 Visual Basic for Applications 프로젝트 시스템을 자동화하려 할 수 있습니다. Visual Basic for Applications 프로젝트 시스템에 액세스할 수 있도록 설정하는 순간 매크로 바이러스 확산을 방지할 수 있는 안전 기능이 작동하지 않게 되는 것입니다. 그러나 일반적인 매크로 보안은 계속 적용되므로 Office 애플리케이션에 대해 유지 관리하는 신뢰할 수 있는 게시자 목록과 매크로 보안 수준을 통해 매크로를 컴퓨터에서 실행해도 되는지 여부가 결정됩니다.

> [!NOTE]
> 이 옵션은 개발 컴퓨터에만 적용됩니다. 최종 사용자 컴퓨터에서는 Office 솔루션을 실행 하기 위해이 옵션이 사용 하도록 설정 되어 있지 않아도 됩니다.

 Visual Basic for Applications 프로젝트 시스템에 액세스할 수 없도록 설정하는 것 자체만으로는 바이러스로부터 컴퓨터를 보호할 수 없으며, 컴퓨터가 매크로 바이러스에 감염되는 경우 일부 바이러스가 다른 문서로 확산되는 것을 중지할 수 있을 뿐입니다. 이 옵션은 컴퓨터에 대한 추가 보호 계층으로 기본적으로 사용하지 않도록 설정됩니다. 그러나 이 옵션을 사용하도록 설정해도 보안 모범 사례를 따르면 컴퓨터가 바이러스에 더 감염되기 쉬운 상태가 되지는 않습니다.

 Office 매크로 바이러스에 대 한 최상의 보호는 Office를 높음 또는 매우 높은 보안 수준으로 실행 하 여 확인 되 고 알려진 원본에서 매크로를 신뢰 하 고 보안 패치와 바이러스 검색 프로그램을 최신 상태로 유지 하는 것입니다.

 수동으로 **Visual Basic 프로젝트에 대 한 액세스 신뢰** 옵션을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

 VBA 또는 COM 오류가 발생하는 경우에는 Office 설치를 복구할 수 있습니다.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Visual Basic 프로젝트에 대 한 액세스를 사용 하거나 사용 하지 않도록 설정 하려면

1. **파일** 탭을 클릭합니다.

2. **옵션**을 클릭합니다.

3. **보안 센터**를 클릭 한 다음 **보안 센터 설정**을 클릭 합니다.

4. **보안 센터**에서 **매크로 설정**을 클릭 합니다.

5. Visual Basic 프로젝트에 대 한 액세스를 활성화 하거나 비활성화 하려면 **VBA project 개체 모델에** 대 한 트러스트 된 액세스를 선택 하거나 선택 취소 합니다.

6. **확인**을 클릭합니다.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office 시스템을 사용 하 여 Visual Basic 프로젝트에 대 한 액세스를 사용 하거나 사용 하지 않도록 설정 하려면

1. Word 또는 Excel의 **도구** 메뉴에서 **매크로**를 가리킨 다음 **보안**을 클릭 합니다.

2. **보안** 대화 상자에서 **신뢰할 수 있는 게시자** 탭을 클릭 합니다.

3. **Visual Basic 프로젝트에**대 한 액세스를 사용 하지 않도록 설정 하거나 선택을 취소 하려면 선택 합니다.

4. **확인**을 클릭합니다.

## <a name="to-set-your-office-macro-security-level"></a>Office 매크로 보안 수준을 설정하려면

1. **파일** 탭을 클릭합니다.

2. **옵션**을 클릭합니다.

3. **보안 센터**를 클릭 한 다음 **보안 센터 설정**을 클릭 합니다.

4. **보안 센터**에서 **매크로 설정**을 클릭 합니다.

5. **매크로 설정** 섹션에서 원하는 설정을 선택 합니다.

6. **확인**을 클릭합니다.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office 시스템으로 Office 매크로 보안 수준을 설정 하려면

1. Word 또는 Excel의 **도구** 메뉴에서 **매크로**를 가리킨 다음 **보안**을 클릭 합니다.

2. **보안 수준** 탭에서 원하는 설정을 선택 합니다.

    **보안 수준** 탭에는 각 수준에 대 한 세부 정보가 포함 되어 있습니다. 자세한 내용은 Office 도움말에서 "매크로 보안 수준" 항목을 참조하세요.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>2007 Microsoft Office system과 함께 VBA를 설치하려면

1. 제어판에서 **프로그램 추가/제거** 또는 **프로그램 및 기능**을 실행 합니다.

2. **현재 설치 된 프로그램** 목록에서 Office를 선택 합니다.

3. **변경**을 클릭합니다.

4. **기능 추가/제거**를 선택한 다음 **계속**을 클릭 합니다.

5. **응용 프로그램의 고급 사용자 지정**선택을 선택 하 고 **다음**을 클릭 합니다.

6. **응용 프로그램 및 도구에 대 한 업데이트 옵션 선택** 목록에서 **Office 공유 기능** 을 확장 합니다.

7. **Visual Basic for Applications**옆에 있는 드롭다운 메뉴를 열고 **내 컴퓨터에서 실행**을 클릭 합니다.

8. **Continue(계속)** 를 클릭합니다.

9. **닫기**를 클릭합니다.

## <a name="to-repair-your-installation-of-office"></a>Office 설치를 복구하려면

1. 제어판에서 **프로그램 추가/제거** 또는 **프로그램 및 기능**을 실행 합니다.

2. **현재 설치 된 프로그램** 목록에서 Office의 버전을 선택 합니다.

3. **변경**을 클릭합니다.

4. **다시 설치 또는 복구**를 선택 하 고 **다음**을 클릭 합니다.

5. **Office 설치에서 오류 검색 및 복구**를 선택한 다음 **설치**를 클릭 합니다.

## <a name="see-also"></a>참고 항목
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
