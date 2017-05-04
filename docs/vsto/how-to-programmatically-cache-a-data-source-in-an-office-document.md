---
title: "方法 : Office ドキュメント内のデータ ソースをプログラムでキャッシュする | Microsoft Docs"
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
  - "データ キャッシュ [Visual Studio での Office 開発], プログラムによる"
  - "データセット [Visual Studio での Office 開発], キャッシュ"
  - "Office アプリケーション [Visual Studio での Office 開発], データ"
  - "StartCaching メソッド"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# 方法 : Office ドキュメント内のデータ ソースをプログラムでキャッシュする
  <xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Tools.Excel.Workbook>、<xref:Microsoft.Office.Tools.Excel.Worksheet> などのホスト項目の `StartCaching` メソッドを呼び出し、プログラムによってドキュメント内のデータ キャッシュにデータ オブジェクトを追加できます。  ホスト項目の `StopCaching` メソッドを呼び出して、データ キャッシュからデータ オブジェクトを削除します。  
  
 `StartCaching` メソッドおよび `StopCaching` メソッドは両方ともプライベートですが、IntelliSense に表示されます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 `StartCaching` メソッドを使用し、データ オブジェクトをデータ キャッシュに追加すると、データ オブジェクトを <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 属性で宣言する必要がありません。  ただし、データ オブジェクトは、データ キャッシュに追加するための特定の要件を満たす必要があります。  詳細については、「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。  
  
### データ オブジェクトをプログラムでキャッシュするには  
  
1.  データオブジェクトをメソッド内部ではなくクラス レベルで宣言します。  この例では、プログラムでキャッシュする、`dataSet1` という名前の <xref:System.Data.DataSet> を宣言していることを前提とします。  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  データ オブジェクトをインスタンス化した後、ドキュメントまたはワークシートのインスタンスの `StartCaching` メソッドを呼び出し、データ オブジェクトの名前を渡します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### データ オブジェクトのキャッシュを停止するには  
  
1.  文書インスタンスまたはワークシート インスタンスの `StopCaching` メソッドを呼び出し、データ オブジェクトの名前を渡します。  この例は、キャッシュを停止しようとしている `dataSet1` という <xref:System.Data.DataSet> があることを前提としています。  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  文書またはワークシートの `Shutdown` イベントのイベント ハンドラーから `StopCaching` を呼び出さないでください。  `Shutdown` イベントが発生する時点では、データ キャッシュの変更は間に合いません。  `Shutdown` イベントの詳細については、「[Office プロジェクトのイベント](../vsto/events-in-office-projects.md)」を参照してください。  
  
## 参照  
 [キャッシュされたデータ](../vsto/caching-data.md)   
 [方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法 : パスワードで保護されたドキュメント内のデータをキャッシュする](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [サーバー上のドキュメント内のデータへのアクセス](../vsto/accessing-data-in-documents-on-the-server.md)   
 [データの保存](../data-tools/saving-data.md)  
  
  