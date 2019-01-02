---
title: '方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュします。'
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
ms.openlocfilehash: 3db60729facffdfd42553f95215e154de528436f
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804446"
---
# <a name="how-to-programmatically-cache-a-data-source-in-an-office-document"></a>方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュします。
  呼び出すことによって、データ オブジェクトをドキュメント内のデータ キャッシュをプログラムで追加することができます、`StartCaching`メソッドのホスト項目など、 <xref:Microsoft.Office.Tools.Word.Document>、 <xref:Microsoft.Office.Tools.Excel.Workbook>、または<xref:Microsoft.Office.Tools.Excel.Worksheet>します。 データ キャッシュから呼び出すことによって、データ オブジェクトを削除、`StopCaching`ホスト項目のメソッド。

 `StartCaching`メソッドと`StopCaching`メソッドは、プライベートの両方が IntelliSense に表示されます。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 使用すると、`StartCaching`で宣言するのには、データ キャッシュ、データ オブジェクトにデータ オブジェクトを追加するメソッドは必要はありません、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性。 ただし、データ オブジェクトには、データ キャッシュに追加する特定の要件を満たす必要があります。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。

## <a name="to-programmatically-cache-a-data-object"></a>データ オブジェクトをプログラムでキャッシュするには

1.  メソッド内ではなく、クラス レベルでデータ オブジェクトを宣言します。 この例では、宣言すること、<xref:System.Data.DataSet>という`dataSet1`プログラムでキャッシュします。

     [!code-csharp[Trin_VstcoreDataExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#12)]

2.  データ オブジェクトをインスタンス化を呼び出して、`StartCaching`データ オブジェクト名を渡し、文書またはワークシートのインスタンスのメソッド。

     [!code-csharp[Trin_VstcoreDataExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#13)]

## <a name="to-stop-caching-a-data-object"></a>データ オブジェクトのキャッシュを停止するには

1.  呼び出す、`StopCaching`データ オブジェクト名を渡し、文書またはワークシートのインスタンスのメソッド。 この例では、ある、<xref:System.Data.DataSet>という`dataSet1`のキャッシュを停止します。

     [!code-csharp[Trin_VstcoreDataExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#14)]

    > [!NOTE]
    >  呼び出さない`StopCaching`のイベント ハンドラーから、`Shutdown`文書またはワークシートのイベント。 時間によって、`Shutdown`イベントは、データ キャッシュを変更するには遅すぎます。 詳細については、`Shutdown`イベントを参照してください[Events in Office Projects](../vsto/events-in-office-projects.md)します。

## <a name="see-also"></a>関連項目

- [キャッシュ データ](../vsto/caching-data.md)
- [方法: オフラインか、サーバーで使用するデータをキャッシュします。](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [方法: パスワードで保護されたドキュメント内のキャッシュ データ](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [サーバー上のドキュメントのデータにアクセス](../vsto/accessing-data-in-documents-on-the-server.md)
- [データを保存します。](../data-tools/saving-data.md)
