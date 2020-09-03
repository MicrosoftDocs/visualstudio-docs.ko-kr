---
title: Office 솔루션에 대 한 특정 보안 고려 사항
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 571b604b87fb7fac4e78c83a791c265d910fae94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985589"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Office 솔루션에 대 한 특정 보안 고려 사항
  Microsoft .NET Framework 및 Microsoft Office에서 제공된 보안 기능을 통해 다양한 보안 위협에 대해 Office 솔루션을 보호할 수 있습니다. 이 항목에서는 이러한 위협 중 일부에 대해 설명하고 이러한 위협으로부터 보호하기 위한 권장 사항을 제공합니다. 또한 Office 솔루션에 영향을 주는 Microsoft Office 보안 설정에 대한 정보를 포함합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>신뢰할 수 있는 코드는 악의적인 새 문서에서 다른 용도로
 공격자는 입사 지원을 위한 개인 정보를 다운로드하는 등 특정 용도를 위한 신뢰할 수 있는 코드를 가져와서 워크시트 등의 다른 문서에서 재사용할 수 있습니다. 코드 쪽에서는 원본 문서가 실행되고 있지 않다는 것을 알지 못하므로 다른 사용자가 열 때 개인 정보 노출 또는 높은 권한으로 코드 실행 등 다른 위협이 발생할 수 있습니다. 또는 공격자가 워크시트의 데이터를 수정할 수 있습니다 .이 경우에는 공격에 전송 될 때 예기치 않게 동작 합니다. 악의적인 사용자가 코드에 연결된 워크시트에서 값, 수식 또는 문자 표시를 변경한 다음 수정된 파일을 보내 다른 사용자를 공격할 수 있습니다. 워크시트의 값을 수정하여 보기 권한이 없는 사용자가 정보에 액세스할 수도 있습니다.

 어셈블리 위치 및 문서 위치 모두에 대해 충분한 실행 증거가 있어야 하므로 이 공격은 실행하기가 쉽지 않습니다. 예를 들어 메일 첨부 파일의 문서 또는 신뢰할 수 없는 인트라넷 서버에는 충분한 실행 권한이 없습니다.

 이 공격을 가능하게 하려면 잠재적으로 신뢰할 수 없는 데이터를 기준으로 결정을 내리는 방법 등으로 코드를 작성해야 합니다. 예제에서는 데이터베이스 서버 이름이 포함된 숨겨진 셀이 있는 워크시트를 만듭니다. 사용자가 워크시트를 SQL 인증 및 하드 코드된 SA 암호를 사용하여 해당 서버에 연결을 시도하는 ASPX 페이지에 제출합니다. 공격자가 숨겨진 셀의 내용을 다른 컴퓨터 이름으로 바꿔서 SA 암호를 알아낼 수 있습니다. 이 문제를 방지하려면 암호를 하드 코드하지 말고 서버에 액세스하기 전에 유효한 것으로 알려진 내부 서버 목록에 대해 서버 ID를 항상 확인합니다.

### <a name="recommendations"></a>권장 사항

- 사용자, 문서, 데이터베이스, 웹 서비스 또는 기타 원본으로부터의 입력 및 데이터의 유효성을 항상 검사합니다.

- 사용자 대신 권한 있는 데이터 가져오기 및 보호되지 않는 워크시트에 데이터 쓰기 등 특정 유형의 기능을 노출할 때 주의합니다.

- 애플리케이션 형식에 따라 코드를 실행하기 전에 원본 문서가 실행 중인지 확인해야 합니다. 예를 들어 알려지고 안전한 위치에 저장된 문서에서 실행되고 있는지 확인합니다.

