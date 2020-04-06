---
title: 보안 문제 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713044"
---
# <a name="security-issues"></a>보안 문제
Visual Studio를 사용하여 프로그램을 디버깅하려면 개발자가 프로그램을 실행하는 데 필요한 권한만 있으면 됩니다. 여기에는 대부분의 상황에서 원격 디버깅이 포함됩니다. 인터넷 정보 서비스와 같은 다른 서비스와 관련된 일부 상황에서는 더 높은 수준의 사용 권한이 필요할 수 있습니다.

 Visual Studio가 실행되는 동안 PDM 프로세스 디버그 관리자(PDM)는 로컬 컴퓨터에서 디버그 프로세스를 추적합니다. 원격으로 *msvsmon.exe라는* 프로그램은 개발자가 원격 디버깅을 처리하고 PDM을 사용할 수 있도록 하기 위해 시작됩니다. *(msvsmon.exe는* 서비스가 아니며 해당 컴퓨터에서 원격 디버깅을 활성화하려면 수동으로 시작해야 합니다.) Visual Studio(또는 *msvsmon.exe)가*실행되지 않는 경우 디버깅을 위한 프로세스가 추적되지 않습니다.

 개발자는 특별한 권한 없이 시작한 프로그램을 디버깅할 수 있습니다. 개발자는 다른 사람이 동일한 보안 그룹의 구성원인 경우 다른 사용자가 시작한 프로세스를 디버깅할 수도 있습니다. 또한 원격 디버깅을 사용하려면 필요한 파일을 원격 컴퓨터에 복사하고 *msvsmon.exe를*시작하기만 하면 됩니다. 자세한 내용은 [원격 디버깅](../../debugger/remote-debugging.md)을 참조하십시오.

## <a name="see-also"></a>참조
- [작업 디버깅](../../extensibility/debugger/debugging-tasks.md)
- [프로세스 디버그 관리자](../../extensibility/debugger/process-debug-manager.md)
- [원격 디버깅](../../debugger/remote-debugging.md)
