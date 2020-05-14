---
title: 솔루션 사용자 옵션(. Suo) 파일 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705312"
---
# <a name="solution-user-options-suo-file"></a>솔루션 사용자 옵션(.Suo) 파일
솔루션 사용자 옵션(.suo) 파일에는 사용자별 솔루션 옵션이 포함되어 있습니다. 이 파일은 소스 코드 제어에 체크 인해서는 안 됩니다.

 솔루션 사용자 옵션(.suo) 파일은 이진 형식으로 저장된 구조화 된 저장소 또는 복합 파일입니다. .suo 파일의 정보를 식별하는 데 사용되는 키인 스트림의 이름으로 사용자 정보를 스트림에 저장합니다. 솔루션 사용자 옵션 파일은 사용자 기본 설정 설정을 저장하는 데 사용되며 Visual Studio에서 솔루션을 저장할 때 자동으로 만들어집니다.

 환경이 .suo 파일을 열면 현재 로드된 모든 VSPackage를 열거합니다. VSPackage가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 인터페이스를 구현하는 경우 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> .suo 파일에서 모든 데이터를 로드하도록 요청하는 VSPackage의 메서드를 호출합니다.

 .suo 파일에 기록된 스트림을 아는 것은 VSPackage의 책임입니다. 작성한 각 스트림에 대해 VSPackage는 스트림의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 이름인 키로 식별되는 특정 스트림을 로드하기 위해 환경을 다시 호출합니다. 그런 다음 환경은 VSPackage를 다시 호출하여 스트림 이름과 `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 메서드에 대한 포인터를 전달하는 특정 스트림을 읽습니다.

 이 시점에서 .suo 파일의 다른 섹션을 읽어야 하는 다른 섹션이 있는지 확인하기 위해 `LoadUserOptions` 다른 호출이 이루어집니다. 이 프로세스는 .suo 파일의 모든 데이터 스트림이 환경에서 읽고 처리될 때까지 계속됩니다.

 솔루션이 저장되거나 닫히면 환경은 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 포인터를 사용하여 메서드를 호출합니다. 저장할 `IStream` 이진 정보가 포함된 메서드가 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 전달된 다음 .suo 파일에 정보를 기록한 `SaveUserOptions` 다음 메서드를 다시 호출하여 .suo 파일에 쓸 다른 정보 스트림이 있는지 확인합니다.

 이러한 두 `SaveUserOptions` 메서드 `WriteUserOptions`및 은 .suo 파일에 저장되는 각 정보 스트림에 대해 재귀적으로 호출되어. `IVsSolutionPersistence` .suo 파일에 여러 스트림을 쓸 수 있도록 재귀적으로 호출됩니다. 이러한 방식으로 사용자 정보는 솔루션과 함께 유지되며 다음에 솔루션을 열 때 사용자에게 보장됩니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [솔루션](../../extensibility/internals/solutions-overview.md)
