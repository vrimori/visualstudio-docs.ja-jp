---
title: "プロパティ ウィンドウのオブジェクトの一覧 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "オブジェクトの一覧の [プロパティ] ウィンドウ"
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# プロパティ ウィンドウのオブジェクトの一覧
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

\[入力\] ENT0ENT ウィンドウのオブジェクト リストは一つ以上の選択したウィンドウ内で使用できるそのほかのオブジェクトに選択項目を変更するドロップダウン リストです。  オンにすると新しいオブジェクトが選択されていることを通知する環境の呼び出しを <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> この一覧から内で異なるオブジェクトをトリガーします。  \[ENT0ENT\] ウィンドウで表示される情報はに関連付けられているプロパティを表示するために選択したオブジェクトに変更されます。  
  
## オブジェクト リスト  
 オブジェクト リストは 2 個のフィールドで構成されます : オブジェクト名 \(太字で表示されます\) とオブジェクトの型。  
  
 太字のオブジェクトの種類の左側に表示されるオブジェクトの名前は <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> のインターフェイスに備わっている `Name` のプロパティを使用してオブジェクト自体から取得されます。  <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A> の <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> のメソッドはインターフェイスのコクラスの <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> を返します。  ドロップダウン リスト オブジェクト名として表示するコクラスの名前を取得 ENT0ENT \[出力\] ウィンドウの使用 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>。  
  
 オブジェクトに `Name` のプロパティがない場合名前はオブジェクト リストの名前の領域に表示されます。  オブジェクト リストに表示される名前が必要な場合はオブジェクトにプロパティを追加できます。  
  
 COM オブジェクトが <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> を実行する ENT0ENT\[出力\] ウィンドウに表示されるリストの左側のオブジェクト名の代わりにインターフェイスの名前。  
  
## 参照  
 [プロパティを拡張します。](../../extensibility/internals/extending-properties.md)