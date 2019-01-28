---
title: プロジェクト システムを拡張するための IDE 定義コマンド |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5964dbbd6851adc1ccf209575dc9867cd18bf1ed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953147"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>プロジェクト システムを拡張するための IDE 定義コマンド
プロジェクト システムを拡張する場合は、コマンドを使用して、コマンドによって提供されるグループ、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE。  
  
 次のセクションでは、プロジェクト システムを拡張する場合に特に役立ちますコマンド項目を一覧表示します。  
  
## <a name="command-menus"></a>コマンド メニュー  
 次の表では、プロジェクトのエクステンダーを呼び出す高レベルのコマンドを配置するための便利な場所であるコマンド メニューを示します。  
  
|コマンド メニュー|説明|  
|------------------|-----------------|  
|IDM_VS_MENU_PROJECT|**プロジェクト**の最上位メニュー。|  
|IDM_VS_TOOL_PROJWIN|**ソリューション エクスプ ローラー**ツールバー。|  
  
## <a name="shortcut-menus"></a>ショートカット メニュー  
 次の表に、ショートカット メニューで、1 つのノードが選択されているときに適用される、**ソリューション エクスプ ローラー**、または複数が同種で選択されている場合、**ソリューション エクスプ ローラー**、ときに選択したすべてのノードでは、同じ型です。  
  
|ショートカット メニュー|説明|  
|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|プロジェクト ノードが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|ファイルが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|フォルダーが選択されている場合に適用されます。|  
|IDM_VS_CTXT_WEBREFFOLDER|Web 参照フォルダーが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|「参照」と呼ばれるリファレンスのルート ノードが選択されている場合に適用されます。|  
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|参照ノードが選択されている場合に適用されます。アセンブリ、COM、およびプロジェクトの参照のみが含まれます。 Web 参照は含まれません。|  
  
 次の表は、ときに適用するショートカット メニューの選択内容、**ソリューション エクスプ ローラー**複数の階層にまたがる  
  
|ショートカット メニュー|説明|  
|-------------------|-----------------|  
|IDM_VS_CTXT_XPROJ_SLNPROJ|現在の選択範囲には、ソリューション ノード、プロジェクトのルート ノードが含まれている場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_SLNITEM|現在の選択範囲には、ソリューション ノードとプロジェクト項目が含まれている場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_MULTIPROJ|現在の選択は、複数のルート プロジェクト ノードのみで構成される場合に適用されます。|  
|IDM_VS_CTXT_XPROJ_PROJITEM|現在の選択範囲には、さまざまなプロジェクトのルート ノード、およびプロジェクト項目が含まれている場合に適用されます。 さらに、選択範囲には、ソリューション ノードを含めることができます。|  
|IDM_VS_CTXT_XPROJ_MULTIITEM|ソリューションでは、複数のプロジェクトからプロジェクト項目が現在の選択範囲に含まれている場合、または同じプロジェクト内のさまざまな種類の項目が選択されているときに適用されます。|  
  
## <a name="command-groups"></a>コマンド グループ  
 次の表は、プロジェクトに拡張してを介してアクセス可能なときに使用できるコマンド グループ、<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>ショートカット メニュー。  
  
|コマンド グループ|説明|  
|-------------------|-----------------|  
|IDG_VS_CTXT_PROJECT_BUILD|ビルド、リビルド、およびプロジェクトを配置するためのコマンド。|  
|IDG_VS_CTXT_COMPILELINK|コンパイルとリンク、プロジェクト用のコマンド。|  
|IDG_VS_CTXT_PROJECT_CONFIG|プロジェクト構成を設定し、ビルドの順序コマンド。|  
|IDG_VS_CTXT_PROJECT_ADD|プロジェクトに項目を追加するコマンド。|  
|IDG_VS_CTXT_PROJECT_START|F5 キーに関連付けられているスタートアップ プロジェクトを設定するコマンド。|  
|IDG_VS_CTXT_PROJECT_SAVE|プロジェクト項目を保存するためのコマンド。|  
|IDG_VS_CTXT_PROJECT_DEBUG|デバッグ用のコマンド。|  
|IDG_VS_CTXT_PROJECT_SCC|ソース管理用コマンド。|  
|IDG_VS_CTXT_PROJECT_TRANSFER|切り取り、用のコマンドは、コピーおよび貼り付け操作。|  
|IDG_VS_CTXT_PROJECT_PROPERTIES|コマンドへのアクセスを提供する、**プロジェクト プロパティ** ダイアログ ボックス。|  
  
## <a name="see-also"></a>関連項目  
 [Vspackage がユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [MenuCommand と OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [再利用可能なボタンのグループの作成](../../extensibility/creating-reusable-groups-of-buttons.md)