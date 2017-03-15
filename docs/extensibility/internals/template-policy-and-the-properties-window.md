---
title: "テンプレートのポリシーおよび [プロパティ] ウィンドウ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テンプレートのポリシーの [プロパティ] ウィンドウ"
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# テンプレートのポリシーおよび [プロパティ] ウィンドウ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

エンタープライズ プロジェクトとテンプレート プロジェクト内に含まれている場合はそのテンプレート プロジェクトにはエンタープライズ ポリシーを適用できます。  テンプレート ポリシーはプロパティの既定値を設定するために非表示にするプロパティを追加するプロパティを使用できるようにシステムになります。  
  
 テンプレート ポリシーを使用して ENT3ENT \[出力\] ウィンドウに情報の表示を制御するには <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> の実行とは異なります。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> はコンポーネント レベルのソリューションまたはプロジェクト レベルのオブジェクトのプロパティを抑制するためにテンプレートのポリシーを使用できますがオブジェクトのプロパティを処理します。  つまり  
  
-   表示される内容を特定のオブジェクトの ENT0ENT \[入力\] ウィンドウで確認するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> メソッドを実装します。  
  
-   前に表示しますが指定されたオブジェクトの ENT0ENT \[入力\] ウィンドウで確認するにはソリューションおよびプロジェクト レベルでテンプレート ポリシーを使用します。  
  
 テンプレート ポリシーを使用して指定した種類のプロジェクト項目が  **ソリューション エクスプローラー**  で選択したときに選択して \[ENT0ENT\] ウィンドウでの特定のプロパティを抑制してもプロジェクトで作業している開発チーム メンバーに便利な場合があります。  たとえばテンプレート ポリシーを使用する場合開発者のデータベースで接続文字列情報を設定し接続文字列を読み取り専用にすることもできます。  このように各開発者がデータ アクセス用の正しいパスを使用できるようにするための簡単な方法を提供できます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [プロパティを拡張します。](../../extensibility/internals/extending-properties.md)