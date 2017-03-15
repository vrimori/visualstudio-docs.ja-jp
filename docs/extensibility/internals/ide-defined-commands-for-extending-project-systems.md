---
title: "プロジェクト システムを拡張するためのコマンドの IDE 定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8ef8f9d3bd75057708f7e1d380da83a38d7efb4b
ms.lasthandoff: 02/22/2017

---
# <a name="ide-defined-commands-for-extending-project-systems"></a>プロジェクト システムを拡張するための IDE 定義のコマンド
プロジェクト システムを拡張する場合は、コマンドを使用して、コマンドによって提供されるグループ、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。  
  
 次のセクションでは、プロジェクト システムを拡張する場合に特に便利にあるコマンド項目を一覧表示します。  
  
## <a name="command-menus"></a>コマンド メニュー  
 次の表は、プロジェクト エクステンダーを呼び出す高レベルのコマンドを配置するための便利な場所には、コマンド メニューを示しています。  
  
|コマンド メニュー|説明|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**プロジェクト**トップレベルのメニュー。|  
|IDM_VS_TOOL_PROJWIN|**ソリューション エクスプ ローラー**ツールバーです。|  
  
## <a name="shortcut-menus"></a>ショートカット メニュー  
 次の表に、ショートカット メニューで、単一のノードが選択したときに適用される、**ソリューション エクスプ ローラー**、または複数同種の選択項目がある場合に、**ソリューション エクスプ ローラー**、これは、選択したすべてのノードが同じ型の場合。  
  
|ショートカット メニュー|説明|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|プロジェクト ノードを選択すると適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|ファイルが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|フォルダーが選択されている場合に適用されます。|  
|IDM_VS_CTXT_WEBREFFOLDER|Web 参照フォルダーが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|「参照」と呼ばれる参照のルート ノードが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE></xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|参照ノードが選択されている場合に適用されます。アセンブリ、COM、およびプロジェクトの参照のみが含まれます。 Web 参照は含まれません。|  
  
 次の表に、適用するときにショートカット メニューの選択内容、**ソリューション エクスプ ローラー**複数の階層にわたる  
  
|ショートカット メニュー|説明|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|現在の選択には、ソリューション ノード、プロジェクトのルート ノードが含まれている場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|現在の選択には、ソリューション ノード、プロジェクト項目が含まれている場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|現在の選択は、複数のルート プロジェクト ノードのみで構成される場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|現在の選択には、さまざまなプロジェクトのルート ノード、およびプロジェクト項目が含まれている場合に適用されます。 さらに、選択範囲には、ソリューション ノードを含めることができます。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|ソリューションでは、複数のプロジェクトからプロジェクト項目が現在の選択範囲に含まれている場合、または異なる種類のアイテムが同じプロジェクトで選択したときに適用されます。|  
  
## <a name="command-groups"></a>コマンド グループ  
 次の表は、プロジェクトを拡張して、を介してアクセス可能なときに使用できるコマンドのグループ、<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>ショートカット メニュー</xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> 。  
  
|コマンド グループ|説明|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|構築、再構築、およびプロジェクトを配置するためのコマンド。|  
|IDG_VS_CTXT_COMPILELINK|コンパイルとリンク、プロジェクトのコマンド。|  
|IDG_VS_CTXT_PROJECT_CONFIG|プロジェクト構成を設定し、ビルドの順序コマンドです。|  
|IDG_VS_CTXT_PROJECT_ADD|項目をプロジェクトに追加するコマンドです。|  
|IDG_VS_CTXT_PROJECT_START|F5 キーに関連付けられているスタートアップ プロジェクトを設定するコマンドです。|  
|IDG_VS_CTXT_PROJECT_SAVE|プロジェクト項目を保存するためのコマンドです。|  
|IDG_VS_CTXT_PROJECT_DEBUG|デバッグ用のコマンドです。|  
|IDG_VS_CTXT_PROJECT_SCC|ソース管理のためのコマンド。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|切り取り、用のコマンドは、コピーおよび貼り付け操作します。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|アクセスを提供する、**プロジェクトのプロパティ** ダイアログ ボックス。|  
  
## <a name="see-also"></a>関連項目  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommand と OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [ボタンの再利用可能なグループを作成します。](../../extensibility/creating-reusable-groups-of-buttons.md)
