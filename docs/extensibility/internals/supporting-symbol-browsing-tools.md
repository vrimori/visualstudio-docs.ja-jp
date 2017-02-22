---
title: "シンボル参照のツールのサポート | Microsoft Docs"
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
  - "シンボルをシンボル閲覧ツール"
  - "ブラウザーでは、シンボル ブラウザー"
  - "シンボル参照のツール"
  - "ライブラリ"
  - "IVsLibrary2 インターフェイス、シンボル参照のツール"
  - "IVsSimpleLibrary2 インターフェイス、シンボル参照のツール"
  - "シンボル参照のツール、ライブラリ マネージャー"
  - "シンボル"
  - "ライブラリ、ツールのシンボル参照"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# シンボル参照のツールのサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**オブジェクト ブラウザー   クラス ビュー   呼び出しブラウザー**  と  **シンボルの検索結果**  のツールは Visual Studio の機能を利用するシンボルを提供します。  これらのツールはシンボル階層ツリー ビューを表示ツリー内のシンボルの関係を示しています。  シンボルはオブジェクト名前空間クラスクラス メンバーおよびさまざまなコンポーネントに含まれる他の言語要素を表す場合があります。  コンポーネントはVisual Studio のプロジェクト[!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] の外部コンポーネントおよび型 \(.tlb\) のライブラリが含まれています。  詳細については、「[コードの構造の表示](../../ide/viewing-the-structure-of-code.md)」を参照してください。  
  
## ライブラリ内のシンボル参照  
 言語の実装はコンポーネントのシンボルを追跡しVisual Studio のオブジェクト マネージャーに一連のインターフェイスを通じてシンボルのリストを提供するライブラリを作成して Visual Studio のシンボル参照の機能を拡張できます。  ライブラリは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> のインターフェイスによって表されます。  Visual Studio のオブジェクト マネージャーはシンボル ブラウザー ツールから新しいデータの要求にライブラリからデータを取得し整理することによって返されます。  これは要求されたデータのツールを設定または更新します。  Visual Studio のマネージャー オブジェクトへの参照を <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> は`GetService` のメソッドに移動するには<xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> サービス ID を渡します。  
  
 各ライブラリはすべてのライブラリ情報を収集する Visual Studio のオブジェクト マネージャーに登録する必要があります。  ライブラリを登録するには<xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> のメソッドを呼び出します。  どのツールによって要求を開始するとVisual Studio のオブジェクト マネージャーの検索は適切なライブラリまたはデータを要求します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> で記述されているシンボルのリスト   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクトとライブラリ マネージャー トリップ間でデータはインターフェイスします。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクト マネージャーは定期的に更新を実行してライブラリに含まれる最新のデータを反映するツール シンボルを参照します。  
  
 次の図はライブラリ マネージャーと Visual Studio のオブジェクト間の要求やデータ交換プロセスのキー要素のサンプルが含まれています。  図のインターフェイスはマネージ コード アプリケーションの一部です。  
  
 ![ライブラリとオブジェクト マネージャー間のデータ フロー](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Visual Studio にシンボルのリストを指定するにはマネージャーに <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> のメソッドを呼び出してVisual Studio のオブジェクト マネージャーを使用してライブラリを登録する必要があります。します。  ライブラリを登録した後Visual Studio のオブジェクト マネージャーはライブラリ機能に関する特定の情報を要求します。  たとえば<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> のメソッドを呼び出してライブラリ フラグとサポートされるカテゴリを要求します。  ある時点でツールの 1 つがこのライブラリからデータを要求するとそのオブジェクト マネージャーは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> のメソッドを呼び出してシンボルのトップレベルのリストを要求します。  これに対してシンボルのリストを開発しVisual Studio のオブジェクト マネージャーに <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> のインターフェイスを通じて公開します。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクト マネージャーは項目がリストに <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> のメソッドを呼び出すことによって決まります。  次のすべての要求はリスト内の指定されたアイテムに関連し各要求の項目のインデックス番号を指定します。  Visual Studio のオブジェクト   マネージャーは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> のメソッドを呼び出して項目の種類ユーザー補助およびそのほかのプロパティ情報の収集を移動します。  
  
 これは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> のメソッドを呼び出して項目の名前を確認し<xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> のメソッドを呼び出してアイコンの情報を要求します。  アイコンはアイテム名の左側に表示され項目ユーザー補助およびそのほかのプロパティの種類を示しています。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のオブジェクト マネージャーは指定したリスト項目は拡張可能で子項目があるかどうかを確認するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> のメソッドを呼び出します。  UI に要素を配置する要求を送信 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> マネージャーはオブジェクトのメソッドを呼び出してシンボルの子リストを要求します。  プロセスがオン デマンド式に基づいてツリーのさまざまな部分に従います。  
  
> [!NOTE]
>  ネイティブ コードでシンボルのプロバイダーを実装するには<xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> のインターフェイスを使用します。  
  
## 参照  
 [方法: オブジェクト マネージャにライブラリを登録](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [方法: オブジェクト マネージャーにライブラリによって提供されるシンボルのリストを公開](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [方法: シンボル ライブラリ内の特定](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)