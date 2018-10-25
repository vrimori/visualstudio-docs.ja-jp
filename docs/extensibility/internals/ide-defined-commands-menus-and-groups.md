---
title: IDE 定義コマンド、メニューのおよびグループ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 34c41608a90b15538e190be093ed2791a90824f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857277"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 定義コマンド、メニュー、およびグループ
によって使用される多くのメニューのコマンドおよびコマンド グループが定義済み、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。 これらのコマンドを拡張するときにもご利用いただけます[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
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