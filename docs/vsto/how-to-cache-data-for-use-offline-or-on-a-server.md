---
title: '方法: オフラインか、サーバーで使用するデータをキャッシュします。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 319cd31ccdc2c5c8cfa2b4540e5f32382008ca5a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873745"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>方法: オフラインか、サーバーで使用するデータをキャッシュします。
  オフラインをマーキングするドキュメントでキャッシュされるデータ項目使用できるようにします。 これもにより、データのドキュメントがサーバーに格納されている場合、他のコードによって操作されるドキュメントで。

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 データ項目が、コードで宣言されている、または、使用する場合にキャッシュされるデータ項目をマークすることができます、<xref:System.Data.DataSet>のプロパティを設定して、**プロパティ**ウィンドウ。 ないデータ項目をキャッシュするかどうか、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>ドキュメント内にキャッシュされているための条件を満たしていることを確認します。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)します。

> [!NOTE]
>  としてマークされている Visual Basic を使用して作成されたデータセット**キャッシュ**と**WithEvents** (はからドラッグされたデータセットを含む、**データソース**ウィンドウまたは**ツールボックス**がある、 **CacheInDocument**プロパティに設定**True**)、キャッシュ内の名前にプレフィックスとしてアンダー スコアがあります。 たとえば、データセットを作成し、名前を付けます**顧客**、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>名前になります **_Customers**キャッシュします。 使用すると<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>このキャッシュされた項目にアクセスすることを指定する必要があります **_Customers**の代わりに**顧客**します。

### <a name="to-cache-data-in-the-document-using-code"></a>コードを使用して、ドキュメント内のデータをキャッシュする

1.  など、プロジェクトでホスト項目クラスのメンバーとして、パブリック フィールドまたはデータ項目のプロパティを宣言、 `ThisDocumen`Word プロジェクトで t クラスまたは`ThisWorkbook`Excel プロジェクト内のクラス。

2.  適用、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性をドキュメントのデータ キャッシュに格納されるデータ項目をマークするメンバーにします。 次の例では、この属性を適用のフィールド宣言に、<xref:System.Data.DataSet>します。

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3.  データ項目のインスタンスを作成するコードを追加し、該当する場合は、データベースから読み込めません。

     最初に作成されるときにのみ、データ項目が読み込まれるその後、キャッシュの内容をし、更新するには、その他のコードを記述する必要があります。

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>[プロパティ] ウィンドウを使用して、ドキュメント内のデータセットをキャッシュするには

1.  使用してプロジェクトにデータ ソースを追加することで、Visual Studio デザイナーでツールを使用して、プロジェクトにデータセットを追加、**データソース**ウィンドウ。

2.  いない状態がある、1 つ、デザイナーで、インスタンスを選択する場合は、データセットのインスタンスを作成します。

3.  **プロパティ**ウィンドウで、設定、 **CacheInDocument**プロパティを**True**します。

     詳細については、次を参照してください。 [Properties in Office Projects](../vsto/properties-in-office-projects.md)します。

4.  **プロパティ**ウィンドウで、設定、**修飾子**プロパティを**パブリック**(既定では、**内部**)。

## <a name="see-also"></a>関連項目
 [データをキャッシュ](../vsto/caching-data.md)[方法。Office ドキュメント内のデータ ソースをプログラムでキャッシュ](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)[方法。パスワードで保護されたドキュメント内のデータをキャッシュ](../vsto/how-to-cache-data-in-a-password-protected-document.md)[サーバー上のドキュメント内のデータ アクセス](../vsto/accessing-data-in-documents-on-the-server.md)[データの保存](../data-tools/saving-data.md)
