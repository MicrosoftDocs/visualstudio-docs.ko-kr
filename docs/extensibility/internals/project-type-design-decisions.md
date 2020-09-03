---
title: 프로젝트 형식 디자인 결정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706367"
---
# <a name="project-type-design-decisions"></a>프로젝트 형식 디자인 결정
새 프로젝트 형식을 만들기 전에 프로젝트 형식에 대 한 몇 가지 디자인 결정을 내려야 합니다. 프로젝트에 포함 되는 항목의 형식, 프로젝트 파일이 유지 되는 방법 및 사용할 약정 모델을 결정 해야 합니다.

## <a name="project-items"></a>프로젝트 항목
 프로젝트에서 파일 또는 추상 개체를 사용 하나요? 파일을 사용 하는 경우 참조 기반 파일이 나 디렉터리 기반 파일이 되나요? 파일이 나 추상 개체가 로컬 또는 원격 중 어디에 있나요?

 프로젝트의 항목은 파일이 될 수도 있고, 데이터베이스 리포지토리의 개체 또는 인터넷을 통한 데이터 연결 등의 더 추상적인 개체 일 수도 있습니다. 항목이 파일인 경우 프로젝트는 참조 기반 또는 디렉터리 기반 프로젝트 일 수 있습니다.

 참조 기반 프로젝트에서는 두 개 이상의 프로젝트에 항목이 표시 될 수 있습니다. 그러나 항목이 나타내는 실제 파일은 한 디렉터리에만 있습니다. 디렉터리 기반 프로젝트에서 모든 프로젝트 항목이 디렉터리 구조에 존재 합니다.

 로컬 항목은 응용 프로그램이 설치 된 컴퓨터와 같은 컴퓨터에 저장 됩니다. 원격 항목은 로컬 네트워크 또는 인터넷의 다른 위치에 있는 별도의 서버에 저장할 수 있습니다.

## <a name="project-file-persistence"></a>프로젝트 파일 지 속성
 데이터는 일반적인 플랫 파일 시스템이 나 구조적 저장소에 저장 되나요? 표준 편집기나 프로젝트 관련 편집기를 사용 하 여 파일을 열 까 요?

 데이터를 유지 하기 위해 대부분의 응용 프로그램은 데이터를 파일에 저장 한 다음 사용자가 정보를 검토 하거나 변경 해야 하는 경우 다시 읽습니다.

 복합 파일이 라고도 하는 구조적 저장소는 일반적으로 여러 COM (구성 요소 개체 모델) 개체에서 지속형 데이터를 단일 파일에 저장 해야 하는 경우에 사용 됩니다. 구조적 저장소를 사용 하면 여러 가지 소프트웨어 구성 요소에서 단일 디스크 파일을 공유할 수 있습니다.

 프로젝트의 항목에 대 한 지 속성과 관련 하 여 고려해 야 할 몇 가지 옵션이 있습니다. 다음 옵션 중 하나를 수행할 수 있습니다.

- 변경 된 각 파일을 개별적으로 저장 합니다.

- 단일 **저장** 작업에서 많은 트랜잭션을 캡처합니다.

- 로컬에서 파일을 저장 한 다음 서버에 게시 하거나, 항목이 원격 개체에 대 한 데이터 연결을 나타내는 경우 다른 방법을 사용 하 여 프로젝트 항목을 저장 합니다.

  지 속성에 대 한 자세한 내용은 [프로젝트 지 속성](../../extensibility/internals/project-persistence.md) 및 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)을 참조 하세요.

## <a name="project-commitment-model"></a>프로젝트 약정 모델
 지속형 데이터 개체를 직접 모드 또는 트랜잭션 모드에서 열 까 요?

 직접 모드에서 데이터 개체를 열면 데이터에 적용 된 변경 내용이 즉시 통합 되거나 사용자가 수동으로 파일을 저장 합니다.

 트랜잭션 모드를 사용 하 여 데이터 개체를 열면 변경 내용이 메모리의 임시 위치에 저장 되 고 사용자가 수동으로 파일을 저장 하도록 선택할 때까지 커밋되지 않습니다. 이때 모든 변경 내용이 함께 발생 하거나 변경 내용이 적용 되지 않습니다.

## <a name="see-also"></a>참고 항목
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
- [프로젝트 지속성](../../extensibility/internals/project-persistence.md)
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)
- [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)
- [프로젝트 형식 만들기](../../extensibility/internals/creating-project-types.md)
