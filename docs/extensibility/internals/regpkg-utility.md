---
title: "RegPkg ユーティリティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "regpkg 登録ユーティリティ"
  - "登録には、regpkg ユーティリティ"
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# RegPkg ユーティリティ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  .Pkgdef ファイルを使用する Visual Studio でパッケージを登録することをお勧めです。 これにより、拡張機能のデプロイ、VSIX の展開の要件は、システム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成される、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)です。 Visual Studio パッケージの展開の詳細については、次を参照してください。 [Visual Studio 拡張機能を配布](../../extensibility/shipping-visual-studio-extensions.md)します。  
  
 RegPkg.exe ユーティリティに登録を VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 展開用に準備します。 このユーティリティは、VSPackage 開発中にバック グラウンドで使用されます。 ビルドして、実験用ハイブに VSPackage を実行できるように、ビルド プロセスの一部として実行されます。  
  
 RegPkg は、複数の形式でシステム レジストリのスクリプトを生成できます。 .Msi プロジェクトまたは Windows Installer XML Toolset ファイルなどの展開プロジェクトでこれらのスクリプトを組み込むことができます。  
  
 RegPkg.exe は一般にある \<*Visual Studio SDK インストール パス*\> \\VisualStudioIntegration\\Tools\\Bin\\RegPkg.exe します。 RegPkg は、この構文を次に示します。  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 \/root:root  
 指定された名前の登録を実行します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ルートです。  
  
 \/regfile:FileName  
 レジストリを更新するのではなく、.reg ファイルを作成します。  \/Vrgfile または\/rgsfile および\/wixfile は使用できません。  
  
 \/rgsfile:FileName  
 レジストリを更新するのではなく、.rgs ファイルを作成します。  \/Vrgfile または\/regfile\/wixfile には使用できません。  
  
 \/vrgfile:FileName  
 レジストリを更新するのではなく、.vrg ファイルを作成します。  \/Regfile または\/rgsfile および\/wixfile は使用できません。  
  
 \/rgm  
 Rg ファイルだけでなく .rgm ファイルを作成します。  \/Rgsfile と組み合わせる必要があります。  
  
 \/wixfile:FileName  
 レジストリを更新するのではなく、Windows Installer XML ツールセットと互換性のあるファイルを作成します。  \/Regfile または\/rgsfile および\/vrgfile は使用できません。  
  
 \/codebase  
 アセンブリではなく、コードベースでの登録を強制します。  
  
 \/assembly  
 コードベースではなく、アセンブリで強制登録します。  
  
 \/unregister  
 このパッケージの登録を解除します。  使用することはできません。  
  
 \/regfile または\/vrgfile または\/rgsfile および\/wixfile です。  
  
## 参照  
 [製品のリリース](../../misc/releasing-a-visual-studio-integration-product.md)   
 [トラブルシューティングの RegPkg パッケージの登録](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)