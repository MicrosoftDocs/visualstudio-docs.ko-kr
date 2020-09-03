---
title: 작업 선택 대화 상자 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659168"
---
# <a name="choose-operation-dialog-box-legacy"></a>작업 선택 대화 상자(레거시)
이 항목에서는 레거시에서 **작업 선택** 대화 상자를 사용 하는 방법에 대해 설명 합니다 [!INCLUDE[wfd1](../includes/wfd1-md.md)] . 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 **작업 선택** 대화 상자는 <xref:System.Workflow.Activities.ReceiveActivity> 활동 또는 활동과 연결할 작업을 선택 하는 데 사용 됩니다 <xref:System.Workflow.Activities.SendActivity> . 이러한 작업에이 대화 상자를 사용 하는 방법에 대 한 자세한 내용은 [방법: Wcf 계약 작업 구현 (레거시)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 및 [방법: Wcf 계약 작업 호출 (레거시)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)을 참조 하세요.

 다음 표에서는 **작업 선택** 대화 상자의 UI (사용자 인터페이스) 요소에 대해 설명 합니다.

|UI 요소|설명|
|----------------|-----------------|
|**계약 추가**|자동으로 새 계약을 만듭니다. 이 계약에 새 작업을 정의할 수 있습니다. 이 UI 요소는 <xref:System.Workflow.Activities.ReceiveActivity>에만 사용됩니다.|
|**작업 추가**|**작업 선택** 대화 상자에서 만든 새 계약에 새 작업을 추가 합니다. **참고:**  **작업 선택** 대화 상자를 통해 만든 계약에만 새 작업을 추가할 수 있습니다. <br /><br /> 이 UI 요소는 <xref:System.Workflow.Activities.ReceiveActivity>에만 사용됩니다.|
|**가져오기 ...**|이전에 정의된 계약을 가져오며 해당 계약에서 작업을 선택할 수 있습니다.|
|**작업 이름**|현재 선택한 작업의 이름입니다. 이 입력란은 **작업 선택** 대화 상자를 통해 작업을 만든 경우에만 편집할 수 있습니다.|
|**매개 변수**|현재 선택한 작업에 대한 매개 변수 정의가 포함된 탭입니다. **참고:**  **작업 선택** 대화 상자를 통해 작업을 만든 경우에만 매개 변수 정의를 변경할 수 있습니다.|
|**속성**|클라이언트와 서비스 간에 보낸 메시지의 <xref:System.Net.Security.ProtectionLevel> 설정이 포함된 탭입니다. **참고:**  이 탭은 **작업 선택** 대화 상자를 통해 작업을 만든 경우에만 사용할 수 있습니다.|
|**권한**|해당 작업을 호출할 수 있는 사용자의 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A> 및 <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A> 속성이 포함된 탭입니다. 예를 들어 Administrators 그룹의 사용자만 해당 작업을 호출할 수 있는 경우 **역할** 텍스트 상자에 "관리자"를 작성 합니다.<br /><br /> 이 탭은 **ChooseOperation** 대화 상자를 통해 만든 작업과 **가져오기** 단추를 통해 가져온 작업 모두에 사용할 수 있습니다.|

> [!NOTE]
> **작업 선택** 대화 상자에는 워크플로의 다른 활동에서 사용 하는 계약 또는 작업만 표시 <xref:System.Workflow.Activities.SendActivity> 됩니다. 마찬가지로 활동에 대 한 **작업 선택** 대화 상자에는 <xref:System.Workflow.Activities.ReceiveActivity> 워크플로의 다른 **ReceiveActivity** 활동에서 사용 하는 계약 또는 작업만 표시 됩니다.

## <a name="see-also"></a>관련 항목
 [방법: Wcf 계약 작업 구현 (레거시)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) 방법: [Windows Workflow Foundation UI 도움말을 위한](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md) [wcf 계약 작업 (레거시)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) 레거시 디자이너 호출