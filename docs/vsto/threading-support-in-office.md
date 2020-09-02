---
title: Office의 스레딩 지원
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3218a12add86739c76cd50f82fdda5d845e2b069
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62978769"
---
# <a name="threading-support-in-office"></a>Office의 스레딩 지원
  이 문서에서는 Microsoft Office 개체 모델에서 스레딩을 지 원하는 방법에 대 한 정보를 제공 합니다. Office 개체 모델은 스레드로부터 안전 하지 않지만 Office 솔루션에서 여러 스레드로 작업할 수 있습니다. Office 응용 프로그램은 COM (구성 요소 개체 모델) 서버입니다. COM을 사용 하면 클라이언트가 임의의 스레드에서 COM 서버를 호출할 수 있습니다. 스레드로부터 안전 하지 않은 COM 서버의 경우 COM은 동시 호출을 serialize 하는 메커니즘을 제공 하 여 언제 든 지 서버에서 하나의 논리 스레드만 실행 되도록 합니다. 이 메커니즘을 STA (단일 스레드 아파트) 모델 이라고 합니다. 호출은 serialize 되므로 서버가 사용 중이거나 백그라운드 스레드에서 다른 호출을 처리 하는 동안에는 호출자가 차단 될 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>여러 스레드를 사용 하는 경우 필요한 정보
 여러 스레드로 작업 하려면 다중 스레딩의 다음 측면에 대해 최소한의 기본 지식이 있어야 합니다.

- Windows Api

- COM 다중 스레드 개념

- 동시성

- 동기화

- 마샬링

  다중 스레딩에 대 한 일반 정보 [는 관리 되는 스레딩](/dotnet/standard/threading/)을 참조 하세요.

  Office는 주 STA에서 실행 됩니다. 이에 대 한 의미를 이해 하면 Office에서 여러 스레드를 사용 하는 방법을 이해할 수 있습니다.

## <a name="basic-multithreading-scenario"></a>기본 다중 스레딩 시나리오
 Office 솔루션의 코드는 항상 주 UI 스레드에서 실행 됩니다. 백그라운드 스레드에서 별도의 작업을 실행 하 여 응용 프로그램 성능을 향상 시킬 수 있습니다. 목표는 한 작업을 수행 하는 대신 두 작업을 한 번에 완료 하는 것입니다 .이 작업은 더 부드러운 실행 (여러 스레드를 사용 하는 주요 이유)이 발생 합니다. 예를 들어 기본 Excel UI 스레드에 이벤트 코드가 있을 수 있으며 백그라운드 스레드에서 서버에서 데이터를 수집 하 고 Excel UI의 셀을 서버의 데이터로 업데이트 하는 작업을 실행할 수 있습니다.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Office 개체 모델을 호출 하는 백그라운드 스레드
 백그라운드 스레드에서 Office 응용 프로그램을 호출 하면 호출은 자동으로 STA 경계를 넘어 마샬링됩니다. 그러나 백그라운드 스레드에서 호출을 수행할 때 Office 응용 프로그램에서 호출을 처리할 수 있다는 보장이 없습니다. 다음과 같은 여러 가지 가능성이 있습니다.

1. 전화를 걸 수 있도록 Office 응용 프로그램에서 메시지를 펌프 해야 합니다. 이 작업을 수행 하는 동안 많은 시간이 소요 되는 경우 시간이 걸릴 수 있습니다.

2. 다른 논리 스레드가 이미 아파트에 있으면 새 스레드는를 입력할 수 없습니다. 이는 논리적 스레드가 Office 응용 프로그램에 들어간 후 다시 호출자의 아파트에 재진입 호출을 수행 하는 경우에 주로 발생 합니다. 해당 호출이 반환 될 때까지 응용 프로그램을 차단 합니다.

3. Excel은 들어오는 호출을 즉시 처리할 수 없는 상태에 있을 수 있습니다. 예를 들어 Office 응용 프로그램은 모달 대화 상자를 표시할 수 있습니다.

   가능성 2와 3의 경우 COM은 [imessagefilter.prefiltermessage](/windows/desktop/api/objidl/nn-objidl-imessagefilter) 인터페이스를 제공 합니다. 서버에서 구현 하는 경우 모든 호출이 [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) 메서드를 통해 입력 됩니다. 가능성 2의 경우 호출은 자동으로 거부 됩니다. 가능성 3의 경우 서버는 상황에 따라 호출을 거부할 수 있습니다. 호출이 거부 되 면 호출자는 수행할 작업을 결정 해야 합니다. 일반적으로 호출자는 [imessagefilter.prefiltermessage](/windows/desktop/api/objidl/nn-objidl-imessagefilter)을 구현 합니다 .이 경우 [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) 메서드에 의해 거부 되었다는 알림이 표시 됩니다.

   그러나 Visual Studio에서 Office 개발 도구를 사용 하 여 만든 솔루션의 경우에는 COM interop 거부 된 모든 호출을로 변환 합니다 <xref:System.Runtime.InteropServices.COMException> ("메시지 필터가 응용 프로그램을 사용 중임을 나타냅니다"). 백그라운드 스레드에서 개체 모델을 호출할 때마다이 예외를 처리할 수 있도록 준비 해야 합니다. 일반적으로 특정 시간 동안 재시도 하 고 대화 상자를 표시 하는 작업이 포함 됩니다. 그러나 백그라운드 스레드를 STA로 만든 다음 해당 스레드에 대 한 메시지 필터를 등록 하 여이 경우를 처리할 수도 있습니다.

## <a name="start-the-thread-correctly"></a>스레드를 올바르게 시작 합니다.
 새 STA 스레드를 만들 때 스레드를 시작 하기 전에 아파트 상태를 STA로 설정 합니다. 다음 코드 예제에서는 이 작업을 수행하는 방법을 보여 줍니다.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 자세한 내용은 [관리 되는 스레딩 모범 사례](/dotnet/standard/threading/managed-threading-best-practices)를 참조 하세요.

## <a name="modeless-forms"></a>모덜리스 폼
 모덜리스 폼을 사용 하면 폼이 표시 되는 동안 응용 프로그램과 상호 작용 하는 형식을 사용할 수 있습니다. 사용자는 폼과 상호 작용 하 고 폼은를 닫지 않고 응용 프로그램과 상호 작용 합니다. Office 개체 모델은 관리 되는 모덜리스 폼을 지원 합니다. 그러나 백그라운드 스레드에서 사용 하면 안 됩니다.

## <a name="see-also"></a>추가 정보
- [스레딩 (c #)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [스레딩(Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [스레드 및 스레딩 사용](/dotnet/standard/threading/using-threads-and-threading)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
