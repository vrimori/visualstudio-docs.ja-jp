---
title: RegPkg パッケージ登録のトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6b95b440d83b8f7158dadb2d757b6d5b1d1f392
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245090"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg パッケージ登録のトラブルシューティング
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
>  .Pkgdef ファイルを使用する Visual Studio でパッケージを登録することをお勧めです。 これにより、拡張機能の配置、システム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成された、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)します。  
  
 RegPkg でを使用してパッケージを登録する[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、RegPkg パッケージに適しているのバージョンを使用する必要があります。  
  
## <a name="regpkg-versions-related-to-package-versions"></a>パッケージのバージョンに関連する RegPkg バージョン  
 RegPkg の 2 つのバージョンがあります。 1 つのバージョンが含まれている[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 使用して、次のアセンブリのいずれかによって作成されたパッケージを登録するのにには、このバージョンを使用します。  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 以前の Microsoft.VisualStudio.Shell.dll assembly を使用して作成されたパッケージを登録することはできません。  
  
 RegPkg の以前のバージョンでは、Microsoft.VisualStudio.Shell.dll assembly を使用して作成されたパッケージを登録できます。 ただし、そのアセンブリのそれ以降のバージョンを使用してビルドされたパッケージを登録することはできません。  
  
## <a name="see-also"></a>関連項目  
 [製品のリリース](../../misc/releasing-a-visual-studio-integration-product.md)

