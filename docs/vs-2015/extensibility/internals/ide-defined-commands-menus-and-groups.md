---
title: IDE 定義コマンド、メニューのおよびグループ |Microsoft Docs
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
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20fc9e69224f45a5e50462d38b4b2001e3122b49
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776760"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定義コマンド、メニュー、およびグループ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

によって使用される多くのメニューのコマンドおよびコマンド グループが定義済み、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。 これらのコマンドを拡張するときにもご利用いただけます[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
## <a name="finding-environment-defined-commands"></a>環境定義コマンドを見つける  
 環境のコマンドは、一連の 4 つの .vsct ファイルで定義されます。  
  
- SharedCmdDef.vsct  
  
- SharedCmdPlace.vsct  
  
- ShellCmdDef.vsct  
  
- ShellCmdPlace.vsct  
  
  これらのファイルにある *\<Visual Studio SDK インストール パス >* \VisualStudioIntegration\Common\Inc\\します。 これらのファイルは、定義と、メニューとメニューのグループ、およびコマンドの独自のコンテナーとして、VSPackage のコマンド テーブル (.vsct) の構成ファイルを使用できるグループの Guid を提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio メニューの GUID および ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Visual Studio のメニュー バーでメニューおよびが含まれているグループの GUID と ID 値を示します。  
  
 [Visual Studio ツール バーの GUID および ID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Visual Studio IDE でツールバーおよびが含まれているグループの GUID と ID 値を示します。  
  
 [Visual Studio コマンドの GUID および ID](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Visual Studio IDE で定義されているコマンドの GUID と ID の値を示します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [プロジェクト システムを拡張するための IDE 定義コマンド](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [VSPackage でユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

