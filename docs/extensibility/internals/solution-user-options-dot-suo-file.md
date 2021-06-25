---
title: 솔루션 사용자 옵션(. Suo) 파일 | Microsoft Docs
description: 이진 형식으로 저장된 구조적 스토리지 파일의 사용자별 솔루션 옵션을 포함하는 솔루션 사용자 옵션(.suo) 파일에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a38eb865cf003f7a2f9bafde7b6e527ce24f2bd
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899617"
---
# <a name="solution-user-options-suo-file"></a>솔루션 사용자 옵션(.Suo) 파일
솔루션 사용자 옵션(.suo) 파일에는 사용자별 솔루션 옵션이 포함되어 있습니다. 이 파일은 소스 코드 제어에 체크 인하면 안 됩니다.

 솔루션 사용자 옵션(.suo) 파일은 이진 형식으로 저장된 구조적 스토리지 또는 복합 파일입니다. .suo 파일에서 정보를 식별하는 데 사용할 키인 스트림 이름으로 사용자 정보를 스트림에 저장합니다. 솔루션 사용자 옵션 파일은 사용자 기본 설정 설정을 저장하는 데 사용되며 Visual Studio 솔루션을 저장할 때 자동으로 만들어집니다.

 환경에서 .suo 파일을 열면 현재 로드된 모든 VSPackage가 열거됩니다. VSPackage가 인터페이스를 구현하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> VSPackage에서 메서드를 호출하여 .suo 파일에서 모든 데이터를 로드하도록 요청합니다.

 VSPackage는 .suo 파일에 기록되었을 수 있는 스트림을 알고 있어야 합니다. VSPackage는 작성한 각 스트림에 대해 를 통해 환경으로 다시 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 호출하여 스트림 이름인 키로 식별되는 특정 스트림을 로드합니다. 그런 다음, 환경에서 VSPackage를 다시 호출하여 스트림 이름과 메서드에 대한 포인터를 전달하는 특정 `IStream` 스트림을 읽습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>

 이때 `LoadUserOptions` .suo 파일에서 읽어야 하는 다른 섹션이 있는지 확인하기 위해 에 대한 또 다른 호출이 이루어집니다. 이 프로세스는 환경에서 .suo 파일의 모든 데이터 스트림을 읽고 처리할 때까지 계속됩니다.

 솔루션이 저장되거나 닫힌 경우 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 메서드에 대한 포인터를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 메서드를 호출합니다. `IStream`저장할 이진 정보를 포함하는 는 메서드에 전달된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 다음, .suo 파일에 정보를 쓰고 `SaveUserOptions` 메서드를 다시 호출하여 .suo 파일에 쓸 다른 정보 스트림이 있는지 확인합니다.

 이러한 두 메서드 `SaveUserOptions` 및 `WriteUserOptions` 는 포인터를 에 전달하여 .suo 파일에 저장할 정보의 각 스트림에 대해 재귀적으로 호출됩니다. `IVsSolutionPersistence` .suo 파일에 여러 스트림을 쓸 수 있도록 재귀적으로 호출됩니다. 이러한 방식으로 사용자 정보는 솔루션과 함께 유지되며 다음에 솔루션을 열 때 해당 위치에 있도록 보장됩니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [솔루션](../../extensibility/internals/solutions-overview.md)
