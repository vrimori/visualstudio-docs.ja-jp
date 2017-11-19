---
title: "VisibilityItem 要素 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db041f839e9b7e8ad3268175829ecfee9380e736
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="visibilityitem-element"></a>VisibilityItem 要素
`VisibilityItem`要素は、コマンドやツールバーの静的な可視性を決定します。 すべてのエントリは、コマンドまたはメニューとも関連付けられているコマンド UI コンテキストを識別します。 Visual Studio は、それらを定義する Vspackage を読み込むことがなくコマンド、メニューのおよびツールバー、およびその可視性を検出します。 IDE を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>コマンド UI コンテキストがアクティブかどうかを確認するメソッド。  
  
 Visual Studio、VSPackage によって決定するコマンドの可視性が必要ですが、VSPackage が読み込まれた後ではなく、`VisibilityItem`です。 コマンドの可視性を確認することができますを実装するいずれか、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>イベント ハンドラーまたは<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドをコマンドを実装する方法によって異なります。  
  
 コマンドまたはを含むメニューの`VisibilityItem`要素は、関連付けられているコンテキストがアクティブな場合にのみ表示されます。 コマンド コンテキストの組み合わせごとにエントリを含めることによって、1 つまたは複数のコマンド UI コンテキストがある 1 つのコマンド、メニューのまたはツールバーを関連付けることができます。 コマンドまたはメニューは、複数のコマンド UI コンテキストに関連付けられて、関連付けられているコマンド UI コンテキストのいずれかがアクティブなときに、コマンドまたはメニューが表示にします。  
  
 `VisibilityItem`要素は、コマンド、メニューのおよびグループにないのツールバーにのみ適用されます。 関連がない要素`VisibilityItem`要素は、親メニューがアクティブなときに表示します。  
  
## <a name="syntax"></a>構文  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須です。 GUID と ID コマンド id の GUID です。|  
|ID|必須です。 GUID と ID のコマンド識別子の ID。|  
|コンテキスト|必須です。 コマンドが表示されている UI コンテキスト。|  
|状態|省略可能です。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`要素は、コマンドやツールバーのグループの静的な可視性を決定します。|  
  
## <a name="remarks"></a>コメント  
 標準の Visual Studio の UI コンテキストが定義されている、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc\vsshlids.h ファイルとしてように、<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>と<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>クラスです。 UI コンテキストの完全なセットが定義されている、<xref:Microsoft.VisualStudio.VSConstants>クラスです。  
  
## <a name="example"></a>例  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)