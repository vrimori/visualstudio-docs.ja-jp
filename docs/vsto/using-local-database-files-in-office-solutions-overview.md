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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1576af3c3fc8a1c7f514a4941eb849df03774c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
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
  
## <a name="see-also"></a>参照  
 [Office ソリューションでのコントロールへのデータをバインディング](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [キャッシュされたデータ](../vsto/caching-data.md)  
  
  