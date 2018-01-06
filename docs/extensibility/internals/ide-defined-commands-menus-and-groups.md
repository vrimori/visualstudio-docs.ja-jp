---
title: "IDE 定義コマンド、メニューのおよびグループ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34e0e95475457e2a5f206ad4ecb0d7e42e2bb9ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定義コマンド、メニューのおよびグループ
多くのメニューのコマンドおよびコマンド グループは既に定義されていますが使用する、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。 これらのコマンドを拡張するときにも、使用できる[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="finding-environment-defined-commands"></a>環境定義コマンドを検索します。  
 環境のコマンドは、一連の 4 つの .vsct ファイルで定義されます。  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 これらのファイルにある *\<Visual Studio SDK インストール パス >*\VisualStudioIntegration\Common\Inc\\です。 これらのファイルは、定義と、メニューとメニューのグループ、およびコマンドのコンテナーとして、VSPackage のコマンド テーブル (.vsct) の構成ファイルでを使用できるグループの Guid を提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio メニューの GUID および ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Visual Studio メニュー バーのメニューおよびが含まれているグループの GUID と ID 値を示します。  
  
 [Visual Studio ツール バーの GUID および ID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Visual Studio IDE でツールバーおよびが含まれているグループの GUID と ID 値を示します。  
  
 [Visual Studio コマンドの GUID および ID](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Visual Studio IDE で定義されているコマンドの GUID と ID 値を示します。  
  
## <a name="see-also"></a>参照  
 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [プロジェクト システムを拡張するための IDE 定義のコマンド](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)