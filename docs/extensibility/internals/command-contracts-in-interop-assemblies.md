---
title: "相互運用機能アセンブリでのコマンドのコントラクト | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンド処理コマンドのコントラクトの相互運用機能アセンブリ"
  - "相互運用機能アセンブリは、コマンドをコントラクトします。"
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 相互運用機能アセンブリでのコマンドのコントラクト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使ってコマンドを処理するための基本的なコントラクト、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスは、環境を呼び出す、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドはサポートされている場合と、コマンドがサポートされているかどうかを判断する、その状態とテキストを判別します。 次に、環境の呼び出し、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> コマンドを実行するメソッドです。  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> メソッドはすべてのコマンドと同じ処理です。 それ以降の通信は \(たとえば、ドロップ ダウン リストの場合\) に必要な場合は、呼び出すことで管理されて、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 適切なパラメーターを持つメソッドです。 これらのパラメーターの解釈は、指定されたコマンドによって異なります。  
  
 コマンドの対象では、出力パラメーターの値が返された場合、呼び出し元は常が割り当てられているすべてのリソースを解放します。 このパラメーターは、バリアントでは、リソースを解放バリアントをオフにするとします。  
  
 コマンドが、階層ウィンドウ内で動作する必要がの場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> インターフェイスを使用する必要があります。<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> インターフェイスに類似するメソッドを持つようなコントラクト: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>です。  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage でルーティング コマンド](../../extensibility/internals/command-routing-in-vspackages.md)   
 [実装](../../extensibility/internals/command-implementation.md)