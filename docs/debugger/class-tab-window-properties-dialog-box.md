---
title: 창 속성 대화 상자, 클래스 탭 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0917c9a038b42e6302ec1f1782f095ca397a92ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565015"
---
# <a name="class-tab-window-properties-dialog-box"></a>창 속성 대화 상자, 클래스 탭
**클래스** 탭을 사용하면 선택한 창의 클래스에 대한 정보를 표시할 수 있습니다. [창 속성 대화 상자](../debugger/window-properties-dialog-box.md)를 표시하려면 [창 뷰](../debugger/windows-view.md) 창으로 포커스를 이동합니다. 트리에서 창 노드를 선택하고 **뷰** 메뉴에서 **속성**을 선택합니다.

 **클래스** 탭에서 다음 설정을 사용할 수 있습니다.

|입력|설명|
|-----------|-----------------|
|**클래스 이름**|이 창 클래스의 이름(또는 서수)입니다.|
|**클래스 스타일**|클래스 스타일 코드의 조합입니다.|
|**클래스 바이트**|이 창 클래스와 연결된 애플리케이션별 데이터입니다.|
|**클래스 아톰**|**RegisterClass** 호출에서 반환되는 클래스의 아톰입니다.|
|**인스턴스 핸들**|클래스를 등록한 모듈의 인스턴스 핸들입니다. 인스턴스 핸들은 고유하지 않습니다.|
|**창 바이트**|이 클래스의 각 창과 연결된 추가 바이트 수입니다. 이러한 바이트의 의미는 애플리케이션에 의해 결정됩니다. DWORD 형식의 바이트 값을 보려면 목록 상자를 확장합니다.|
|**창 프로시저**|이 클래스의 창을 위한 **WndProc** 함수의 현재 주소입니다. 이 주소는 창이 서브클래싱된 경우 **일반** 탭의 **창 프로시저**와 다릅니다.|
|**메뉴 이름**|이 클래스의 창과 연결된 주 메뉴의 이름입니다(메뉴가 없는 경우 “none”).|
|**아이콘 핸들**|이 클래스의 창과 연결된 아이콘의 핸들입니다(아이콘이 없는 경우 “none”).|
|**커서 핸들**|이 클래스의 창과 연결된 커서의 핸들입니다(커서가 없는 경우 “none”).|
|**배경 브러시**|이 클래스의 창과 연결된 배경 브러시의 핸들이거나, 창 배경을 그리기 위한 미리 정의된 COLOR_* 색 중 하나입니다(브러시가 없는 경우 “none”).|