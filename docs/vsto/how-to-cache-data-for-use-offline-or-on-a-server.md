---
title: "方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "データ [Visual Studio での Office 開発], キャッシュ"
  - "データ キャッシュ [Visual Studio での Office 開発], オフライン使用"
  - "データ キャッシュ [Visual Studio での Office 開発], サーバー使用"
  - "データセット [Visual Studio での Office 開発], キャッシュ"
  - "Office アプリケーション [Visual Studio での Office 開発], データ"
  - "オフライン データ [Visual Studio での Office 開発]"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# 方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする
  ドキュメント内でキャッシュするデータ項目を指定して、オフラインで使用できます。  ドキュメントがサーバーに保存されているときに、他のコードからドキュメント内のデータを使用することもできます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 キャッシュするデータ項目は、データ項目をコードで宣言するときに指定するか、<xref:System.Data.DataSet> を使用する場合は、**プロパティ** ウィンドウのプロパティを設定して指定します。  <xref:System.Data.DataSet> または <xref:System.Data.DataTable> ではないデータ項目をキャッシュする場合は、ドキュメントにキャッシュするための基準を満たすことを確認します。  詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。  
  
> [!NOTE]  
>  Visual Basic で **Cached** および **WithEvents** を指定して作成したデータセット \(**\[データ ソース\]** ウィンドウまたは**ツールボックス**からドラッグされ、**CacheInDocument** プロパティが **True** に設定されたデータセットを含む\) は、アンダースコアで始まる名前でキャッシュに格納されます。  たとえば、Customers という名前のデータセットを作成した場合、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> の名前はキャッシュ内では \_Customers です。  キャッシュされた項目へのアクセスに <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> を使用する場合、Customers ではなく \_Customers を指定する必要があります。  
  
### コードを使用してドキュメント内のデータをキャッシュするには  
  
1.  データ項目のパブリック フィールドまたはプロパティを、プロジェクトのホスト項目クラス \(たとえば、Word プロジェクトの場合は `ThisDocument` クラス、Excel プロジェクトの場合は `ThisWorkbook` クラス\) のメンバーとして宣言します。  
  
2.  メンバーに <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性を適用し、データ項目がドキュメントのデータ キャッシュに格納されるように設定します。  次の例では、この属性を <xref:System.Data.DataSet> のフィールド宣言に適用しています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  データ項目のインスタンスを作成し、\(該当する場合は\) データベースからそれを読み込むためのコードを追加します。  
  
     データ項目が読み込まれるのは最初の作成時のみで、その後はキャッシュがドキュメント内に残されます。キャッシュの内容を更新するには他のコードを作成する必要があります。  
  
### プロパティ ウィンドウを使用してドキュメント内のデータセットをキャッシュするには  
  
1.  Visual Studio デザイナーのツールを使用して、データセットをプロジェクトに追加します。たとえば、**\[データ ソース\]** ウィンドウを使用して、データ ソースをプロジェクトに追加します。  
  
2.  データセットのインスタンスをまだ作成してない場合は作成し、デザイナーでそのインスタンスを選択します。  
  
3.  **\[プロパティ\]** ウィンドウで、**CacheInDocument** プロパティを **True** に設定します。  
  
     詳細については、「[Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)」を参照してください。  
  
4.  **\[プロパティ\]** ウィンドウで、**\[Modifiers\]** プロパティを **\[Public\]** \(既定では、**\[Internal\]**\) に設定します。  
  
## 参照  
 [キャッシュされたデータ](../vsto/caching-data.md)   
 [方法 : Office ドキュメント内のデータ ソースをプログラムでキャッシュする](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [方法 : パスワードで保護されたドキュメント内のデータをキャッシュする](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)   
 [データの保存](../data-tools/saving-data.md)  
  
  