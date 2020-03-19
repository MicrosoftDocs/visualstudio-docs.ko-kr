---
title: 클래스 디자이너 오류
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc8b2c013a3e685a6071f4a12d63e3ca475051a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596517"
---
# <a name="class-designer-errors"></a>클래스 디자이너 오류

**클래스 디자이너**는 소스 파일 위치를 추적하지 않으므로 프로젝트 구조를 수정하거나 프로젝트에서 소스 파일을 이동하면 **클래스 디자이너**가 유형을 추적하지 못할 수 있습니다. 예를 들어, typedef, 기본 클래스 및 연결 형식 등의 소스 유형을 수정하는 것이 일반적입니다. **클래스 디자이너에서 이 형식을 표시할 수 없습니다.** 와 같은 오류가 발생할 수 있습니다. 이러한 오류를 해결하려면 수정되거나 위치가 변경된 소스 코드를 클래스 다이어그램으로 끌어서 다시 표시합니다.

## <a name="resources"></a>리소스

다음 리소스에서 다른 오류 및 경고에 대한 도움말을 찾을 수 있습니다.

- [Visual C++ 코드 작업](working-with-visual-cpp-code.md)은 클래스 다이어그램에 C++를 표시하는 것과 관련된 문제 해결 정보를 포함합니다.
- [Visual Studio 클래스 디자이너 포럼](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner)은 **클래스 디자이너** 관련 질문을 위한 포럼을 제공합니다.

## <a name="see-also"></a>참고 항목

- [클래스와 형식 디자인 및 보기](designing-and-viewing-classes-and-types.md)