- 애플리케이션에서 권한 있는 작업을 수행하는 경우 문서를 열 때 경고를 표시하는 것도 좋은 방법입니다. 예를 들어 애플리케이션이 개인 정보에 액세스하려고 하며 계속할지 또는 취소할지 선택하라는 시작 대화 상자나 시작 화면을 사용자에게 표시할 수 있습니다. 문제 없는 문서에서 이러한 경고가 나타나는 경우 최종 사용자는 손상되기 전에 애플리케이션을 종료할 수 있습니다.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Outlook 개체 모델 보호에 의해 코드가 차단 됨
 Microsoft Office에서는 코드에서 개체 모델의 특정 속성, 메서드 및 개체를 사용하지 못하도록 제한할 수 있습니다. Outlook에서는 이러한 개체에 대 한 액세스를 제한 하 여 악의적인 목적으로 전자 메일 웜과 바이러스가 개체 모델을 사용 하는 것을 방지 합니다. 이 보안 기능을 Outlook 개체 모델 보호라고 합니다. 개체 모델 보호를 사용 하는 동안 VSTO 추가 기능에서 제한 된 속성이 나 메서드를 사용 하려고 하면 사용자가 작업을 중지할 수 있도록 하는 보안 경고를 표시 하거나 사용자가 제한 된 기간 동안 속성 또는 메서드에 대 한 액세스 권한을 부여할 수 있도록 합니다. 사용자가 작업을 중지한 경우 Visual Studio의 Office 솔루션을 사용하여 만들어진 Outlook VSTO 추가 기능에서 <xref:System.Runtime.InteropServices.COMException>을 throw합니다.

 개체 모델 보호는 Outlook이 Microsoft Exchange Server와 함께 사용되는지 여부에 따라 여러 가지 방법으로 VSTO 추가 기능에 영향을 줄 수 있습니다.

- Outlook이 Exchange와 함께 사용되지 않는 경우 관리자는 컴퓨터의 모든 VSTO 추가 기능에 대해 개체 모델 보호를 사용하거나 사용하지 않도록 설정할 수 있습니다.

- Outlook이 Exchange와 함께 사용되는 경우 관리자는 컴퓨터의 모든 VSTO 추가 기능에 대해 개체 모델 보호를 사용 또는 사용하지 않도록 설정하거나, 개체 모델 보호 발생 없이 특정 VSTO 추가 기능을 실행할 수 있도록 지정할 수 있습니다. 또한 관리자는 개체 모델의 특정 영역에 대해 개체 모델 보호 동작을 수정할 수도 있습니다. 예를 들어 관리자는 개체 모델 보호를 사용 하도록 설정한 경우에도 VSTO 추가 기능에서 프로그래밍 방식으로 메일을 보내도록 자동으로 허용할 수 있습니다.

  Outlook 2007부터 Outlook 보안을 유지하면서 개발자 및 사용자 환경을 개선하도록 개체 모델 보호 동작이 변경되었습니다. 자세한 내용은 [Outlook 2007의 코드 보안 변경 내용](/previous-versions/office/developer/office-2007/bb226709(v=office.12))을 참조 하세요.

### <a name="minimize-object-model-guard-warnings"></a>개체 모델 보호 경고 최소화
 제한된 속성 및 메서드 사용 시 보안 경고가 표시되지 않도록 하려면 VSTO 추가 기능에서 프로젝트에 `Application` 클래스의 `ThisAddIn` 필드에서 Outlook 개체를 가져와야 합니다. 이 필드에 대 한 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

 이 개체에서 가져온 Outlook 개체만 개체 모델 보호에서 신뢰할 수 있습니다. 반면, 개체 모델 보호를 사용하도록 설정할 경우 새 `Microsoft.Office.Interop.Outlook.Application` 개체에서 가져온 개체는 신뢰할 수 없으며 제한된 속성 및 메서드는 보안 경고를 발생시킵니다.

 개체 모델 보호를 사용하도록 설정할 경우 다음 코드 예제는 보안 경고를 표시합니다. `Microsoft.Office.Interop.Outlook.MailItem` 클래스의 `To` 속성은 개체 모델 보호에 의해 제한됩니다. `Microsoft.Office.Interop.Outlook.MailItem`개체가 `Microsoft.Office.Interop.Outlook.Application` 필드에서 가져오는 대신 **new** 연산자를 사용 하 여 만든에서 해당 개체를 가져오므로 개체는 신뢰할 수 없습니다 `Application` .

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 다음 코드 예제에서는 `Microsoft.Office.Interop.Outlook.MailItem` 개체 모델 가드에서 신뢰 하는 개체의 제한 된 속성을 사용 하는 방법을 보여 줍니다. 이 코드에서는 신뢰할 수 있는 `Application` 필드를 사용하여 `Microsoft.Office.Interop.Outlook.MailItem`을 가져옵니다.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> Outlook을 Exchange와 함께 사용할 경우 `ThisAddIn.Application` 에서 모든 Outlook 개체를 가져와도 VSTO 추가 기능에서 전체 Outlook 개체 모델에 액세스하지 못할 수 있습니다. 예를 들어 Exchange 관리자가 outlook 개체 모델을 사용 하 여 주소 정보에 액세스 하려는 모든 시도를 자동으로 거부 하도록 outlook을 설정 하는 경우, 코드 예제에서는 신뢰할 수 있는 필드를 사용 하는 경우에도 이전 코드 예제가 To 속성에 액세스 하는 것을 허용 하지 않습니다 `ThisAddIn.Application` .

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Exchange 사용 시 신뢰할 수 있는 추가 기능 지정
 Outlook을 Exchange와 함께 사용하는 경우 관리자는 개체 모델 보호 발생 없이 특정 VSTO 추가 기능을 실행할 수 있도록 지정할 수 있습니다. Visual Studio의 Office 솔루션을 사용하여 만들어진 Outlook VSTO 추가 기능은 개별적으로 신뢰할 수 없으며 그룹으로만 신뢰할 수 있습니다.

 Outlook은 VSTO 추가 기능에 있는 진입점 DLL의 해시 코드를 기반으로 VSTO 추가 기능을 신뢰 합니다. 을 대상으로 하는 모든 Outlook VSTO 추가 기능은 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 동일한 진입점 DLL (*VSTOLoader.dll*)을 사용 합니다. 즉, 관리자가 개체 모델 보호를 발생 시 키 지 않고 실행 하도록를 대상으로 하는 VSTO 추가 기능을 신뢰 하는 경우 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 를 대상으로 하는 다른 모든 Vsto 추가 기능도 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 신뢰할 수 있습니다. 개체 모델 보호 발생 없이 실행하도록 VSTO 추가 기능을 신뢰하는 방법에 대한 자세한 내용은 [Outlook에서 바이러스 예방 기능을 관리하는 데 사용되는 방법 지정](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12))을 참조하세요.

