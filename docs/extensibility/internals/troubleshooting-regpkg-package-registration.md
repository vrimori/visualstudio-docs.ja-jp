---
title: "トラブルシューティングの RegPkg パッケージの登録 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RegPkg"
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# トラブルシューティングの RegPkg パッケージの登録
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  .Pkgdef ファイルを使用する Visual Studio でパッケージを登録することをお勧めです。 これにより、拡張機能の配置、システム レジストリにアクセスする必要はありません。 Pkgdef ファイルを使用して作成される、 [CreatePkgDef ユーティリティ](../../extensibility/internals/createpkgdef-utility.md)です。  
  
 RegPkg を使用してパッケージを登録する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 、パッケージに適した RegPkg のバージョンを使用する必要があります。  
  
## パッケージのバージョンに関連する RegPkg バージョン  
 RegPkg の 2 つのバージョンがあります。 1 つのバージョンが含まれている [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 このバージョンを使用して、次のアセンブリのいずれかを使用して組み込まれているパッケージを登録します。  
  
1.  Microsoft.VisualStudioShell.9.0.dll  
  
2.  Microsoft.VisualStudioShell.10.0.dll  
  
3.  Microsoft.VisualStudioShell.11.0.dll  
  
 以前の Microsoft.VisualStudio.Shell.dll assembly を使用して組み込まれているパッケージに登録できません。  
  
 RegPkg の以前のバージョンでは、Microsoft.VisualStudio.Shell.dll assembly を使用して組み込まれているパッケージを登録できます。 ただし、そのアセンブリの以降のバージョンを使用して構築されたパッケージを登録することはできません。  
  
## 参照  
 [製品のリリース](../../misc/releasing-a-visual-studio-integration-product.md)