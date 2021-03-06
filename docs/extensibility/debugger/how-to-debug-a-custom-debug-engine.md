---
title: '방법: 사용자 지정 디버그 엔진 디버깅 | Microsoft Docs'
description: Visual Studio를 사용 하 여 사용자 지정 디버그 엔진 또는 사용자 지정 프로젝트 형식을 디버깅 하는 데 사용할 수 있는 단계에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffd21fb08e920209d47ff66feb436f8a83aab53e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059927"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>방법: 사용자 지정 디버그 엔진 디버깅
프로젝트 형식은 메서드에서 디버그 엔진 (DE)을 시작 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> . 이는 프로젝트 형식을 제어 하는 인스턴스의 제어에서 DE가 시작 됨을 의미 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 그러나이 인스턴스는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE를 디버그할 수 없습니다. 사용자 지정 DE를 디버그할 수 있도록 하는 단계는 다음과 같습니다.

> [!NOTE]
> : "사용자 지정 디버그 엔진 디버그" 절차에서 프로 파일에 연결 하기 전에 DE가 시작 될 때까지 기다려야 합니다. DE가 시작 될 때 표시 되는 DE-DE의 시작 부분 근처에 메시지 상자를 놓으면 해당 지점에서 연결 하 고 메시지 상자의 선택을 취소 하 여 계속할 수 있습니다. 이렇게 하면 모든 DE 이벤트를 catch 할 수 있습니다.

> [!WARNING]
> 다음 절차를 시도 하기 전에 원격 디버깅이 설치 되어 있어야 합니다. 자세한 내용은 [원격 디버깅](../../debugger/remote-debugging.md) 을 참조 하세요.

## <a name="debug-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 디버그

1. 원격 디버그 모니터 *msvsmon.exe* 를 시작 합니다.

2. *msvsmon.exe* **도구** 메뉴에서 **옵션** 을 선택 하 여 **옵션** 대화 상자를 엽니다.

3. "인증 없음" 옵션을 선택 하 고 **확인** 을 클릭 합니다.

4. 인스턴스를 시작 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하 고 사용자 지정 DE 프로젝트를 엽니다.

5. 의 두 번째 인스턴스를 시작 하 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 고 DE를 시작 하는 사용자 지정 프로젝트를 엽니다. 개발용으로는 일반적으로 VSIP가 설치 될 때 설정 되는 실험적 레지스트리 하이브에 있습니다.

6. 의이 두 번째 인스턴스에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 지정 프로젝트에서 소스 파일을 로드 하 고 디버그할 프로그램을 시작 합니다. 몇 분 정도 기다렸다가 DE-DE를 로드 하거나 중단점에 도달할 때까지 기다립니다.

7. 첫 번째 인스턴스 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (DE 프로젝트 사용)에서 **디버그** 메뉴의 **프로세스에 연결** 을 선택 합니다.

8. **프로세스에 연결** 대화 상자에서 **전송을** **원격 (인증을 사용 하지 않는 네이티브 전용)** 으로 변경 합니다.

9. **한정자** 를 컴퓨터 이름으로 변경 합니다. (참고: 항목에 대 한 기록이 있으므로이 이름을 한 번만 입력 해야 합니다.)

10. **사용 가능한 프로세스** 목록에서 실행 중인 DE 인스턴스를 선택 하 고 **연결** 단추를 클릭 합니다.

11. 기호를 DE에 로드 한 후에는 중단점을 DE 코드에 넣습니다.

12. 디버깅 프로세스를 중지 한 다음 다시 시작할 때마다 6 ~ 10 단계를 반복 합니다.

## <a name="debug-a-custom-project-type"></a>사용자 지정 프로젝트 형식 디버깅

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]일반 레지스트리 hive에서 시작 하 고 프로젝트 형식 프로젝트 (프로젝트 형식의 인스턴스화가 아닌 프로젝트 형식에 대 한 소스)를 로드 합니다.

2. 프로젝트 속성을 열고 **디버그** 페이지로 이동 합니다. **명령** 에 IDE 경로를 입력 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (기본적으로 *[drive]* Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. **명령 인수** 에서 `/rootsuffix exp` 실험적 레지스트리 hive (VSIP를 설치할 때 만들어짐)에 대해을 입력 합니다.

4. **확인** 을 클릭하여 변경 내용을 수락합니다.

5. **F5** 키를 눌러 프로젝트 형식을 시작 합니다. 그러면의 두 번째 인스턴스가 시작 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 됩니다.

6. 이 시점에서 프로젝트 형식 소스 코드에 중단점을 추가할 수 있습니다.

7. 의 두 번째 인스턴스에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 형식의 새 인스턴스를 로드 하거나 만듭니다. 로드 또는 생성 중에 중단점이 적중 될 수 있습니다.

8. 프로젝트 형식을 디버깅 합니다.

9. DE 시작 프로세스를 디버깅 하는 경우 "사용자 지정 디버그 엔진 디버그" 절차의 단계를 수행 하 여 DE-DE를 시작한 후에 연결할 수 있습니다. 이를 통해 세 가지 인스턴스를 실행할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 하나는 프로젝트 형식 소스를 위한 것이 고 다른 하나는 인스턴스화된 프로젝트 형식에 대 한 것이 고, 세 번째 인스턴스는 de-de에 연결 됩니다.

## <a name="see-also"></a>참조
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
