---
title: "プロジェクト システムを拡張するためのコマンドの IDE 定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3b450a55de29e112d158cb783ad366eb4fbcaca7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>プロジェクト システムを拡張するための IDE 定義のコマンド
プロジェクト システムを拡張する場合は、コマンドを使用してコマンドによって提供されるグループ、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
 次のセクションはプロジェクト システムを拡張するために特に役立ちますコマンド項目を一覧表示します。  
  
## <a name="command-menus"></a>コマンド メニュー  
 次の表は、プロジェクトのエクステンダーを呼び出す高レベルのコマンドを配置するための場所は便利コマンド メニューを示します。  
  
|コマンド メニュー|説明|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**プロジェクト**トップレベルのメニュー。|  
|IDM_VS_TOOL_PROJWIN|**ソリューション エクスプ ローラー**ツールバー。|  
  
## <a name="shortcut-menus"></a>ショートカット メニュー  
 次の表に、ショートカット メニューで、単一のノードが選択したときに適用される、**ソリューション エクスプ ローラー**で選択した複数の同種がある場合や、**ソリューション エクスプ ローラー**、ときに選択したすべてのノードでは、同じ型です。  
  
|ショートカット メニュー|説明|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|プロジェクト ノードが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|ファイルが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|フォルダーが選択されている場合に適用されます。|  
|IDM_VS_CTXT_WEBREFFOLDER|Web 参照フォルダーが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|「参照」と呼ばれる参照ルート ノードが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|参照ノードが選択されている場合に適用されます。アセンブリ、COM、およびプロジェクトの参照のみが含まれます。 Web 参照は含まれません。|  
  
 次の表に、ときに使用されるショートカット メニューの選択内容、**ソリューション エクスプ ローラー**にまたがる複数の階層  
  
|ショートカット メニュー|説明|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|現在の選択範囲には、ソリューション ノードとプロジェクトのルート ノードが含まれている場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|現在の選択範囲には、ソリューション ノードとプロジェクト項目が含まれている場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|現在の選択は、複数のルート プロジェクト ノードのみで構成される場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|現在の選択範囲には、プロジェクトのルート ノードとプロジェクト アイテムの組み合わせが含まれている場合に適用されます。 さらに、選択範囲には、ソリューション ノードがあります。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|現在の選択範囲には、ソリューションでは、複数のプロジェクトからプロジェクト項目が含まれている場合、または同じプロジェクト内のさまざまな種類の項目が選択されているときに適用されます。|  
  
## <a name="command-groups"></a>コマンド グループ  
 次の表は、プロジェクトを拡張して、を介してアクセス可能なときに使用できるコマンド グループ、<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>ショートカット メニュー。  
  
|コマンド グループ|説明|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|ビルド、再構築、およびプロジェクトを配置するためのコマンド。|  
|IDG_VS_CTXT_COMPILELINK|コンパイルとリンク、プロジェクト用のコマンド。|  
|IDG_VS_CTXT_PROJECT_CONFIG|プロジェクト構成を設定し、ビルドの順序コマンド。|  
|IDG_VS_CTXT_PROJECT_ADD|項目をプロジェクトに追加されるコマンド。|  
|IDG_VS_CTXT_PROJECT_START|F5 キーに関連付けられているスタートアップ プロジェクトを設定するコマンド。|  
|IDG_VS_CTXT_PROJECT_SAVE|プロジェクト項目の保存用のコマンド。|  
|IDG_VS_CTXT_PROJECT_DEBUG|デバッグ用のコマンド。|  
|IDG_VS_CTXT_PROJECT_SCC|ソース管理用のコマンド。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|切り取り、コマンドでは、コピーし、貼り付けの操作です。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|アクセスを提供するコマンド、**プロジェクト プロパティ** ダイアログ ボックス。|  
  
## <a name="see-also"></a>参照  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommand と OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [再利用可能なボタンのグループの作成](../../extensibility/creating-reusable-groups-of-buttons.md)