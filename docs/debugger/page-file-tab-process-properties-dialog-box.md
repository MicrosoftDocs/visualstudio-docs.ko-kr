---
title: 프로세스 속성 대화 상자, 페이지 파일 탭 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25dc3b0aca1b58c18ae4038540c14fc4dbfe4036
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904109"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>프로세스 속성 대화 상자, 페이지 파일 탭
**페이지 파일** 탭을 사용하여 프로세스의 페이징 파일을 검사할 수 있습니다. [프로세스 속성 대화 상자](../debugger/process-properties-dialog-box.md)를 표시하려면 포커스를 [프로세스 뷰](../debugger/processes-view.md) 창으로 이동합니다. 트리에서 프로세스 노드를 선택하고 **보기** 메뉴에서 **속성**을 선택합니다.

 **페이지 파일** 탭에서 다음 설정을 사용할 수 있습니다.

|입력|설명|
|-----------|-----------------|
|**페이지 파일 바이트**|이 프로세스가 페이징 파일에서 현재 사용 중인 페이지 수입니다. 페이징 파일은 프로세스에서 사용되지만 다른 파일에는 포함되지 않은 데이터 페이지를 저장합니다. 페이징 파일은 모든 프로세스에서 사용되며, 페이징 파일의 공간이 부족하면 다른 프로세스가 실행되는 동안 오류가 발생할 수 있습니다.|
|**최고 페이지 파일 바이트**|이 프로세스가 페이징 파일에서 사용한 최대 페이지 수입니다.|
|**페이지 폴트**|이 프로세스에서 실행 중인 스레드로 인한 페이지 폴트 수입니다. 페이지 폴트는 스레드가 주 메모리의 작업 집합에 없는 가상 메모리 페이지를 참조할 때 발생합니다. 따라서 페이지가 대기 목록에 있거나 이미 주 메모리에 있는 경우 또는 페이지를 공유하는 다른 프로세스에서 사용 중인 경우에는 디스크에서 해당 페이지가 검색되지 않습니다.|