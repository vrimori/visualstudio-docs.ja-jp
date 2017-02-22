---
title: "クエリ (ソース コントロール VSPackage) 保存クエリの編集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "QEQS イベント"
  - "Query イベントのクエリの保存の編集"
  - "クエリの編集のクエリの保存のイベントのソース管理パッケージ"
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# クエリ (ソース コントロール VSPackage) 保存クエリの編集
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] エディターとクエリの編集のクエリを保存するイベントをブロードキャスト \(QEQS\) できます。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のソース管理のスタブはQEQS のイベントの受け取りと同様にQEQS サービスを実行します。  これらのイベントは現在アクティブなソース管理 VSPackage に転送されます。  アクティブなソース管理 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> VSPackage はメソッドとメソッドを実装します。  `IVsQueryEditQuerySave2` のインターフェイスのメソッドは文書が初めて編集する直前の文書が保存される直前に呼び出されます。  
  
## QueryEditQuerySave のイベント  
 ソース管理 `IVsQueryEditQuerySave2` VSPackage はインターフェイスおよび必要なメソッドを実装して QEQS のイベントを処理する必要があります。  VSPackage が少なくとも実行する 2 とおりの方法の簡単な説明を次に示します。  実際の実装はソース管理のモデル ロジックを実行する必要があります。  
  
### QueryEditFiles のメソッド  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> はプロジェクトまたはエディターでファイルを変更するときに呼び出されます。  理想的にはこのメソッドはファイルを保存するとファイルが変更されると  *には*  呼び出されます。  呼び出されると`IVsQueryEditQuerySave2::QueryEditFiles` のメソッドをチェックする必要があるかどうかおよび再読み込みするか指定したファイルがソース管理下にあるチェックします。  ファイルが編集できるようになっている場合があるため`IVsQueryEditQuerySave2::QueryEditFiles` のメソッドでは呼び出し元のプログラムを編集をキャンセルするように指示します。  呼び出し元は呼び出しモードを指定することもできます。  「」サイレント モードではこのメソッドはによって UI が表示されない場合にのみ処理を行います。  UI が避けられない場合の問題を示すにはフラグはを返す必要があります。  
  
 メソッドはトランザクション的な方法で実行します ; つまり編集が一つのファイルにキャンセル編集すべてのファイルに対して取り消された。  逆に編集が許可されるとすべてのファイルに対して許可されます。  このメソッドはファイルの指定した文字列に対して一度編集できるようになっているファイルのセットの後続の呼び出しで編集したことを常に割り当てる必要があります。  編集許可のループではファイルを閉じ保存および再読み込みするまで継続 ; 属性 \(プロパティ\) を変更するまで ; ソース管理またはパッケージが変更されます。  `IVsQueryEditQuerySave2::QueryEditFiles` メソッドの実装で考慮する場合はユーザーから複数のファイル特殊なファイルキャンセルメモリの編集があります。  
  
### QuerySaveFiles のメソッド  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> はプロジェクトまたはエディターで複数のファイルを格納する必要があるときに呼び出されます。  呼び出されると`IVsQueryEditQuerySave2::QuerySaveFiles` のメソッドは指定されたファイルが読み取り専用かどうかをソース管理下にあるチェックします。  ファイルがチェック アウトする必要がある場合はソース管理パッケージに転送されます。  ファイルが格納されている場合があるため`IVsQueryEditQuerySave2::QuerySaveFiles` のメソッドはエディターの保存をキャンセルするに告げなければ必要があります。  `IVsQueryEditQuerySave2::QueryEditFiles` のメソッドと同様に呼び出し元は呼び出しモードを指定することもできます。  「」サイレント モードではこのメソッドはによって UI が表示されない場合にのみ処理を行います。  UI が避けられない場合の問題を示すにはフラグはを返す必要があります。  
  
 このメソッドはトランザクション的な方法で実行する必要があります。; つまり保存が一つのファイルにキャンセルすべてのファイルに対して取り消された。  逆に保存が許可されるとすべてのファイルに対して許可する必要があります。  `IVsQueryEditQuerySave2::QueryEditFiles` のメソッドと同様に`IVsQueryEditQuerySave2::QuerySaveFiles` メソッドの実装で考慮する場合はユーザーから複数のファイル特殊なファイルキャンセルメモリの編集があります。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>