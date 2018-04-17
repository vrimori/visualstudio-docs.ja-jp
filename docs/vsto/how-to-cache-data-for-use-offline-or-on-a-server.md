---
title: '方法: オフラインであるか、サーバーで使用するデータをキャッシュ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 91b50684e18aaf4b7b6d95d24c81ecb56bdefc4c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>方法 : オフラインで使用するデータまたはサーバー上で使用するデータをキャッシュする
  オフラインをマーキングするドキュメントでキャッシュに保存するデータ項目使用できるようにします。 できるようになります、データのドキュメントがサーバーに格納されている場合、他のコードによって操作されるドキュメントにします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 使用している場合や、コードで宣言されると、データ項目をキャッシュするデータ項目をマークすることができます、<xref:System.Data.DataSet>のプロパティを設定して、**プロパティ**ウィンドウです。 はないデータ項目をキャッシュするかどうか、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>ドキュメント内にキャッシュされているための条件を満たしていることを確認してください。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。  
  
> [!NOTE]  
>  としてマークされている Visual Basic を使用して作成されたデータセット**Cached**と**WithEvents** (からドラッグされたデータセットを含む、**データソース**ウィンドウまたは**ツールボックス**がある、 **CacheInDocument**プロパティに設定**True**)、キャッシュ内でその名前の先頭にアンダー スコアがあります。 たとえば、データセットを作成し、名前を付けます**顧客**、<xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>名前になります**_Customers**キャッシュにします。 使用すると<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>このキャッシュされたアイテムにアクセスする必要がありますを指定する**_Customers**の代わりに**顧客**です。  
  
### <a name="to-cache-data-in-the-document-using-code"></a>コードを使用して、ドキュメント内のデータをキャッシュする  
  
1.  などのプロジェクトでホスト項目クラスのメンバーとして、パブリック フィールドまたはデータ項目のプロパティを宣言、 `ThisDocumen`Word プロジェクトで t クラスまたは`ThisWorkbook`Excel プロジェクト内のクラスです。  
  
2.  適用、<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>属性をドキュメントのデータ キャッシュに格納されるデータ項目をマークするメンバーにします。 次の例では、この属性を適用のフィールドの宣言に、<xref:System.Data.DataSet>です。  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]  
  
3.  データ項目のインスタンスを作成するコードを追加し、該当する場合、データベースから読み込めません。  
  
     最初に作成されるときにのみ、データ項目が読み込まれるその後、キャッシュの内容をし、更新するには、その他のコードを記述する必要があります。  
  
### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>[プロパティ] ウィンドウを使用して、ドキュメント内のデータセットをキャッシュするには  
  
1.  使用して、プロジェクト データ ソースを追加することによって、Visual Studio デザイナーで、たとえば、ツールを使用して、プロジェクトにデータセットを追加、**データソース**ウィンドウです。  
  
2.  されていない、いずれかであるし、デザイナーで、インスタンスを選択しない場合は、データセットのインスタンスを作成します。  
  
3.  **プロパティ**ウィンドウで、設定、 **CacheInDocument**プロパティを**True**です。  
  
     詳細については、次を参照してください。 [Office プロジェクトのプロパティ](../vsto/properties-in-office-projects.md)です。  
  
4.  **プロパティ**ウィンドウで、設定、**修飾子**プロパティを**パブリック**(既定では、**内部**)。  
  
## <a name="see-also"></a>関連項目  
 [データのキャッシュ](../vsto/caching-data.md)   
 [方法: Office ドキュメント内のデータ ソースをプログラムでキャッシュ](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [方法: パスワードで保護されたドキュメント内のデータをキャッシュします。](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [サーバー上のドキュメント内のデータにアクセスします。](../vsto/accessing-data-in-documents-on-the-server.md)   
 [データの保存](/visualstudio/data-tools/saving-data)  
  
  