---
title: 원격 컴퓨터에서 워크플로 디버깅 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656854"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>원격 컴퓨터에서 워크플로 디버깅(레거시)
이 항목에서는 레거시 [!INCLUDE[wf](../includes/wf-md.md)]를 사용하여 빌드된 원격 레거시 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션을 디버깅하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 애플리케이션이 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 를 설치할 때 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] 구성 요소 설치 옵션 중 하나는 용 디버거를 설치 하는 것입니다 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] . 원격 디버깅 구성 요소가 설치됩니다. 이 원격 디버깅 구성 요소는 원격 워크플로 디버깅의 대상 컴퓨터에 설치해야 합니다.

 또한 디버깅을 수행하는 데 사용되는 로컬 컴퓨터의 GAC(전역 어셈블리 캐시)에 원격 컴퓨터에서 디버깅할 레거시 워크플로의 워크플로 정의가 포함된 어셈블리를 설치해야 합니다. 예를 들어 원격 컴퓨터 A에서 실행 중인 레거시 워크플로를 로컬 컴퓨터 B에서 디버깅하는 경우, 워크플로 정의가 컴퓨터 B의 GAC에 있어야 합니다. 그러면 디자이너가 원격 컴퓨터 A에서 실행 중인 워크플로의 워크플로 마크업을 역직렬화하고 컴퓨터 B에 표시할 수 있습니다. 전역 어셈블리 캐시에 대한 자세한 내용은 MSDN Library를 참조하십시오.

 [!INCLUDE[wf2](../includes/wf2-md.md)] 원격 디버깅은 다른 구성 요소에 대 한 원격 디버깅과 동일 하 게 작동 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 자세한 내용은 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] MSDN Library에서 원격 디버깅을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)