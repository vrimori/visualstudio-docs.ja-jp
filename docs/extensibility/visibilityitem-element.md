---
title: "VisibilityItem 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VisibilityItem 要素 (VSCT XML スキーマ)"
  - "VisibilityItem、VSCT XML スキーマ要素"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# VisibilityItem 要素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`VisibilityItem` 要素は、コマンドとツールバーの静的な可視性を決定します。 すべてのエントリは、コマンドまたはメニューとも関連付けられているコマンド UI コンテキストを識別します。 Visual Studio は、それらを定義する Vspackage を読み込むことがなく、コマンド、メニューのおよびツールバー、およびその可視性を検出します。 IDE を使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> コマンド UI コンテキストがアクティブかどうかを確認するメソッドです。  
  
 Visual Studio に VSPackage が決定するコマンドの可視性が必要ですが、VSPackage が読み込まれた後ではなく、 `VisibilityItem`です。 コマンドの可視性を調べるに、いずれかを実装できます、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> イベント ハンドラーまたは <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> コマンドを実装した方法に応じての手法です。  
  
 コマンドまたはメニューを持つ、 `VisibilityItem` 要素は、関連付けられているコンテキストがアクティブな場合にのみ表示されます。 コマンド コンテキストの組み合わせごとにエントリを含めることによって、1 つまたは複数のコマンド UI のコンテキストで 1 つのコマンド、メニューのまたはツールバーを関連付けることができます。 コマンドまたはメニューは、複数のコマンド UI コンテキストに関連付けられて、関連付けられているコマンド UI コンテキストのいずれかがアクティブにし、コマンドまたはメニューは表示にされます。  
  
 `VisibilityItem` 要素は、コマンド、メニューのおよびグループにないのツールバーにのみ適用されます。 関連付けられていない要素 `VisibilityItem` 要素は、親メニューがアクティブなときに表示します。  
  
## 構文  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|guid|必須です。 GUID と ID コマンドの識別子の GUID です。|  
|ID|必須です。 GUID と ID コマンドの識別子の ID です。|  
|コンテキスト|必須です。 コマンドが表示されている UI コンテキスト。|  
|状態|省略可能です。 「[条件付きの属性](../extensibility/vsct-xml-schema-conditional-attributes.md)」を参照してください。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` 要素は、コマンドとツールバーのグループの静的な可視性を決定します。|  
  
## 解説  
 標準の Visual Studio の UI コンテキストが定義されている、 *Visual Studio SDK インストール パス*でなく、\\VisualStudioIntegration\\Common\\Inc\\vsshlids.h ファイル、 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> と <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> クラスです。 UI コンテキストのより完全なセットが定義されている、 <xref:Microsoft.VisualStudio.VSConstants> クラスです。  
  
## 使用例  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)