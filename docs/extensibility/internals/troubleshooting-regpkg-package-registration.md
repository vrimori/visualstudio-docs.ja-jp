---
title: RegPkg パッケージ登録のトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5424ca9a1a51088a020d04faa55754ad487d5723
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910538"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg パッケージ登録のトラブルシューティング
> [!NOTE]
>  .Pkgdef ファイルを使用する Visual Studio でパッケージを登録することをお勧めです。 これにより、拡張機能の配置、システム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成された、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)します。  
  
 RegPkg でを使用してパッケージを登録する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、RegPkg パッケージに適しているのバージョンを使用する必要があります。  
  
## <a name="regpkg-versions-related-to-package-versions"></a>パッケージのバージョンに関連する RegPkg バージョン  
 RegPkg の 2 つのバージョンがあります。 1 つのバージョンが含まれている[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 使用して、次のアセンブリのいずれかによって作成されたパッケージを登録するのにには、このバージョンを使用します。  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   以前の Microsoft.VisualStudio.Shell.dll assembly を使用して作成されたパッケージを登録することはできません。  
  
   RegPkg の以前のバージョンでは、Microsoft.VisualStudio.Shell.dll assembly を使用して作成されたパッケージを登録できます。 ただし、そのアセンブリのそれ以降のバージョンを使用してビルドされたパッケージを登録することはできません。  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../../extensibility/internals/vspackages.md)