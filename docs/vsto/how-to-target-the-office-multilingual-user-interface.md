---
title: '방법: Office 다국어 사용자 인터페이스 대상'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5217f2d6cf67eced00c0c84b9bacda94573c5a09
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537503"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>방법: Office 다국어 사용자 인터페이스 대상
  MUI (다국어 사용자 인터페이스)는 최종 사용자에 게 UI (사용자 인터페이스)의 언어를 변경할 수 있는 기능을 제공 하는 Microsoft Office 기능입니다. 예를 들어 영어 UI를 사용 하 여 작업 하는 최종 사용자는 UI의 언어를 스페인어로 변경할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 여러 언어의 Office를 사용 하는 사용자가 응용 프로그램을 사용 하는 경우 사용자 컴퓨터에서 Office에 사용 되는 언어와 일치 하도록 UI 문자열의 언어를 자동으로 변경 하는 코드를 추가할 수 있습니다 (사용자가 올바른 리소스를 설치한 경우).

## <a name="to-check-the-current-office-ui-setting"></a>현재 Office UI 설정을 확인 하려면

1. <xref:System.Threading.Thread.CurrentUICulture%2A>현재 스레드의 속성을 사용 합니다. 사용자의 컴퓨터에서 현재 실행 되는 Office 버전에서 사용 하는 언어와 일치 하도록 UI 문자열의 언어를 설정 합니다.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>참고 항목
- [방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Office 솔루션의 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)
