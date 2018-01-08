---
title: "RegPkg ユーティリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4a4a3481b6ff1a5b8af0581e2c04602073adeae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="regpkg-utility"></a>RegPkg ユーティリティ
> [!NOTE]
>  .Pkgdef ファイルを使用しては、Visual Studio でパッケージを登録することをお勧めします。 これにより、拡張機能の配置、VSIX 配置の要件をシステム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成される、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)です。 Visual Studio パッケージの展開の詳細については、次を参照してください。 [Visual Studio 拡張機能の配布](../../extensibility/shipping-visual-studio-extensions.md)です。  
  
 RegPkg.exe ユーティリティで VSPackage を登録する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]展開用に準備します。 このユーティリティは、VSPackage の開発中にバック グラウンドで使用されます。 ビルドして、実験用ハイブで VSPackage を実行できるように、ビルド プロセスの一部として実行されます。  
  
 RegPkg は、いくつかの形式でシステム レジストリ スクリプトを生成できます。 .Msi プロジェクトまたは Windows Installer XML Toolset ファイルなどの展開プロジェクトでこれらのスクリプトを組み込むことができます。  
  
 RegPkg.exe 通常は\< *Visual Studio SDK インストール パス*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe です。 RegPkg は、この構文を次に示します。  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 指定された名前の登録を実行します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ルート。  
  
 /regfile:FileName  
 レジストリを更新するのではなく、.reg ファイルを作成します。  /Vrgfile または/rgsfile/wixfile では使用できません。  
  
 /rgsfile:FileName  
 レジストリを更新するのではなく、.rgs ファイルを作成します。  /Vrgfile または/regfile/wixfile では使用できません。  
  
 /vrgfile:FileName  
 レジストリを更新するのではなく、.vrg ファイルを作成します。  /Regfile または/rgsfile/wixfile では使用できません。  
  
 /rgm  
 Rgs ファイルに加えて .rgm ファイルを作成します。  /Rgsfile と組み合わせる必要があります。  
  
 /wixfile:FileName  
 レジストリを更新するのではなく、Windows インストーラー XML ツールセットと互換性のあるファイルを作成します。  /Regfile または/rgsfile/vrgfile では使用できません。  
  
 /codebase  
 アセンブリではなく、コードベースの登録を強制的に実行します。  
  
 /assembly  
 コードベースではなく、アセンブリの登録を強制的に実行します。  
  
 /unregister  
 このパッケージの登録を解除します。  使用することはできません。  
  
 /regfile または/vrgfile または/rgsfile および/wixfile です。  
  
## <a name="see-also"></a>参照  
 [VSPackage](../../extensibility/internals/vspackages.md)  
 [RegPkg パッケージ登録のトラブルシューティング](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)