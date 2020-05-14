---
title: '방법: 사용자 지정 디버그 엔진 디버그 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738581"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>방법: 사용자 지정 디버그 엔진 디버그
프로젝트 형식은 메서드에서 DE버그 엔진(DE)을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 시작합니다. 즉, DE는 프로젝트 형식을 제어하는 인스턴스의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제어하에 시작됩니다. 그러나 해당 인스턴스는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE를 디버깅할 수 없습니다. 다음은 사용자 지정 DE를 디버깅할 수 있는 단계입니다.

> [!NOTE]
> : "사용자 지정 디버그 엔진 디버그" 절차에서는 DE가 시작될 때까지 기다려야 연결됩니다. DE가 시작될 때 나타나는 DE의 시작 부분에 메시지 상자를 배치하면 해당 시점에 연결한 다음 메시지 상자를 지우고 계속할 수 있습니다. 이렇게 하면 모든 DE 이벤트를 catch할 수 있습니다.

> [!WARNING]
> 다음 절차를 시도하기 전에 원격 디버깅이 설치되어 있어야 합니다. 자세한 내용은 [원격 디버깅을](../../debugger/remote-debugging.md) 참조하십시오.

## <a name="debug-a-custom-debug-engine"></a>사용자 지정 디버그 엔진 디버그

1. *msvsmon.exe,* 원격 디버그 모니터를 시작합니다.

2. *msvsmon.exe의* **도구** 메뉴에서 **옵션** 대화 상자를 열려면 **옵션을** 선택합니다.

3. "인증 없음" 옵션을 선택하고 **확인을**클릭합니다.

4. 사용자 지정 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE 프로젝트의 인스턴스를 시작하고 엽니다.

5. DE를 시작하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 지정 프로젝트를 두 번째 인스턴스를 시작하고 엽니다(개발의 경우 일반적으로 VSIP가 설치될 때 설정된 실험 레지스트리 하이브에 있음).

6. 이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]두 번째 인스턴스에서는 사용자 지정 프로젝트에서 소스 파일을 로드하고 디버깅할 프로그램을 시작합니다. DE가 로드될 때까지 잠시 기다리거나 중단점이 적중될 때까지 기다립니다.

7. DE 프로젝트의 첫 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 번째 인스턴스에서 **디버그** 메뉴에서 **프로세스에 연결을** 선택합니다.

8. **프로세스에 연결** 대화 상자에서 **원격으로 전송을** **변경합니다(인증없이 네이티브만).**

9. **한정자를** 컴퓨터 이름으로 변경합니다(참고: 항목 기록이 있으므로 이 이름을 한 번만 입력해야 합니다).

10. 사용 **가능한 프로세스** 목록에서 실행 중인 DE의 인스턴스를 선택하고 **연결** 단추를 클릭합니다.

11. 기호가 DE에 로드된 후 DE 코드에 중단점을 배치합니다.

12. 디버깅 프로세스를 중지한 다음 다시 시작할 때마다 6단계부터 10단계까지 반복합니다.

## <a name="debug-a-custom-project-type"></a>사용자 지정 프로젝트 유형 디버그

1. 일반 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 레지스트리 하이브에서 시작하여 프로젝트 유형 프로젝트를 로드합니다(프로젝트 형식의 인스턴스화가 아니라 프로젝트 유형에 대한 소스).

2. 프로젝트 속성을 열고 **디버그** 페이지로 이동합니다. **명령의**경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에 대한 경로를 입력합니다(기본적으로 *[드라이브]* \프로그램 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 파일\Microsoft 8\Common7\IDE\devenv.exe).

3. 명령 **인수의**경우 `/rootsuffix exp` 실험 레지스트리 하이브(VSIP가 설치되었을 때 생성됨)에 대해 입력합니다.

4. **확인** 을 클릭하여 변경 내용을 수락합니다.

5. **F5를**눌러 프로젝트 유형을 시작합니다. 그러면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 두 번째 인스턴스가 시작됩니다.

6. 이 시점에서 프로젝트 유형 소스 코드에 중단점을 배치할 수 있습니다.

7. 의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]두 번째 인스턴스에서 프로젝트 유형의 새 인스턴스를 로드하거나 만듭니다. 로드 또는 생성 중에 중단점이 적중될 수 있습니다.

8. 프로젝트 유형을 디버깅합니다.

9. DE를 시작하는 프로세스를 디버깅하도록 선택한 경우 "사용자 지정 디버그 엔진 디버그" 절차에서 단계를 수행하여 DE를 시작한 후 연결합니다. 이렇게 하면 프로젝트 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 형식 소스에 대한 인스턴스, 인스턴스화된 프로젝트 형식에 대한 두 번째 인스턴스, DE에 연결된 세 가지 인스턴스의 실행 인스턴스가 있습니다.

## <a name="see-also"></a>참조
- [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)
