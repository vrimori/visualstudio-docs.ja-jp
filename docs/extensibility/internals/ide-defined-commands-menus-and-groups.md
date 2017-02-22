---
title: "IDE 定義コマンド、メニューのおよびグループ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "環境定義のコマンド"
  - ".vsct ファイル、環境定義定数"
  - "コマンド グループ、環境で定義されています。"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# IDE 定義コマンド、メニューのおよびグループ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

多くのメニューのコマンドおよびコマンド グループは既に定義されてで使用するため、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。 これらのコマンドは拡張するときに使用できるようにも [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## 環境定義コマンドを検索します。  
 環境のコマンドは、一連の 4 つの .vsct ファイルで定義されます。  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 これらのファイルにある *\< Visual Studio SDK インストール パス \>*\\VisualStudioIntegration\\Common\\Inc\\ します。 これらのファイルは、定義と、メニューとメニューのグループ、およびコマンドのコンテナーとして、VSPackage のコマンド テーブル構成 \(.vsct\) ファイルでを使用できるグループの Guid を提供します。  
  
## このセクションの内容  
 [Guid と Visual Studio のメニューの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Visual Studio のメニュー バーのメニューおよび含まれているグループの GUID と ID 値を示します。  
  
 [Guid と Visual Studio ツールバーの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Visual Studio ide では、ツールバーの含まれているグループの GUID と ID 値を示します。  
  
 [Guid と、Visual Studio コマンドの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Visual Studio IDE で定義されているコマンドの GUID と ID の値を示します。  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [プロジェクト システムを拡張するための IDE 定義のコマンド](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)