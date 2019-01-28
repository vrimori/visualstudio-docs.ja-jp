---
title: VisibilityItem 要素 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e0bfdf54ccd3975864b965182d86923c6c335eb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980922"
---
# <a name="visibilityitem-element"></a>VisibilityItem 要素
`VisibilityItem`コマンドとツールバーの静的な可視性を決定します。 すべてのエントリは、コマンドまたは メニューとも関連付けられているコマンドの UI コンテキストを識別します。 Visual Studio は、それらを定義する Vspackage を読み込むことがなく、コマンド、メニューとツールバー、およびその可視性を検出します。 IDE を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>コマンド UI コンテキストがアクティブかどうかを確認するメソッド。  
  
 Visual Studio、VSPackage によって決定するコマンドの可視性が必要ですが、VSPackage が読み込まれた後ではなく、`VisibilityItem`します。 コマンドの可視性を判断する、いずれかを実装できます、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>イベント ハンドラーまたは<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>メソッドをコマンドを実装する方法。  
  
 コマンドまたはメニューを持つ、`VisibilityItem`要素は、関連付けられているコンテキストがアクティブな場合にのみ表示されます。 コマンド コンテキストの組み合わせごとにエントリを含めることによって、UI コンテキストが 1 つまたは複数のコマンドを 1 つのコマンド、メニューのまたはツールバーを関連付けることができます。 コマンドまたはメニューに関連付けられたコマンド UI の複数のコンテキストは、関連付けられたコマンド UI コンテキストのいずれかがアクティブなときに、コマンドまたはメニューが表示にします。  
  
 `VisibilityItem`要素は、コマンド、メニュー、ツールバー、グループにのみ適用されます。 関連付けられていない要素`VisibilityItem`要素は、親メニューがアクティブなときに表示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|guid|必須。 コマンド id を GUID と ID の GUID です。|  
|ID|必須。 コマンド id を GUID と ID の ID。|  
|コンテキスト|必須。 コマンドが表示されている UI コンテキスト。|  
|条件|任意。 参照してください[条件付き属性](../extensibility/vsct-xml-schema-conditional-attributes.md)します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`コマンドとツールバーのグループの静的な可視性を決定します。|  
  
## <a name="remarks"></a>Remarks  
 標準の Visual Studio の UI コンテキストが定義されている、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc\vsshlids.h ファイルと同様、<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>と<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>クラス。 UI コンテキストのより完全なセットが定義されている、<xref:Microsoft.VisualStudio.VSConstants>クラス。  
  
## <a name="example"></a>例  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
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
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)