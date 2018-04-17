---
title: '方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- StartCaching method
- data caching [Office development in Visual Studio], programmatically
- data [Office development in Visual Studio], caching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 29451bab5caeeaf3f9de0b9344ae52430ec045a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>方法 : Office ドキュメント内のデータ ソースをプログラムでキャッシュする
  呼び出すことによって、データ オブジェクトをドキュメント内のデータ キャッシュをプログラムで追加することができます、`StartCaching`メソッドのホスト項目など、 <xref:Microsoft.Office.Tools.Word.Document>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、または<xref:Microsoft.Office.Tools.Excel.Worksheet>です。 データ キャッシュから呼び出すことによってデータ オブジェクトを削除、`StopCaching`ホスト項目のメソッドです。  
  
 `StartCaching`メソッドおよび`StopCaching`メソッドは、プライベートの両方が IntelliSense に表示されます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 使用すると、`StartCaching`で宣言するのには、データ キャッシュ、データ オブジェクトにデータ オブジェクトを追加するメソッドは必要はありません、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性。 ただし、データ オブジェクトは、データ キャッシュに追加する特定の要件を満たす必要があります。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。  
  
### <a name="to-programmatically-cache-a-data-object"></a>プログラムでデータ オブジェクトをキャッシュするには  
  
1.  メソッド内ではなく、クラス レベルでデータ オブジェクトを宣言します。 この例では、宣言すること、<xref:System.Data.DataSet>という`dataSet1`プログラムでキャッシュします。  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]  
  
2.  データ オブジェクトをインスタンス化し、呼び出す、`StartCaching`文書またはワークシートのインスタンス名を渡しますデータ オブジェクトのメソッドです。  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]  
  
### <a name="to-stop-caching-a-data-object"></a>データ オブジェクトのキャッシュを停止するには  
  
1.  呼び出す、`StopCaching`文書またはワークシートのインスタンス名を渡しますデータ オブジェクトのメソッドです。 この例があるか、<xref:System.Data.DataSet>という`dataSet1`キャッシュを停止します。  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  呼び出す必要はありません`StopCaching`のイベント ハンドラーから、`Shutdown`文書またはワークシートのイベントです。 時間によって、`Shutdown`イベントは、データ キャッシュを変更するには遅すぎます。 詳細については、`Shutdown`イベントを参照してください[Office プロジェクトのイベント](../vsto/events-in-office-projects.md)です。  
  
## <a name="see-also"></a>関連項目  
 [データのキャッシュ](../vsto/caching-data.md)   
 [方法: オフラインであるか、サーバーで使用するデータをキャッシュ](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [方法: パスワードで保護されたドキュメント内のデータをキャッシュします。](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [サーバー上のドキュメント内のデータにアクセスします。](../vsto/accessing-data-in-documents-on-the-server.md)   
 [データの保存](/visualstudio/data-tools/saving-data)  
  
  