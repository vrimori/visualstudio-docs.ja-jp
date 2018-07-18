---
title: RegPkg パッケージ登録のトラブルシューティング |Microsoft ドキュメント
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
ms.openlocfilehash: 4857e41888962a92dced87d63fa2b63161ecac55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137119"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg パッケージ登録のトラブルシューティング
> [!NOTE]
>  .Pkgdef ファイルを使用しては、Visual Studio でパッケージを登録することをお勧めします。 これにより、拡張機能の配置、システム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成される、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)です。  
  
 RegPkg を使用してパッケージを登録する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]は、パッケージの適切な RegPkg のバージョンを使用する必要があります。  
  
## <a name="regpkg-versions-related-to-package-versions"></a>パッケージのバージョンに関連する RegPkg バージョン  
 RegPkg の 2 つのバージョンがあります。 1 つのバージョンが含まれる[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 次のアセンブリのいずれかを使用してビルドされているパッケージを登録するのにには、このバージョンを使用します。  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 以前 Microsoft.VisualStudio.Shell.dll assembly を使用して作成されたパッケージに登録できません。  
  
 RegPkg の以前のバージョンでは、Microsoft.VisualStudio.Shell.dll assembly を使用してビルドされているパッケージを登録できます。 ただし、そのアセンブリのそれ以降のバージョンを使用して構築されたパッケージに登録できません。  
  
## <a name="see-also"></a>関連項目  
 [VSPackage](../../extensibility/internals/vspackages.md)