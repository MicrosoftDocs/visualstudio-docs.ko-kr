---
title: PerfView를 사용하여 ETL 추적 수집
ms.date: 09/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 24d72e9630506ecc3d25fcc75e51eeb84f619e53
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271158"
---
# <a name="collect-an-etl-trace-with-perfview"></a>PerfView를 사용하여 ETL 추적 수집

PerfView는 Visual Studio와 관련된 문제를 해결하는 데 유용한 [Windows용 이벤트 추적](/windows/desktop/ETW/event-tracing-portal)을 기반으로 ETL(이벤트 추적 로그) 파일을 만드는 도구입니다. 문제를 보고하는 경우 제품 팀에서 PerfView를 실행하여 추가 정보를 수집하도록 요청하는 경우가 있습니다.

## <a name="install-perfview"></a>PerfView 설치

[GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md)에서 PerfView를 다운로드합니다.

## <a name="run-perfview"></a>PerfView 실행

1. Windows 탐색기에서 **PerfView.exe**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 관리자로 선택합니다.
1. 수집 메뉴에서 **수집**을 선택합니다.
1. **Zip**, **병합** 및 **ThreadTime**을 선택합니다.
1. **순환 MB**를 1000으로 늘립니다.
1. 두 번 이상 수집하려는 경우 **현재 디렉터리**를 변경하여 ETL 추적을 지정된 폴더 및 데이터 파일에 저장합니다.
1. 데이터 기록을 시작하려면 **컬렉션 시작** 단추를 선택합니다.
1. 데이터 기록을 중지하려면 **컬렉션 중지** 단추를 선택합니다. PrefView.etl.zip 파일은 지정된 디렉터리에 저장됩니다.

PerfView는 해당 버퍼에 적합한 최근 데이터만 저장할 수 있습니다. 따라서 Visual Studio가 중지되거나 느려지기 시작한 후에는 최대한 빨리 컬렉션을 중지하세요. 문제가 발생한 후 30초 이상 수집하지 마세요.

자세한 내용은 [Channel9의 PerfView 자습서](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command)를 확인하세요.
