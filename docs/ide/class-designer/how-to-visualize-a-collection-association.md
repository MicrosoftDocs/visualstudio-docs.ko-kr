---
title: 컬렉션 연결 시각화
description: 클래스 디자이너에서 컬렉션 형식 연결을 시각화하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e4e446925b2ee46bc846a3edfbf09fb2eb695ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912638"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>방법: 클래스 디자이너에서 컬렉션 형식 연결 시각화

다른 형식의 컬렉션에 해당하는 속성 및 필드를 컬렉션 형식 연결로 클래스 다이어그램에 표시할 수 있습니다. 일반 연결은 필드 또는 속성을 소유 클래스와 필드 형식을 연결하는 선으로 표시하지만, 컬렉션 형식 연결은 소유 클래스와 수집된 형식을 연결하는 선으로 표시합니다.

## <a name="to-create-a-collection-association"></a>컬렉션 형식 연결을 만들려면

1. 코드에서 해당 형식이 강력한 형식의 컬렉션인 속성 또는 필드를 만듭니다.

2. 클래스 다이어그램에서 속성 및 필드가 표시되도록 클래스를 확장합니다.

3. 클래스에서 필드나 속성을 마우스 오른쪽 단추로 클릭하고 **컬렉션 형식 연결로 표시** 를 선택합니다.

속성 또는 필드가 수집된 형식과 연결된 형식 연결 선으로 표시됩니다.

## <a name="see-also"></a>추가 정보

- [방법: 형식 간에 연결 만들기](how-to-create-associations-between-types.md)
- [클래스 및 형식 디자인](designing-and-viewing-classes-and-types.md)
