---
title: 솔루션 사용자 옵션 () .Suo) 파일 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705312"
---
# <a name="solution-user-options-suo-file"></a>솔루션 사용자 옵션(.Suo) 파일
솔루션 사용자 옵션 (.suo) 파일에는 사용자별 솔루션 옵션이 포함 되어 있습니다. 이 파일은 소스 코드 제어에 체크 인 되지 않아야 합니다.

 솔루션 사용자 옵션 (.suo) 파일은 이진 형식으로 저장 된 구조화 된 저장소 또는 복합 파일입니다. .Suo 파일의 정보를 식별 하는 데 사용할 키가 되는 스트림의 이름을 스트림으로 사용자 정보를 저장 합니다. 솔루션 사용자 옵션 파일은 사용자 기본 설정을 저장 하는 데 사용 되며, Visual Studio에서 솔루션을 저장할 때 자동으로 만들어집니다.

 환경에서 .suo 파일을 열면 현재 로드 된 모든 Vspackage를 열거 합니다. VSPackage가 인터페이스를 구현 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 환경에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> VSPackage에서 메서드를 호출 하 여 .suo 파일에서 모든 데이터를 로드 하도록 요청 합니다.

 .Suo 파일에 작성 했을 수 있는 스트림을 파악 하는 것은 VSPackage의 책임입니다. VSPackage는 작성 된 각 스트림에 대해를 통해 환경을 다시 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 하 여 스트림의 이름인 키로 식별 되는 특정 스트림을 로드 합니다. 그러면 환경에서 VSPackage를 다시 호출 하 여 스트림의 이름 및 메서드에 대 한 포인터를 전달 하는 특정 스트림을 읽습니다 `IStream` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> .

 이 시점에서 다른 호출을 수행 하 여 `LoadUserOptions` 읽어야 할 .suo 파일의 다른 섹션이 있는지 확인 합니다. 이 프로세스는 .suo 파일의 모든 데이터 스트림이 환경에서 읽고 처리 될 때까지 계속 됩니다.

 솔루션을 저장 하거나 닫으면 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 메서드에 대 한 포인터를 사용 하 여 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> . `IStream`저장 될 이진 정보를 포함 하는는 메서드에 전달 되며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> ,이 메서드는 해당 정보를 .suo 파일에 쓰고 메서드를 다시 호출 `SaveUserOptions` 하 여 .suo 파일에 쓸 다른 정보 스트림이 있는지 확인 합니다.

 이러한 두 메서드인 `SaveUserOptions` 및는 `WriteUserOptions` 에 대 한 포인터를 전달 하 여 .suo 파일에 저장 되는 각 정보 스트림에 대해 재귀적으로 호출 됩니다 `IVsSolutionPersistence` . 이를 재귀적으로 호출 하 여 .suo 파일에 여러 스트림을 쓸 수 있도록 합니다. 이러한 방식으로 사용자 정보는 솔루션과 함께 유지 되며 다음에 솔루션을 열 때 해당 정보를 가지게 됩니다.

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [솔루션](../../extensibility/internals/solutions-overview.md)