## <a name="permission-changes-do-not-take-effect-immediately"></a>권한 변경 내용은 즉시 적용 되지 않습니다.
 관리자가 문서 또는 어셈블리에 대한 사용 권한을 조정한 경우 변경 내용을 적용하려면 사용자가 모든 Office 애플리케이션을 종료했다가 다시 시작해야 합니다.

 Microsoft Office 애플리케이션을 호스트하는 기타 애플리케이션도 새 권한이 적용되는 것을 방해할 수 있습니다. 보안 정책을 변경한 후에는 호스트인지 또는 독립 실행형인지 관계없이 Office를 사용하는 모든 애플리케이션을 종료해야 합니다.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Microsoft Office 시스템의 보안 센터 설정이 추가 기능 또는 문서 수준 사용자 지정에 영향을 주지 않음
 사용자는 **보안 센터**의 옵션을 설정하여 VSTO 추가 기능이 로드되지 않도록 방지할 수 있습니다. 그러나 Visual Studio의 Office 솔루션을 사용하여 만든 문서 수준 사용자 지정 및 VSTO 추가 기능은 이러한 신뢰 설정에 의해 영향을 받지 않습니다.

 사용자가 **보안 센터**를 사용하여 VSTO 추가 기능이 로드되지 않도록 방지한 경우 다음 형식의 VSTO 추가 기능이 로드되지 않습니다.

- 관리되는/관리되지 않는 COM VSTO 추가 기능

- 관리되는/관리되지 않는 스마트 문서

- 관리되는/관리되지 않는 자동화 VSTO 추가 기능

- 관리되는/관리되지 않는 실시간 데이터 구성 요소

  다음 절차에서는 사용자가 **보안 센터** 를 사용하여 VSTO 추가 기능이 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 및 Microsoft Office 2010에서 로드되지 않도록 제한하는 방법을 설명합니다. 이러한 절차는 Visual Studio의 Office 개발을 사용하여 만든 사용자 지정 또는 VSTO 추가 기능에 영향을 주지 않습니다.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-office_15_short-applications"></a>Microsoft Office 2010 및 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 애플리케이션에서 VSTO 추가 기능을 사용하지 않으려면

1. **파일** 탭을 선택합니다.

2. *ApplicationName* **옵션** 단추를 선택합니다.

3. 범주 창에서 **보안 센터**를 선택합니다.

4. 세부 정보 창에서 **보안 센터 설정**을 선택합니다.

5. 범주 창에서 **추가 기능**을 선택합니다.

6. 세부 정보 창에서 **애플리케이션 추가 기능에 신뢰할 수 있는 게시자의 서명 필요** 또는 **모든 애플리케이션 추가 기능 사용 안 함**을 선택합니다.

## <a name="see-also"></a>추가 정보
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
