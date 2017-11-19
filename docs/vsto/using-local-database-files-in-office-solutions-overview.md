---
title: "Office ソリューションの概要にあるローカル データベース ファイルを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e90143904c8d628e4288e24602907a75ae4bc59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>Office ソリューションにおけるローカル データベース使用の概要
  Office ソリューションでは、SQL Server Express (.mdf) ファイルまたは Microsoft Office Access (.mdb) ファイルなどのデータベース ファイルを含めることができます。 これにより、一元化されたデータベースのメンテナンスができない場合は必要な 1 台のコンピューターのみで使用されているローカル インベントリ ソリューションの例にあるローカル データベースを維持するためにエンドユーザーことができます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>データベース ファイルをプロジェクトにインポートします。  
 プロジェクトにデータベース ファイルをインポートするには、使用、**データ ソース構成ウィザード**データベース ファイルに基づくデータ ソースを作成します。 ウィザードでは、データベース ファイルと型指定されたデータセットをプロジェクトに追加します。  
  
## <a name="deploying-the-database-file"></a>データベース ファイルの配置  
 **データ ソース構成ウィザード**相対パスを使用して、ローカル データベース ファイルへの接続を作成します。 これにより、ファイルの相対位置を保持している場合に、1 台のコンピューターからソリューションを別にコピーすることができます。  
  
 ソリューションをサーバーに配置し、各エンドユーザーにドキュメントを配布した場合も手動でデータベース ファイルを配布して、ドキュメントに対する相対位置が、インストールする必要があります。 つまり、そのユーザーも、データベース ファイルを移動しない限り、エンド ユーザーが自分のコンピューターで、新しい場所にドキュメントを移動できないことです。  
  
## <a name="local-database-files-and-caching-the-dataset"></a>ローカル データベース ファイルとデータセットのキャッシュ  
 Microsoft Office Excel および Microsoft Office Word のドキュメント レベルのソリューションでは、属性を持つデータセットのインスタンスをマークすることによって、ドキュメント内のデータセットをキャッシュできます<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>です。 追加すると、データベース ファイルをプロジェクトを使用して、**データ ソース構成ウィザード**、型指定されたデータセットが自動的にプロジェクトに追加します。 適用することはほとんどありません必要がある<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>、このデータセットにデータが既にローカル ユーザーのコンピューター上にあるためです。 詳細については、「 [Caching Data](../vsto/caching-data.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [キャッシュされたデータ](../vsto/caching-data.md)  
  
  