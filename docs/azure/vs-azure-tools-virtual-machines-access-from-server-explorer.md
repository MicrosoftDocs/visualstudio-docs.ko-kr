---
title: 서버 탐색기에서 Azure Virtual Machines 액세스 | Microsoft Docs
description: Visure Studio에서 Azure 서버 탐색기 (VM) 만들기 및 관리하기를 보는 방법에 대한 개요를 가져옵니다.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 8fd5d81e721bc2df7041d4cb724687e5ee540a7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911667"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>서버 탐색기에서 Azure Virtual Machines 액세스

Azure에서 호스팅되는 가상 머신이 있는 경우 서버 탐색기에서 액세스할 수 있습니다. 처음에 Azure 구독에 로그인해야 모바일 서비스를 볼 수 있습니다. 로그인하려면 서버 탐색기에서 Azure 노드에 대한 바로 가기 메뉴를 열고 **Microsoft Azure에 연결**을 선택할 수 있습니다.

1. 클라우드 탐색기에서 가상 머신을 선택한 다음 F4 키를 선택하여 속성 창을 표시합니다.

    다음의 테이블은 사용 가능하지만 모두 읽기 전용인 속성을 보여줍니다. 변경하려면 [Azure Portal](https://portal.azure.com)을 사용합니다.

   | 속성 | 설명 |
   | --- | --- |
   | DNS 이름 |가상 머신의 인터넷 주소 URL입니다. |
   | 환경 |가상 머신에 대한 이 속성의 값은 항상 프로덕션입니다. |
   | Name |가상 머신의 이름입니다. |
   | Size |사용 가능한 디스크 공간과 메모리의 양이 반영된 가상 머신의 크기입니다. 자세한 내용은 [가상 머신 크기](/azure/cloud-services/cloud-services-sizes-specs)를 참조 하세요. |
   | 상태 |값은 시작, 시작됨, 중지, 중지됨 및 상태 검색을 포함합니다. 상태 검색이 나타나면 현재 상태는 알 수 없습니다. 이 속성의 값은 [Azure Portal](https://portal.azure.com)에서 사용된 값과 다릅니다. |
   | 구독 ID |Azure 계정에 대한 구독 ID 구독에 대한 속성을 확인하여 [Azure Portal](https://portal.azure.com)에 대한 이 정보를 표시할 수 있습니다. |
2. 엔드포인트 노드를 선택하고 **속성** 창을 확인합니다.
3. 다음 테이블은 사용 가능하지만 읽기 전용인 엔드포인트 속성을 설명합니다. 가상 머신에 대해 엔드포인트를 추가하거나 편집하려면 [Azure Portal](https://portal.azure.com)을 사용합니다.

   | 속성 | 설명 |
   | --- | --- |
   | Name |엔드포인트에 대한 식별자입니다. |
   | 프라이빗 포트 |애플리케이션의 내부 네트워크 액세스 용 포트입니다. |
   | 프로토콜 |이 엔드포인트에 대한 전송 계층이 사용하는 프로토콜로, TCP 또는 UDP입니다. |
   | 공용 포트 |애플리케이션에 대한 공용 액세스에 사용되는 포트입니다. |
