---
title: RegPkg ユーティリティ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d793097034dde050c8a3f45a1f227603e4a64d3e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533529"
---
# <a name="regpkg-utility"></a>RegPkg ユーティリティ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[RegPkg ユーティリティ](https://docs.microsoft.com/visualstudio/extensibility/internals/regpkg-utility)します。  
  
> [!NOTE]
>  .Pkgdef ファイルを使用する Visual Studio でパッケージを登録することをお勧めです。 これにより、拡張機能の配置、VSIX 展開の要件であるシステム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成された、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)します。 Visual Studio パッケージの配置の詳細については、次を参照してください。 [Visual Studio 拡張機能の配布](../../extensibility/shipping-visual-studio-extensions.md)します。  
  
 RegPkg.exe ユーティリティによる VSPackage の登録[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]して展開用に準備します。 VSPackage 開発中にバック グラウンドでこのユーティリティを使用します。 ビルドして、実験用ハイブで VSPackage を実行できるように、ビルド プロセスの一部として実行されます。  
  
 RegPkg は、複数の形式でシステム レジストリのスクリプトを生成できます。 .Msi プロジェクトや Windows Installer XML Toolset ファイルなどの展開プロジェクトでこれらのスクリプトを組み込むことができます。  
  
 RegPkg.exe は通常\< *Visual Studio SDK インストール パス*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe します。 RegPkg は、この構文を次に示します。  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 指定された名前の登録を実行します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ルート。  
  
 /regfile:FileName  
 レジストリを更新するのではなく、.reg ファイルを作成します。  /Vrgfile または/rgsfile/wixfile では使用できません。  
  
 /rgsfile:FileName  
 レジストリを更新するのではなく、.rgs ファイルを作成します。  /Vrgfile または/regfile/wixfile では使用できません。  
  
 /vrgfile:FileName  
 レジストリを更新するのではなく、.vrg ファイルを作成します。  /Regfile または/rgsfile/wixfile では使用できません。  
  
 /rgm  
 Rgs ファイルだけでなく .rgm ファイルを作成します。  /Rgsfile と組み合わせる必要があります。  
  
 /wixfile:FileName  
 レジストリを更新するのではなく、Windows Installer XML ツールセットと互換性のあるファイルを作成します。  /Regfile または/rgsfile/vrgfile では使用できません。  
  
 /codebase  
 アセンブリではなく、コードベースで強制的に登録します。  
  
 /assembly  
 コードベースではなく、アセンブリを強制的に登録します。  
  
 /登録解除  
 このパッケージを登録解除します。  使用することはできません。  
  
 /regfile または/vrgfile または/rgsfile または/wixfile します。  
  
## <a name="see-also"></a>関連項目  
 [製品のリリース](../../misc/releasing-a-visual-studio-integration-product.md)   
 [RegPkg パッケージ登録のトラブルシューティング](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)

