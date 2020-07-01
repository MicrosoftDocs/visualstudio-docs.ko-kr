---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 054198eff46c0983a5610b29dee5e29e5ac67a70
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147092"
---
안전 하지 않은 데이터는 deserialize 할 때 취약 합니다. 공격자는 예기치 않은 형식을 포함 하도록 serialize 된 데이터를 수정 하 여 악의적인 부작용으로 개체를 주입할 수 있습니다. 예를 들어, 안전 하지 않은 역직렬 변환기에 대 한 공격은 기본 운영 체제에서 명령을 실행 하거나, 네트워크를 통해 통신 하거나, 파일을 삭제할 수 있습니다.