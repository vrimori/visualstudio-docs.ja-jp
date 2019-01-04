---
title: RegPkg ユーティリティ |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3f9eecfaeffd19ece7e0ca2fe14e3f95556503d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904878"
---
# <a name="regpkg-utility"></a>RegPkg ユーティリティ
> [!NOTE]
>  .Pkgdef ファイルを使用する Visual Studio でパッケージを登録することをお勧めです。 これにより、拡張機能の配置、VSIX 展開の要件であるシステム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成された、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)します。 Visual Studio パッケージの配置の詳細については、次を参照してください。 [Visual Studio 拡張機能の配布](../../extensibility/shipping-visual-studio-extensions.md)します。  
  
 RegPkg.exe ユーティリティによる VSPackage の登録[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]して展開用に準備します。 VSPackage 開発中にバック グラウンドでこのユーティリティを使用します。 ビルドして、実験用ハイブで VSPackage を実行できるように、ビルド プロセスの一部として実行されます。  
  
 RegPkg は、複数の形式でシステム レジストリのスクリプトを生成できます。 .Msi プロジェクトや Windows Installer XML Toolset ファイルなどの展開プロジェクトでこれらのスクリプトを組み込むことができます。  
  
 RegPkg.exe は通常\< *Visual Studio SDK インストール パス*> \VisualStudioIntegration\Tools\Bin\RegPkg.exe します。 RegPkg は、この構文を次に示します。  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root:root  
 指定された名前の登録を実行します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ルート。  
  
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
 [VSPackage](../../extensibility/internals/vspackages.md)  
 [RegPkg パッケージ登録のトラブルシューティング](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)