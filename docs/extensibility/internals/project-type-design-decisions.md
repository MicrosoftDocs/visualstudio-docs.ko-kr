---
title: 프로젝트 유형 설계 결정 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706367"
---
# <a name="project-type-design-decisions"></a>프로젝트 형식 디자인 결정
새 프로젝트 유형을 만들기 전에 프로젝트 유형에 대해 몇 가지 설계 결정을 내려야 합니다. 프로젝트에 포함할 항목 의 유형, 프로젝트 파일이 유지되는 방법 및 사용할 약정 모델을 결정해야 합니다.

## <a name="project-items"></a>프로젝트 항목
 프로젝트에서 파일 또는 추상 개체를 사용합니까? 파일을 사용하는 경우 참조 기반 또는 디렉터리 기반 파일입니까? 파일 또는 추상 개체가 로컬 또는 원격입니까?

 프로젝트의 항목은 파일이거나 데이터베이스 리포지토리의 개체 또는 인터넷을 통해 데이터 연결과 같은 보다 추상적인 개체일 수 있습니다. 항목이 파일인 경우 프로젝트는 참조 기반 또는 디렉터리 기반 프로젝트일 수 있습니다.

 참조 기반 프로젝트에서 항목은 두 개 이상의 프로젝트에 나타날 수 있습니다. 그러나 항목이 나타내는 실제 파일은 하나의 디렉터리에만 있습니다. 디렉터리 기반 프로젝트에서는 모든 프로젝트 항목이 디렉터리 구조에 존재합니다.

 로컬 항목은 응용 프로그램이 설치된 동일한 컴퓨터에 저장됩니다. 원격 항목은 로컬 네트워크의 별도 서버 또는 인터넷의 다른 곳에 저장할 수 있습니다.

## <a name="project-file-persistence"></a>프로젝트 파일 지속성
 데이터는 공통 플랫 파일 시스템 또는 구조화 된 저장소에 저장됩니까? 표준 편집기 또는 프로젝트별 편집기에서 파일을 열수 있습니까?

 데이터를 유지하려면 대부분의 응용 프로그램은 데이터를 파일에 저장한 다음 사용자가 정보를 검토하거나 변경해야 하는 경우 다시 읽습니다.

 복합 파일이라고도 하는 구조화 저장소는 일반적으로 여러 구성 요소 개체 모델(COM) 개체가 지속성 데이터를 단일 파일에 저장해야 하는 경우에 사용됩니다. 구조화 된 스토리지를 사용하면 여러 가지 소프트웨어 구성 요소가 단일 디스크 파일을 공유할 수 있습니다.

 프로젝트의 항목에 대한 지속성과 관련하여 고려해야 할 몇 가지 옵션이 있습니다. 다음 옵션 중 하나를 수행할 수 있습니다.

- 각 파일이 변경되면 개별적으로 저장합니다.

- 단일 **저장** 작업에서 많은 트랜잭션을 캡처합니다.

- 파일을 로컬로 저장한 다음 서버에 게시하거나 다른 접근 방식을 사용하여 항목이 원격 개체에 대한 데이터 연결을 나타내는 경우 프로젝트 항목을 저장합니다.

  지속성에 대한 자세한 내용은 [프로젝트 지속성](../../extensibility/internals/project-persistence.md) 및 [프로젝트 항목 열기 및 저장을](../../extensibility/internals/opening-and-saving-project-items.md)참조하십시오.

## <a name="project-commitment-model"></a>프로젝트 약정 모델
 지속된 데이터 개체가 직접 모드 또는 트랜잭션 모드에서 열리나요?

 데이터 개체가 직접 모드에서 열리면 데이터에 대한 변경 내용이 즉시 통합되거나 사용자가 수동으로 파일을 저장할 때 통합됩니다.

 트랜잭션 모드를 사용하여 데이터 개체를 열면 변경 내용이 메모리의 임시 위치에 저장되며 사용자가 수동으로 파일을 저장하도록 선택할 때까지 커밋되지 않습니다. 이 때 모든 변경사항이 함께 발생해야 하며 변경사항은 변경되지 않습니다.

## <a name="see-also"></a>참조
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
- [프로젝트 지속성](../../extensibility/internals/project-persistence.md)
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)
- [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)
- [프로젝트 형식 만들기](../../extensibility/internals/creating-project-types.md)
