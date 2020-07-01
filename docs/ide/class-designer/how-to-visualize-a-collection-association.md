---
title: '방법: 컬렉션 형식 연결 시각화(클래스 디자이너)'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3636b6548725ddc9af0a2e28acfdda06a8821f9a
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769892"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>방법: 클래스 디자이너에서 컬렉션 형식 연결 시각화

다른 형식의 컬렉션에 해당하는 속성 및 필드를 컬렉션 형식 연결로 클래스 다이어그램에 표시할 수 있습니다. 일반 연결은 필드 또는 속성을 소유 클래스와 필드 형식을 연결하는 선으로 표시하지만, 컬렉션 형식 연결은 소유 클래스와 수집된 형식을 연결하는 선으로 표시합니다.

## <a name="to-create-a-collection-association"></a>컬렉션 형식 연결을 만들려면

1. 코드에서 해당 형식이 강력한 형식의 컬렉션인 속성 또는 필드를 만듭니다.

2. 클래스 다이어그램에서 속성 및 필드가 표시되도록 클래스를 확장합니다.

3. 클래스에서 필드나 속성을 마우스 오른쪽 단추로 클릭하고 **컬렉션 형식 연결로 표시**를 선택합니다.

속성 또는 필드가 수집된 형식과 연결된 형식 연결 선으로 표시됩니다.

## <a name="see-also"></a>참고 항목

- [방법: 형식 간에 연결 만들기](how-to-create-associations-between-types.md)
- [클래스 및 형식 디자인](designing-and-viewing-classes-and-types.md)
